# Contributing to the Gradle Community Site

[![a](https://img.shields.io/badge/slack-%23docs-brightgreen?style=flat&logo=slack)](./contributing/community-slack.md)

Contributing to this site is easy!
While we may not have many issues for newcomers,
we welcome all contributions, big or small. 

Many minor changes can be made directly from your browser.
Just submit a pull request to the respective repository.
On the rop right corner you can also see the _Edit_ icons
that will normally get you right to the content page.

For bigger changes, you can develop locally. 
Detailed instructions are provided below.

## Communication channels

- `#docs` on the [Gradle Community Slack](./contributing/community-slack.md)

## Contributing Content

### Contributing to Gradle Cookbook

See the [Gradle Cookbook Contributor Guide](./cookbook/CONTRIBUTING.md).

### Other locations

The Gradle website is in the early stages of development,
and we do not have fixed processes and practices yet.
Just submit a pull request with your change.
If you have any concerns, let's discuss them on Slack or in a GitHub issue.

## Developing the site

It is possible to deploy the site instance locally or inside a Dev Container.
The latter is the recommended approach.

### Technology under the hood

The community site is built with [MkDocs](https://www.mkdocs.org/),
[MkDocs Multirepo Plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin/tree/main),
and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material).
So, it uses the Python technology stack instead of Gradle,
but on the other hand we're leveraging one of the most powerful documentation engines.

### Setting up the environment

#### Dev Containers

This repository includes the Dev Container definition that you can use in Visual Studio Code or in IntelliJ Platform
to spin up the local development environment.
The same Dev Container is used for CI/CD, and it is the recommended way for local development.

#### Running locally

Requirements:

- Python3 and PiP (Python's package manager), recent versions
- Linux, macOS or Windows WSL-2 environment.
  Windows native may work but it is not tested.

For now, you need to install the dependencies:

```shell
pip install -r .devcontainer/requirements.txt
mkdocs build
```

### Local development

Once you have the ready to build environment,
you can use `mkdocs build` to build the static site.

To do live development, use the following command to provision the site on `http://localhost:8000/community`:

```shell
mkdocs serve
```

Note that the MkDocs Multi-Repo plugin is quite slow,
and it may take up to 10 seconds to rebuild the website on configuration changes.
If you develop the local part within this repository (design, content, etc.),
you can run the `build` and the `serve` commands with the `FULL_BUILD=false` variable, e.g.:

```shell
FULL_BUILD=false mkdocs serve
```

### Building the Cookbook PDF

Run `BUILD_PDF=1 mkdocs build` to generate the PDF file in [_site/pdf/cookbook.pdf](./../_site/pdf/cookbook.pdf).

## CI/CD

This site is built and deployed by GitHub Actions.
We have continuous delivery, so your patches will be delivered just a few minutes
after the change is merged.
