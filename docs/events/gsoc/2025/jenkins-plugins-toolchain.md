---
title: "Gradle Convention Plugin for Developing Jenkins Plugins"
description: "A project by Aarav Mahajan for GSoC 2025 with the goal to revive and empower the Gradle-based development ecosystem within the Jenkins community, enabling easier, more modern plugin development using Kotlin and Gradle"
---

# GSoC 2025 - Gradle Convention Plugin for Developing Jenkins Plugins

This project aims to modernize Jenkins plugin development with Gradle by updating the [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin) to comply with Jenkins hosting requirements. The goals include achieving feature parity with Maven workflows, improving developer experience through a new convention plugin streamlining the build, test, and release process for Jenkins plugins. This project will provide the Jenkins community with a modern, robust Gradle-based ecosystem by improving developer efficiency and plugin reliability.

<div style="text-align:center;">
  <img src="../images/Jenkins-Gradle.png" alt="Jenkins and Gradle logos" width="600">
</div>

# Status

Passed mid-term evaluation with successful integration of Jenkins BOM, Quality Tools & Static Analysis Integration

## 🚩 Goal

To deliver a production-grade, idiomatic Gradle convention plugin purpose-built for Jenkins plugin development, designed to provide seamless feature parity with the Jenkins Plugin Parent POM (& Maven lifecycle), but leveraging the power & expressiveness of Kotlin & Kotlin DSL. This convention plugin will strictly adhere to the principle of [Convention over Configuration (CoC)](https://en.wikipedia.org/wiki/Convention_over_configuration), enabling Jenkins plugin developers to effortlessly adopt community best practices, security standards, & Jenkins hosting requirements out of the box.

## 🤝 Team

### Contributor

- [Aarav Mahajan](https://github.com/aaravmahajanofficial)

### Mentors

- [Oleg Nenashev](https://github.com/oleg-nenashev)
- [Rahul Somasunderam](https://github.com/rahulsom)
- [Steve Hill](https://github.com/sghill)

## 🧩 Rationale

Jenkins plugin development is currently fragmented across two major build tools: Maven and Gradle. While Maven enjoys mature support through the Jenkins [Parent POM](https://github.com/jenkinsci/plugin-pom), the Gradle ecosystem lags behind due to an outdated and incomplete [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin). This results in:

- Non-compliance with Jenkins Hosting Requirements, making plugin publishing harder

- Poor support for compatibility testing ([PCT](https://github.com/jenkinsci/plugin-compat-tester))

- Cumbersome dependency management and [BOM](https://github.com/jenkinsci/bom) integration

- Inconsistent development experience due to the Groovy-based configuration

- Lack of standardized, reusable configuration via a convention plugin

These issues make it significantly harder for developers, especially those familiar with Gradle, to contribute high-quality plugins to the Jenkins ecosystem.

## 📝 Deliverables

### Integration of Jenkins & Ecosystem BOM Mangement

**Status:** Complete :green_circle:

**Objectives:**

- Simplify dependency management for Jenkins plugin projects, eliminating "dependency hell" by providing robust, convention-driven BOM (Bill of Materials) integration.
- Ensure that developers spend less time troubleshooting version conflicts & more time building features, with reliable, reproducible builds as the default experience.

**Implemented Features:**

- [x] Apply a curated set of BOMs (Bill of Materials) for Jenkins core & major ecosystem dependencies (Spring, Jackson, Jetty, Groovy, Netty, SLF4J, Guava, Log4J, Vert.x, etc.) which leads to transparent, idiomatic BOM management.
- [x] Add support for toggling BOMs on/off via plugin DSL or Gradle properties.
- [x] Users may declare additional BOMs as needed for their plugins, including test-only.

### Quality Tools & Static Analysis Integration

**Status:** Complete :green_circle:

**Objectives:**

- Minimize configuration burden & reduce boilerplate for plugin developers, raising the baseline of code quality across all Jenkins plugins built with Gradle.

**Implemented Features:**

- [x] Provide out-of-the-box integration with industry-standard static analysis & code quality tools (Checkstyle, PMD, SpotBugs, Detekt, Spotless, Jacoco/Kover, OWASP Dependency Check, Dokka, etc.) to enforce Jenkins community best practices.
- [x] Add effortless customization & conditional enablement/disablement of each tool via the plugin DSL or Gradle properties.
- [x] Enforce consistent, modern Kotlin project setup by auto applying recommended compiler options, JVM toolchain, & dependency alignment using a centralized version catalog; minimizing misconfiguration.

### Publish Convention Plugin

**Status:** Complete :green_circle:

- [x] Successfully published the Jenkins Gradle Convention Plugin on the [Gradle Plugin Portal](https://plugins.gradle.org/plugin/io.github.aaravmahajanofficial.jenkins-gradle-convention-plugin) with proper versioning & metadata for discoverability and usability by plugin developers.

## ⏳ What's next?

- Improve the metadata/manifest/pom generation by automatically populating essential & previously missing manifest entries.
- Integrate Plugin Compatibility Tester (PCT)
- Comprehensive, easy-to-follow documentation, integrated in CI/CD
- Solicit feedback from the Jenkins and Gradle communities to guide improvements

## 🌐 References

- [Project Page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/3ujOIGDx)
- [Contributor Proposal](https://docs.google.com/document/d/1W-_rDWrnHSgV3fGdQWSryOmym15e9TEoHlBvQJysJgw/edit?usp=sharing)
- [GitHub Repository](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin)
- [Slack Channel](https://gradle-community.slack.com/archives/C08S0GKMB5G)
