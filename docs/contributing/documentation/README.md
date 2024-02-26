# Contributing to Documentation

Documentation is essential part of developer experience for Gradle Build Tool users.
All contributions are welcome!

## Get Started

- Join the community Slack workspace
- Use the `#docs` channel to discuss any documentation matters
- If your pull request gets stuck, do not hesitate to ask in `#docs` or in `#contributing` channels

## Locations

- [Contributing to the Gradle Build Tool documentation](../../gradle/CONTRIBUTING/#contributing-to-documentation) -
  - This repository includes Gradle documentation sources, including but not limited to: User Manual, DSL Reference, documentation for core plugins and Javadoc
  - Implementation: Asciidoc + custom documentation engine
- Plugin documentation - Documentation for the key plugins is provided by the Gradle Build Tool repo.
  For other plugins, see their repositories for the docs and contributing guidelines.
  - Implementation: most plugins use simple documentation pages in GitHub-flavored Markdown (`README.md`).
- [Contributing to the Community site](../../CONTRIBUTING.md) -
  Community resources on this website
  - Implementation - Markdown + MkDocs

## Tools

In Gradle we use a diverse set of tooling for documentation development.
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
