---
title: "Gradle Convention Plugin for Developing Jenkins Plugins"
description: "A project by Aarav Mahajan for GSoC 2025 with the goal to revive and empower the Gradle-based development ecosystem within the Jenkins community, enabling easier, more modern plugin development using Kotlin and Gradle"
---

# GSoC 2025 - Gradle Convention Plugin for Developing Jenkins Plugins

This project aims to modernize Jenkins plugin development with Gradle by updating the [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin) to comply with Jenkins hosting requirements. The goals include achieving feature parity with Maven workflows, migrating the codebase from Groovy to Kotlin, and improving developer experience through a new convention plugin streamlining the build, test, and release process for Jenkins plugins. This project will provide the Jenkins community with a modern, robust Gradle-based ecosystem by improving developer efficiency and plugin reliability.

<p align="center">
  <img src="../images/Jenkins-Gradle.png" alt="Jenkins and Gradle logos" width="600" style="height:auto;">
</p>

## Team

### Contributor

- [Aarav Mahajan](https://github.com/aaravmahajanofficial)

### Mentors

- [Oleg Nenashev](https://github.com/oleg-nenashev)
- [Rahul Somasunderam](https://github.com/rahulsom)
- [Steve Hill](https://github.com/sghill)

## Rationale

Jenkins plugin development is currently fragmented across two major build tools: Maven and Gradle. While Maven enjoys mature support through the Jenkins [Parent POM](https://github.com/jenkinsci/plugin-pom), the Gradle ecosystem lags behind due to an outdated and incomplete [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin). This results in:

- Non-compliance with Jenkins Hosting Requirements, making plugin publishing harder

- Poor support for compatibility testing ([PCT](https://github.com/jenkinsci/plugin-compat-tester))

- Cumbersome dependency management and [BOM](https://github.com/jenkinsci/bom) integration

- Inconsistent development experience due to the Groovy-based configuration

- Lack of standardized, reusable configuration via a convention plugin

These issues make it significantly harder for developers, especially those familiar with Gradle, to contribute high-quality plugins to the Jenkins ecosystem.

## References

- [Project Page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/3ujOIGDx)
- [Contributor Proposal](https://docs.google.com/document/d/1W-_rDWrnHSgV3fGdQWSryOmym15e9TEoHlBvQJysJgw/edit?usp=sharing)
