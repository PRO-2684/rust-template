# {{project-name}}

[![GitHub License](https://img.shields.io/github/license/{{username}}/{{project-name}}?logo=opensourceinitiative)](https://github.com/{{username}}/{{project-name}}/blob/main/LICENSE)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/{{username}}/{{project-name}}/release.yml?logo=githubactions)](https://github.com/{{username}}/{{project-name}}/blob/main/.github/workflows/release.yml)
[![GitHub Release](https://img.shields.io/github/v/release/{{username}}/{{project-name}}?logo=githubactions)](https://github.com/{{username}}/{{project-name}}/releases)
[![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/{{username}}/{{project-name}}/total?logo=github)](https://github.com/{{username}}/{{project-name}}/releases)
[![Crates.io Version](https://img.shields.io/crates/v/{{project-name}}?logo=rust)](https://crates.io/crates/{{project-name}})
[![Crates.io Total Downloads](https://img.shields.io/crates/d/{{project-name}}?logo=rust)](https://crates.io/crates/{{project-name}})
[![docs.rs](https://img.shields.io/docsrs/{{project-name}}?logo=rust)](https://docs.rs/{{project-name}})

{{project-description}}

## ⚙️ Automatic Releases Setup

1. [Create a new GitHub repository](https://github.com/new) with the name `{{project-name}}` and push this generated project to it.
2. Enable Actions for the repository, and grant "Read and write permissions" to the workflow [here](https://github.com/{{username}}/{{project-name}}/settings/actions).
3. [Generate an API token on crates.io](https://crates.io/settings/tokens/new), with the following setup:

    - `Name`: `{{project-name}}`
    - `Expiration`: `No expiration`
    - `Scopes`: `publish-new`, `publish-update`
    - `Crates`: `{{project-name}}`

4. [Add a repository secret](https://github.com/{{username}}/{{project-name}}/settings/secrets/actions/new) named `CARGO_TOKEN` with the generated token as its value.
5. Consider removing this section and updating this README with your own project information.

[Trusted Publishing](https://crates.io/docs/trusted-publishing) is a recent feature added to crates.io. To utilize it, first make sure you've already successfully published the crate to crates.io. Then, follow these steps:

1. [Add a new trusted publisher](https://crates.io/crates/{{project-name}}/settings/new-trusted-publisher) to your crate.
    - Set "Workflow filename" to `release.yml`.
    - Keep other fields intact.
    - Click "Add".
2. Modify [`release.yml`](.github/workflows/release.yml).
    1. Comment out or remove the `publish-release` job.
    2. Un-comment the `trusted-publishing` job.
3. Remove the `CARGO_TOKEN` [repository secret](https://github.com/{{username}}/{{project-name}}/settings/secrets/actions).
4. Revoke the API token on [crates.io](https://crates.io/settings/tokens).

## 📥 Installation

### Using [`binstall`](https://github.com/cargo-bins/cargo-binstall)

```shell
cargo binstall {{project-name}}
```

### Downloading from Releases

Navigate to the [Releases page](https://github.com/{{username}}/{{project-name}}/releases) and download respective binary for your platform. Make sure to give it execute permissions.

### Compiling from Source

```shell
cargo install {{project-name}}
```

## 💡 Examples

TODO

## 📖 Usage

TODO

## 🎉 Credits

TODO
