# Rust Template

My template for Rust projects.

## 🪄 Features

### 📦 Automatic Releases

When a tag starting with `v` is pushed to the repository, the `tagged-release` workflow will be triggered, which will:

- Create a release on GitHub
- Run `cargo test` to ensure the code is working
- Build the project binary in release mode, for Linux, macOS, and Windows
- Upload the binaries to the release
- Publish the crate to crates.io

### 🤖 Justfile

> [!NOTE]
> This section assumes that you're developing on Linux, and have [`just`](https://github.com/casey/just) installed.

Provides a few handy commands, including:

- `just b`/`just build`: Build the release binary
- `just r`/`just run`: Compile and run the project
- `just t`/`just test`: Run tests
- `just v`/`just version`: Set or get version

The `just v` command, without additional arguments, will print the current version of the project. If a version is provided, e.g. `just v 0.1.1`, it will set the version to `0.1.1`. To be specific, it will:

1. Update `version` in `Cargo.toml`
2. Update `Cargo.lock` (`cargo update`)
3. Add and commit changes (signed), with message `Bump version to v0.1.1`
4. Tag the commit with `v0.1.1` (signed)

You can then push the commit and tag to the remote repository, which will trigger the `tagged-release` workflow.

### 📖 Template Documentation & Code

- `README.md`: The README file, including:
    - Badges for license, workflow status, release, downloads, crates.io version and downloads, and docs.rs
    - Project name and description
    - Installation instructions
    - Examples, usage and credits (you can fill these in later, or remove them)
- `LICENSE`: The MIT License, with your username filled in
- `Cargo.toml`: The Cargo manifest file, with relevant fields filled in
    - Supporting `cargo-binstall` out of the box
    - Various optimizations for release builds
- `src/lib.rs`, `src/main.rs` and `tests/integration_test.rs`: The main library, binary and integration test, with an example `add` function

## 🤔 Usage

1. [Setup `cargo-generate`](https://github.com/cargo-generate/cargo-generate/#installation) on your machine.
2. Run the following command to create a new project from this template:

    ```bash
    cargo generate PRO-2684/rust-template
    ```

3. Follow the prompts to set up your project. You'll be asked for:

   - Project name
   - Project description

    Your [username](https://cargo-generate.github.io/cargo-generate/templates/builtin_placeholders.html?highlight=username) will be automatically determined by `cargo-generate`.

4. After the project is generated, consider filling out `keywords` and `categories` in `Cargo.toml`, and updating the README.
5. In order for [automatic releases](#-automatic-releases) to work, you need to:
    
    1. Create a new GitHub repository with the **same name** as your project
    2. Push the generated project to the new repository
    3. Enable GitHub Actions for the repository, and grant "Read and write permissions" to the workflow (Required for publishing GitHub releases)
    4. Provide `CARGO_TOKEN` repository secret, with enough permissions to publish your crate to crates.io

## ✅ TODO

- [ ] Showcase an example project generated using this template
    - [ ] Auto sync with this template using GitHub Actions
- [ ] Allow for specifying crate type
    - [ ] `bin`: Only `main.rs` will be generated (default, when `--bin` flag is used)
    - [ ] `lib`: Only `lib.rs` will be generated (when `--lib` flag is used)
    - [ ] `mixed`: Both `main.rs` and `lib.rs` will be generated (current, how to specify this?)
    - Workspace not planned yet
- [ ] Allow for multiple binaries and their `name` fields
- [ ] Allow for specifying whether to sign commits and tags
- [ ] Generate `cli` feature, if the crate type is `mixed`
