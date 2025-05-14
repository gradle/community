# GSoC 2025 - Project Ideas

This is an archive of the 2025 project ideas about Gradle.
The projects were published in the Kotlin Foundation,
see the list [here](https://kotlinlang.org/docs/gsoc-2025.html).

### 🔍 Clean and actionable reporting for Gradle code quality plugins for Kotlin

Gradle recently introduced a new [Problems API](https://docs.gradle.org/current/userguide/reporting_problems.html)  that allows Gradle and third-party plugins to propagate issues and warnings in a unified way. This API provides clean and actionable error reporting and more insights into the console output, dedicated HTML reports, and connected observability tools. IDEs such as IntelliJ IDEA or Android Studio also have access to the details via Gradle’s tool integration API, and can show warnings right in the code editor. Several core features and plugins have already adopted the Problems API: Java compilation, dependency resolution errors, deprecation warnings, etc. We want the code quality plugins for Kotlin to adopt this API, too; it would greatly improve the developer experience for 100,000+ Kotlin developers using Gradle. 

In this project, we invite contributors to choose a number of Kotlin code quality plugins, such as Ktlint, Detekt, Diktat, ArchUnit, or Checkstyle for Kotlin, and integrate them with Problems API. You can also work on integrating a similar analysis for Gradle builds defined with KotlinDSL. 

* Complexity: Easy or Medium, 90 hrs or 175 hrs  
* Deliverables: Implement Problems API integration in the mentioned plugins  
* Skills to improve: Kotlin, Gradle  
* Potential Mentors: Oleg Nenashev, Balint Hegyi, Reinhold Degenfellner

### 📦 Maven Central publishing plugin for Gradle with new APIs

[Maven Central](https://central.sonatype.com/) is one of the most popular Maven repositories for publishing JVM-focused libraries and projects. It is actively used by Apache Maven or Gradle-based open-source projects, and based on Sonatype Nexus v2, pending migration to a newer version. There is ongoing migration of open source projects to a new Maven Central Instance, which has a very different API implementation and needs special support in the build tool plugins. Developing a Gradle plugin that is compatible with the new Maven Central publication APIs would help the library authors building with Gradle to have a smooth experience with the new process.

Currently there are multiple implementations of Maven Central publishing plugins in Gradle, e.g. the [Maven Publish Plugin](https://docs.gradle.org/current/userguide/publishing_maven.html) or the [New Maven Central Publishing](https://github.com/GradleUp/nmcp) which already tries to adopt the new APIs . A potential contributor, during the application or the community bonding phase, would need to review the implementations and suggest a plugin to be updated, or decide to build a new plugin / fork. The deliverables would include either a new version of an existing plugin for Maven Central publishing or a new plugin for Gradle. We anticipate the implementation to be in Kotlin or Java and to have proper test coverage and documentation. Additional deliverables may include Kotlin DSL extensions to simplify usage of the plugins and [Declarative Gradle](https://declarative.gradle.org/) extensions.

* Complexity: Easy to Medium, 90 hrs to 175 hrs  
* Deliverables: updated Maven Central publishing plugin or a new plugin  
* Skills to improve: Kotlin, Gradle, Maven Repositories  
* Potential Mentors: Gradle team, respective plugin maintainers

### 🚅 Improving Configuration Cache and lock contention in key Gradle plugins 

Gradle is working on [Isolated Projects](https://docs.gradle.org/current/userguide/isolated_projects.html) \- a new feature that greatly extends the configuration cache to further improve performance, particularly the performance of Android Studio and Intellij IDEA sync. From the developer experience standpoint, it is one of the most anticipated features in Gradle.

One of the problems for Isolated projects is the lock contention in the Gradle core and plugins sometimes getting in the way of parallel execution. We would like to reduce the lock contention, especially in the key Gradle Build Tool plugins for Java, Kotlin, Android and Kotlin Multiplatform ecosystems. Contributors are welcome to choose the deliverables, based on their interest and the desired project size. Potential deliverables include but not limited to:

* Embed the [Configuration Cache Report](https://github.com/gradle/configuration-cache-report) tool into the Gradle Profiler (or "implement a GitHub Action for it"?)  
* Profile Gradle and a few popular Gradle plugins in various projects, with automation of the test suite on GHA  
* Determine potential areas and plugins where lock contention can be reduced, with or without Configuration Cache  
* While around, contribute to other areas of [Configuration Cache compatibility](https://github.com/gradle/gradle/issues/13490) in the target plugins  
* Implement some of the discovered improvements

Summary: 

* Complexity: Easy to Large, 90 hrs to 350 hrs  
* Deliverables: Implementing extensibility features in the Kotlin DSL for Gradle and improving support for common project integrations  
* Skills to improve: Kotlin, Gradle, Java, Performance Analysis, Profiling  
* Potential Mentors: Oleg Nenashev, Laura Kassovic

### 🔌 Gradle Convention plugin for developing Jenkins Plugins

There are more than 50 Jenkins plugins that are implemented with Gradle. There is a [Gradle JPI plugin](https://github.com/jenkinsci/gradle-jpi-plugin) but it is not fully compliant with Jenkins hosting requirements, and needs an update. In this project idea, the aim would be to recover the Gradle developer flow for Jenkins, reach feature parity with the Apache Maven flow ([Parent POM](https://github.com/jenkinsci/plugin-pom), [Plugin Compatibility Tester](https://github.com/jenkinsci/plugin-compat-tester), [Jenkins Bill of Materials](https://github.com/jenkinsci/bom), etc.) and to improve the developer experience for those who develop Jenkins plugins with Gradle.

Contributors are welcome to choose the deliverables, based on their interest and the desired project size. Potential deliverables include but not limited to:

* Refreshing the Gradle JPI plugin and making it compliant with hosting best practices
* Migrating the Gradle JPI plugin codebase from Groovy to Kotlin
* Implementing a new convention plugin for Jenkins Plugins that would cover the main features of Jenkins plugin Parent POM, with Kotlin and Kotlin DSL. This would include not just building the plugin, but also testing and static analysis according to Jenkins’ best practices
* Adopting the refreshed plugin and/or the convention plugin in the most popular Gradle plugin, including the Gradle Plugin itself
* Integrating Gradle Plugins into Plugin Compatibility Tester and Bill of Materials
* Documenting the updated Gradle development flow for Jenkins plugins

Summary:

* Complexity: Easy to Large, 90 hrs or 350 hrs
* Deliverables: Updated Gradle JPI Plugin AND/OR new convention plugin for Jenkins, published on Jenkins Update Center and Gradle Plugin Portal
* Skills to improve: Kotlin DSL, Kotlin, Gradle, Jenkins, Java
* Potential Mentors: Oleg Nenashev, Stefan Wolf

### 📓 Kotlin DSL documentation samples test framework

Many projects, including Gradle, have a lot of Kotlin DSL samples and code snippets (see the Gradle Docs for examples). Testing them against multiple versions poses certain challenges because the snippets often represent incomplete code for the sake of brevity. We would like to build a test framework that simplifies the verification of those samples within a unit test framework (Kotest or JUnit 5) on GitHub Actions and Teamcity.

* Complexity: Easy or Medium, 90 hrs or 175 hrs
* Deliverables: Implementing extensibility features in the Kotlin DSL for Gradle and improving support for common project integrations
* Skills to improve: Kotlin, Gradle, Java, Static Analysis
* Potential Mentors: Oleg Nenashev

### 🔌 IntelliJ Platform Gradle Plugin – Gradle Reporting and Parallel Verifications

The IntelliJ Platform Gradle Plugin, a plugin for the Gradle build system, simplifies configuring your environment for building, testing, verifying, and publishing plugins for IntelliJ-based IDEs. The plugin manages the build, test, and verification steps while keeping up with the constant changes introduced in the IntelliJ Platform. The IntelliJ Platform Gradle Plugin is used by JetBrains, third-party developers, and external companies to integrate their workflows with JetBrains tools.

* Complexity: Medium, 175 hrs
* Skills to improve: Kotlin, Gradle, IntelliJ Platform
* Potential Mentors: Jakub Chrzanowski, JetBrains
