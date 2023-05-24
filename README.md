# Internet Base IDE devcontainer for the Internet Computer

Template to start developing web3 apps on the
<https://internetcomputer.org>

maintained by
<https://internetbase.org>

## Dev Container Templates: Self Authoring Guide

> This repo provides a starting point and example for creating your own custom [Dev Container Templates](https://containers.dev/implementors/templates), hosted for free on GitHub Container Registry. The example in this repository follows the [Dev Container Template distribution specification](https://containers.dev/implementors/templates-distribution/).
>
> To provide feedback on the distribution spec, please leave a comment [on spec issue #71](https://github.com/devcontainers/spec/issues/71).

## Repo and Template Structure

This repository contains a _collection_ of two Templates - `hello` and `color`. These Templates serve as simple template implementations which helps containerize the project. Similar to the [`devcontainers/templates`](https://github.com/devcontainers/templates) repo, this repository has a `src` folder. Each Template has its own sub-folder, containing at least a `devcontainer-template.json` and `.devcontainer/devcontainer.json`.

```
├── src
│   ├── ic
│   │   ├── devcontainer-template.json
│   │   └──| .devcontainer
│   │      ├── devcontainer.json
│   │      └── Dockerfile

```

### Versioning

Templates are individually versioned by the `version` attribute in a Template's `devcontainer-template.json`. Templates are versioned according to the semver specification. More details can be found in [the Dev Container Template specification](https://containers.dev/implementors/templates-distribution/#versioning).

### Publishing

> NOTE: The Distribution spec can be [found here](https://containers.dev/implementors/templates-distribution/).
>
> While any registry [implementing the OCI Distribution spec](https://github.com/opencontainers/distribution-spec) can be used, this template will leverage GHCR (GitHub Container Registry) as the backing registry.

Templates are source files packaged together that encode configuration for a complete development environment.

This repo contains a GitHub Action [workflow](.github/workflows/release.yaml) that will publish each template to GHCR. By default, each Template will be prefixed with the `<owner/<repo>` namespace. For example, the two Templates in this repository can be referenced by an [implementing tool](https://containers.dev/supporting#tools) with:

```
ghcr.io/vvv-interactive/ibdev/ic:latest
```

The provided GitHub Action will also publish a third "metadata" package with just the namespace, eg: `ghcr.io/devcontainers/template-starter`. This contains information useful for tools aiding in Template discovery.

'`devcontainers/template-starter`' is known as the template collection namespace.

### Adding Templates to the Index

Next you will need to add your Templates collection to our [public index](https://containers.dev/templates) so that other community members can find them. Just follow these steps once per collection you create:

- Go to [github.com/devcontainers/devcontainers.github.io](github.com/devcontainers/devcontainers.github.io)
  - This is the GitHub repo backing the [containers.dev](https://containers.dev/) spec site
- Open a PR to modify the [collection-index.yml](https://github.com/devcontainers/devcontainers.github.io/blob/gh-pages/_data/collection-index.yml) file

This index is from where [supporting tools](https://containers.dev/supporting) like [VS Code Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) and [GitHub Codespaces](https://github.com/templates/codespaces) surface Templates for their Dev Container Creation Configuration UI.

### Updating Documentation

This repo contains a GitHub Action [workflow](.github/workflows/release.yaml) that will automatically generate documentation (ie. `README.md`) for each Template. This file will be auto-generated from the `devcontainer-template.json` and `NOTES.md`.
