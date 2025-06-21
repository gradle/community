---
Title: "Maven Central publishing plugin for Gradle with new APIs"
Description: "A project by Yongjun Hong for GSoC 2025, focused on developing a Gradle plugin compatible with the new Maven Central publication APIs."
---

# GSoC 2025 - Maven Central publishing plugin for Gradle with new APIs

This project aims to develop a new Gradle plugin compatible with the updated **Maven Central APIs**, simplifying the publishing process through **Kotlin DSL extensions** and automating essential tasks.

The long-term goal of the project is to provide a reliable Maven Central publishing plugin based on the latest Gradle APIs and Kotlin DSL, standardizing and simplifying publishing process across the Gradle ecosystem to help many open-source developers distribute their libraries more easily.

<p align="center">
  <img src="https://github.com/Nouran-11/gradle-gsoc.png/blob/main/Gradle-GSOC.png?raw=true" alt="Gradle and GSoC logos" width="600">
</p>

## Team

### Contributor

- [Yongjun Hong](https://github.com/YongGoose)

### Mentors

- [Oleg Nenashev](https://github.com/oleg-nenashev)

## Organization
- [Kotlin](https://kotlinlang.org/)
- [Gradle](https://gradle.org/)

## Technologies
- Java
- Kotlin
- Gradle
- Maven Central
- Kotlin DSL

## Rationale
Maven Central is a key repository for publishing JVM libraries. It is currently [migrating to a new version](https://central.sonatype.org/news/20250326_ossrh_sunset/) with a different API, which existing Gradle plugins don’t fully support yet.

Developing a Gradle plugin compatible with the new Maven Central API will help library authors publish smoothly and adapt easily to the changes.

## First Coding Phase

### Deliverables
- Implemented a **hierarchical POM** configuration mechanism
- Enabled **per-project overrides** through the project-level DSL

### Summary / Idea
The main focus of this phase was to implement a hierarchical approach to POM metadata configuration, improving usability for multi-module projects.
Inspired by the utility of [pomFromGradleProperties()](https://vanniktech.github.io/gradle-maven-publish-plugin/central/#configuring-the-pom), the plugin now allows users to define shared defaults (e.g., organization name, license, developer info) at the root level, while still enabling fine-grained customization at the individual project level. This significantly reduces boilerplate and promotes consistency across modules in large repositories.

### Next Steps
- Implement validation to detect missing or incorrect metadata early.
- Develop a Generic Maven Central Compliance Verification Tool to catch common publishing errors (e.g., missing signatures, malformed POMs) before release ([#9](https://github.com/YongGoose/kotlin-pom-gradle/issues/9)).

## References
- [Project Page on the GSoC website](https://summerofcode.withgoogle.com/programs/2025/projects/zCRWjfpd)
