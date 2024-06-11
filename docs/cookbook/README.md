# The Gradle Cookbook

Gradle Cookbook is an open-source collection of recipes, guides and examples for the Gradle Build Tool.
The goal of this portal is to offer solution-based documentation for end users,
including but not limited to key use cases like
publishing to Maven Central,
CI/CD tool and IDE integrations,
support for languages and frameworks,
troubleshooting Gradle Build Tool,
etc.

In this document, _Gradle Build Tool_ is abbreviated _Gradle_.

!!! note
    The Gradle Cookbook is under active development.
    Its structure and links may change, and we're working on adding more content.
    Any contributions are welcome, see the [Contributor Guide](./CONTRIBUTING.md)!

## Why and How?

The Gradle Build Tool ecosystem is huge, it includes many plugins, integrations, developer tools and other components.
Not all of them can be covered in the [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html)
which represents core documentation maintained for each Gradle release.
Moreover, being tied to the Gradle release contribution process and the release cycle makes it more difficult to contribute there.
Even for us, it has been difficult to maintain documentation in such a way,
and many pages have been quite outdated.

So, we decided to build a second resource as an extension to the Gradle User Manual,
with the following in mind:

- Gradle Cookbook remains an official resource under `community.gradle.org`.
  It is not a second-class citizen, just another structure not tied to the Gradle release cycle
- Pages should be focused on offering solutions to end users for particular use cases,
  hence the _Cookbook_
- We follow the Wiki-alike collaboration style,
  with a lower barrier to contribute than `gradle/gradle`.
  Some sections can get explicit maintainers/reviewers over time.
- We use Documentation-as-Code, with simple Markdown or Asciidoc files used as a source
- Minimizing duplication.
  We can include documentation from other sources under the [Gradle GitHub organization](https://github.com/gradle/)

## Table of Contents

- [Gradle Built Tool on CI](/community/cookbook/ci/jenkins/)

## Contributing

Contributions are welcome!
You can extend the Cookbook by adding new recipes, updating the existing ones,
or even creating whole new sections.
Check out the [Contributor Guide](./CONTRIBUTING.md) for more information.

## References

- [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html)
- [Other Documentation Locations](../contributing/documentation/README.md/#locations)
