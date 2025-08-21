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


## Deliverables
1. **Hierarchical POM Management** (Completed 🙂)
    - Define POM metadata once at the root project level and automatically inherit it across all submodules.
    - Allow submodules to override specific properties when needed, ensuring flexibility while maintaining consistency.
    - Minimize repetitive configuration in multi-module projects.

2. **Comprehensive POM Validation** (Completed 🙂)
    - Validate POM files for required fields, proper formatting, and compliance with Maven Central standards before publishing.
    - Proactively prevent common publishing errors and ensure repository compatibility.

3. **Automated Artifact Signature Presence Check** (Completed 🙂)
    - Automatically check whether artifact signatures are present during the build process before publishing.
    - Detect missing signatures early to prevent deployment failures.

4. **Plugin Deployment to Gradle Plugin Portal** (Completed 🙂)
    - Provide three plugin variants:
        - Hierarchical POM management: [For build.gradle.kts](https://plugins.gradle.org/plugin/io.github.yonggoose.kotlin-pom-gradle-project), [For settings.gradle.kts](https://plugins.gradle.org/plugin/io.github.yonggoose.kotlin-pom-gradle-setting)
        - POM Validation: [Validation Plugin](https://plugins.gradle.org/plugin/io.github.yonggoose.kotlin-pom-gradle-artifact-check-project)

5. **User-Friendly Installation & Documentation** (Planned 🤔)
    - Offer detailed installation and usage guides, including a comprehensive README and demo video.

6. **Community-Driven Expansion Plans** (Planned 🤔)
    - Plan for additional validation rules, enhanced integration with popular Gradle plugins, and expanded customization options.
    - Continuously improve the plugin based on community feedback.

7. **Open-Source Contribution** (Planned 🤔)
    - Welcome contributions in various forms, including bug reports, feature requests, documentation improvements, and code contributions.
    - Encourage participation through the GitHub repository.

## What's Next

Community interest and engagement are essential for the long-term success of this project. To achieve this, the plugin should be promoted in various places to actively attract users and contributors.

- **Writing Blog Posts**: Create blog posts showcasing use cases that integrate with VannikTech's Maven Publish, helping to promote the plugin.
- **Promoting on Social Media**: Share and promote the plugin on Gradle’s Slack channel as well as other developer communities.


## References
- [Project Page on the GSoC website](https://summerofcode.withgoogle.com/programs/2025/projects/zCRWjfpd)
- [Kotlin-pom-gradle Repository](https://github.com/YongGoose/kotlin-pom-gradle/pull/8)
- [Gradle Plugin Portal](https://plugins.gradle.org/u/YongGoose)
- [Discussion Channel](https://gradle-community.slack.com/archives/C08S108K9NY)
