---
title: "The Gradle Cookbook"
description: >
  Gradle Cookbook is an open-source collection of recipes, guides and examples for the Gradle Build Tool.
---

Gradle Cookbook is an open-source collection of recipes, guides and examples for the Gradle Build Tool.
This is a complementary resource to the official [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html),
which covers core capabilities maintained by the Gradle team.

The goal of this portal is to offer solution-based documentation for end users about external integrations,
including but not limited to 
CI/CD tools, IDEs,
support for languages and frameworks,
and various peripheral tools.

In the Gradle Cookbook, _Gradle Build Tool_ is abbreviated _Gradle_.

!!! note
    The Gradle Cookbook is under active development (see the roadmap item [here](https://github.com/gradle/community/issues/42)).
    Its structure, scope and links may change, and we're working on adding more content.
    Any contributions are welcome, see the [Contributor Guide](./CONTRIBUTING.md)!

## Why and How?

The Gradle Build Tool ecosystem is huge, it includes many plugins, integrations, developer tools and other components.
Not all of them can be covered in the [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html)
which represents core documentation maintained for each Gradle release.
Moreover, being tied to the Gradle release contribution process and the release cycle makes it more difficult to contribute there.
Maintaining documentation has been challenging for us as well,
leading to many outdated pages.

So, we decided to build a second resource as an extension to the Gradle User Manual,
with the following in mind:

- Gradle Cookbook remains an official resource under `community.gradle.org`.
  It is not a second-class citizen, just another structure that is not tied to the Gradle release cycle
- Pages should be focused on offering solutions to end users for particular use cases,
  hence the _Cookbook_
- We follow the Wiki-alike collaboration style,
  with a lower barrier to contribute than `gradle/gradle`.
  Some sections can get explicit maintainers/reviewers over time.
- We use Documentation-as-Code, with simple Markdown or Asciidoc files used as a source
- Minimizing duplication.
  We can include documentation from other sources under the [Gradle GitHub organization](https://github.com/gradle/)

## Chapters

- [Gradle for Kotlin development](./kotlin/README.md)
- [Gradle for Android development](./android/README.md)
- [Gradle on Continuous Integration](./ci/README.md)

More chapters will be added soon, based on contributions.

## Contributing

Contributions are welcome!
You can extend the Cookbook by adding new recipes (e.g. by porting your blogpost),
updating the existing ones,
or even creating whole new sections.
Check out the [Contributor Guide](./CONTRIBUTING.md) for more information.

## Trademark Notice

Gradle and the Gradlephant logo (the "Gradle Marks") are registered trademarks of Gradle, Inc. and/or its subsidiaries.
Use of the Gradle Marks the Gradle Cookbook pages is for identification purposes only and does not imply sponsorship or endorsement by Gradle, Inc.
In the Gradle Cookbook, "Gradle" typically means "Gradle Build Tool" and does not reference Gradle Inc. and/or its subsidiaries.

See the [Gradle Branding Guidelines](https://gradle.com/brand/) for more information about
trademark usage and the approval process.

## References

- [Gradle User Manual](https://docs.gradle.org/current/userguide/userguide.html)
- [Other Documentation Locations](../contributing/documentation/README.md/#locations)
