# Contributing to the Community Site

Contributing to this site is easy!
Just submit a pull request to the respective repository.
On the rop right corner you can also see the _Edit_ icons
that will normally get you right to the content page.

We do not have so many newcomer friendly issues in this repository,
but you are welcome to submit any small and big patches!

## Technology under the hood

The community site is built with [MkDocs](https://www.mkdocs.org/),
[MkDocs Multirepo Plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin/tree/main),
and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material).
So, it uses the Python technology stack instead of Gradle,
but on the other hand we're leveraging one of the most powerful documentation engines.

## Preparing the environment

It is possible to deploy the site instance locally or inside a Dev Container.

### Dev Container

This repository includes the Dev Container definition that you can use in Visual Studio Code or in IntelliJ Platform
to spin up the local development environment.

### Running locally

Requirements:

- Python3 and PiP (Python's package manager), recent versions
- Linux, MacOS or Windows WSL-2 environment.
  Windows native may work but it is not tested.

For now, you need to install the dependencies:

```shell
pip install -r .devcontainer/requirements.txt
mkdocs build
```

## Local development

Once you have the ready to build environment,
you can use `mkdocs build` to build the static site.

To do live development, use the following command to provision the site on `http://localhost:8000/community`:

```shell
mkdocs serve
```

Note that the Mkdocs Multi-Repo plugin is quite slow,
and it may take up to 10 seconds to rebuild the website on configuration changes.
If you develop the local part within this repository (design, content, etc.),
you can run the `build` and the `serve` commands with the `FULL_BUILD=false` variable, e.g.:

```shell
FULL_BUILD=false mkdocs serve
```

## CI/CD

This site is built and deployed by GitHub Actions.
We have continuous delivery, so your patches will be delivered just a few minutes
after the change is merged.
