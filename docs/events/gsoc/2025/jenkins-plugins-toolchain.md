---
title: "Gradle Convention Plugin for Developing Jenkins Plugins"

description: "A project by Aarav Mahajan for GSoC 2025 with the goal to revive and empower the Gradle-based development ecosystem within the Jenkins community, enabling easier, more modern plugin development using Kotlin and Gradle"
---

# GSoC 2025 - Gradle Convention Plugin for Developing Jenkins Plugins

![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=%2330363c)
[![GitHub](https://img.shields.io/badge/GitHub-Repository?style=flat&logo=github&logoColor=white&labelColor=%2330363c&color=%237b53fb)](https://github.com/jenkinsci/gradle-convention-plugin)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg?&labelColor=%2330363c)](https://opensource.org/licenses/Apache-2.0)
[![Slack](https://img.shields.io/badge/Slack-%23jenkins--plugin--toolchain-4A154B?&logo=slack&logoColor=white&&labelColor=%2330363c)](https://gradle-community.slack.com/archives/C08S0GKMB5G)

> **TL;DR:** Make **Gradle a first-class**, **compliant**, **low-friction toolchain for Jenkins plugin development**—on par with (and nicer to use than) Maven.

## Overview

This project aims to make Gradle a first-class tool for Jenkins plugin development by introducing a modern, Kotlin-first convention plugin built on top of the [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin). This convention plugin will strictly adhere to the principle of [Convention over Configuration (CoC)](https://en.wikipedia.org/wiki/Convention_over_configuration). Its objectives are to ensure full compliance with Jenkins hosting requirements, achieve feature parity with Maven-based workflows, and deliver a streamlined developer experience. By automating best practices for build, test, and release, this project empowers the Jenkins community with a robust, future-proof, and efficient Gradle-based ecosystem—improving both developer productivity and plugin reliability.

<figure>
  <img src="https://github.com/jenkinsci/gradle-convention-plugin/blob/main/docs/img/logo.png?raw=true"  alt="Project Banner"  width="600">
  <figcaption style="font-size:14px; color:#f0f0f0; text-align:center; margin-top:8px; line-height:1.4; text-shadow: 1px 1px 2px rgba(0,0,0,0.7);">
    Smarter Jenkins plugin builds with Gradle — simple, fast, and modern.
  </figcaption>
</figure>

## Status

- **Current Phase:** Completed | Actively Maintained & Evolving :cyclone:
- **Highlights:**
  - Passed mid-term evaluation | [Watch Mid-term Demo Video](https://drive.google.com/file/d/1VaGFiRP466RS1FyaT6rT7xskZKXJ50x_/view)
  - Hosted on the [official Jenkins GitHub organization](https://github.com/jenkinsci/gradle-convention-plugin)

## Team

### Contributor

- [Aarav Mahajan](https://github.com/aaravmahajanofficial)

### Mentors

- [Oleg Nenashev](https://github.com/oleg-nenashev)

- [Rahul Somasunderam](https://github.com/rahulsom)

- [Steve Hill](https://github.com/sghill)

## Rationale

- **Limitations of the Current Jenkins Build Ecosystem:**

  - Jenkins plugin development is tightly coupled with Maven ([Parent POM](https://github.com/jenkinsci/plugin-pom), [Plugin Compatibility Tester](https://github.com/jenkinsci/plugin-compat-tester), metadata, CI pipelines).
  - Gradle, though powerful, lacks standardized, hosting-compliant workflows, limiting adoption.

- **Existing Gradle JPI plugin is insufficient:**

  - _Non-compliance with Jenkins hosting requirements_ → blocks acceptance

  - _No [Plugin Compatibility Tester (PCT)](https://github.com/jenkinsci/plugin-compat-tester) support_ → weak cross-version testing

  - _Dependency management & BOM gaps_ → unreliable builds

  - _Outdated Groovy-based codebase_ → harder to maintain

  - _No convention plugin_ → developers face more configuration overhead

- **Developers need modern, efficient, and maintainable workflows:**
  Despite Gradle strengths, Jenkins plugin development continues to be dominated by Maven due to deep alignment of core infrastructure with Maven conventions.

  Key Gradle advantages:

  - Extensible build logic defined in code rather than rigid XML
  - Faster build times with incremental builds, caching, and the Gradle Daemon
  - A developer-friendly experience with Kotlin and Groovy DSLs, plus interactive tooling
  - [**Convention Plugins**](https://docs.gradle.org/current/samples/sample_convention_plugins.html) — a powerful way to share and reuse standardized build logic across projects. They can be combined like traits, much like multiple or diamond inheritance in OOP. In contrast, Maven’s parent POM model only allows a single parent (since Maven 3), forcing developers to rely on heavy profile usage and boilerplate.

!!! note

    A new “JPI2” variant of the Gradle JPI Plugin was introduced by Rahul and Steve, adding support for Gradle 8+, improved dependency handling, and a modern architecture. The gradle convention plugin is designed to be forward-compatible, once JPI2 APIs stabilize, we plan to migrate the convention plugin to leverage it for an even better experience.

## Deliverables

### Integration of Jenkins & Ecosystem BOM Management

**Status:** Complete

**Objectives:**

- Simplify dependency management for Jenkins plugin projects, eliminating "dependency hell" by providing robust, convention-driven BOM (Bill of Materials) integration.

- Ensure that developers spend less time troubleshooting version conflicts & more time building features, with reliable, reproducible builds as the default experience.

**Implemented Features:**

- [x] Apply a curated set of BOMs (Bill of Materials) for Jenkins core & major ecosystem dependencies (Spring, Jackson, Jetty, Netty, SLF4J, Guava, Log4J, Vert.x, etc.) which leads to transparent, idiomatic BOM management.

- [x] Add support for toggling BOMs on/off via plugin DSL or Gradle properties.

- [x] Users may declare additional BOMs as needed for their plugins, including test-only.

### Quality Tools & Static Analysis Integration

**Status:** Complete

**Objectives:**

- Minimize configuration burden & reduce boilerplate for plugin developers, raising the baseline of code quality across all Jenkins plugins built with Gradle.

**Implemented Features:**

- [x] Provide out-of-the-box integration with industry-standard static analysis & code quality tools (Checkstyle, PMD, SpotBugs, Detekt, Spotless, Jacoco/Kover, OWASP Dependency Check, Dokka, etc.) to enforce Jenkins community best practices.

- [x] Add effortless customization & conditional enablement/disablement of each tool via the plugin DSL or Gradle properties.

- [x] Enforce consistent, modern Kotlin project setup by auto applying recommended compiler options, JVM toolchain, & dependency alignment using a centralized version catalog; minimizing misconfiguration.

### Publish Convention Plugin

**Status:** Complete

- [x] Successfully published the Jenkins Gradle Convention Plugin on the [Gradle Plugin Portal](https://plugins.gradle.org/plugin/io.github.aaravmahajanofficial.jenkins-gradle-convention-plugin) with proper versioning & metadata for discoverability and usability by plugin developers.

### Add Unit/Integration Tests

**Status:** Complete | Actively Expanding

**Related to:** [#112](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin/issues/112)

### Fix Metadata Generation

**Status:** Complete

**Objectives:**

- Improve the metadata/manifest/pom generation by automatically populating essential & previously missing manifest entries.

**Resolved in**: [#134](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin/issues/134)

**Implementation Features:**

- [x] Programmatically injected the missing manifest attributes in the `GenerateJenkinsManifestTask` of the `gradle-jpi-plugin` by creating an additional manifest file and merging it with upstream manifest files.

### Native-Gradle Support for Plugin Compatibility Tester (PCT)

**Status:** Under Review

**Objectives:**

- Provide **integration of PCT** within Gradle builds, for enabling seamless cross-version testing of Jenkins plugins.

**Pull Request:** [#795](https://github.com/jenkinsci/plugin-compat-tester/pull/795)

**Implemented Features:**

- [x] Add ExternalGradleRunner and GradleExecutionException for Gradle support
- [x] Add support for extracting metadata from Gradle-generated POM files by `gradle-jpi-plugin`

### Jenkins Plugin Hosting Request

**Status:** In Progress

**Objectives:** To get plugin source code hosted in a repository in the `jenkinsci` GitHub organization.

**Resolved in:** [#4608](https://github.com/jenkins-infra/repository-permissions-updater/issues/4608)

### Solicit Feedback

**Status:** In progress, actively collecting feedback

**Objectives:** Gather input from the Jenkins & Gradle communities to guide improvements and ensure the plugin meets developer needs.

**Activites:**

- [Blog on Gradle Community (Dev.to) – Gradle Convention Plugin for Developing Jenkins Plugins](https://dev.to/gradle-community/gradle-convention-plugin-for-developing-jenkins-plugins-4n1d)
- [Announcement at Jenkins Developer Mailing List](https://groups.google.com/g/jenkinsci-dev/c/00r_hESYtKY)
- [Jenkins.io Blog – Gradle Convention Plugin for Jenkins Plugin Development](https://github.com/jenkins-infra/jenkins.io/pull/8391) - Under Review

## Roadmap

Next steps for plugin delivery and integration:

- Support continuous delivery for Jenkins plugins
- Integrate seamlessly with Jenkins pipelines (e.g., [buildPluginWithGradle](https://github.com/jenkins-infra/pipeline-library/blob/master/vars/buildPluginWithGradle.groovy) for CI)
- Migrate to Gradle-JPI2-Plugin when new APIs are available

## References

- [Project Page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/3ujOIGDx)

- [Contributor Proposal](https://docs.google.com/document/d/1W-_rDWrnHSgV3fGdQWSryOmym15e9TEoHlBvQJysJgw/edit?usp=sharing)

- [GitHub Repository](https://github.com/jenkinsci/gradle-convention-plugin)

- Discussion channel: `#jenkins-plugin-toolchain` on the [Gradle Community Slack](https://slack.gradle.org/)
