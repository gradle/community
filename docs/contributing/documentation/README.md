---
title: "Contributing to Gradle Documentation"
description: >
    Documentation is essential part of developer experience for Gradle Build Tool users.
    All contributions are welcome!
---

Documentation is essential part of developer experience for Gradle Build Tool users.
All contributions are welcome!

## Get Started

- Join the community Slack workspace
- Use the `#docs` channel to discuss any documentation matters
- If your pull request gets stuck, do not hesitate to ask in the `#docs` or `#contributing` channels

## Locations

- [Gradle Build Tool - User Manual on docs.gradle.org/](https://docs.gradle.org/)
    - This site includes main Gradle documentation sources, including but not limited to: User Manual, DSL Reference, documentation for core plugins and Javadoc
    - Implementation: Asciidoc + custom documentation engine
    - [Contributor Guide](../../gradle/CONTRIBUTING/#contributing-to-documentation)
- [Gradle Cookbook](../../cookbook/README.md) - a collection of recipes, guides and examples for the Gradle Build Tool.
    - This is an additional solution-based documentation
    - Implementation: MkDocs + Material for MkDocs
    - [Contributor Guide](../../cookbook/CONTRIBUTING.md)
- Plugin documentation - Documentation for the key plugins is provided by the Gradle Build Tool repo.
  For other plugins, see their repositories for the docs and contributing guidelines.
    - Implementation: most plugins use simple documentation pages in GitHub-flavored Markdown (`README.md`).
- [Gradle Community Site](https://community.gradle.org/) -
  Community resources, including [Gradle Cookbook](../../cookbook/README.md) and top-level [Gradle Contributor Guide](../README.md)
    - Implementation - Markdown + MkDocs
    - [Contributor Guide](../../CONTRIBUTING.md)

## Tools

In Gradle we use a diverse set of tooling for documentation development.
We use both Markdown and Asciidoc for writing,
with MkDocs, Jekyll, and the Gradle Asciidoc Plugin as our main tools for documentation.
Additionally, we utilize other tools such as Dokka, Javadoc, and OpenAPI specifications.

Many small patches can be just submitted from the GitHub web editor.
For bigger patches and local development, see the referenced contributing guidelines.

## Private source locations

Please note that some of `gradle.org` locations are private source at the moment.
It includes:

- The main site (gradle.org)
- The official blog (blog.gradle.org)
- The newsletter archive (newsletter.gradle.org)
- Gradle guides and most of training courses (gradle.org/guides/)

If you want to submit patches to any of those locations,
please reach out to us on the `#docs` channel.
