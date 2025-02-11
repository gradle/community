---
title: "Gradle in Google Summer of Code"
description: >
  Gradle has participated in GSoC since 2023, under the umbrellas of the Kotlin Foundation and the Eclipse Foundation.
  Join us!
---

[Google Summer of Code (GSoC)](https://summerofcode.withgoogle.com/) is a global,
online program focused on bringing new contributors into open source software development.
GSoC Contributors work with an open source organization on a 12+ week programming project
under the guidance of mentors.
Gradle has participated in GSoC since 2023.

## GSoC 2025

In 2025, we plan to participate under the umbrella of the [Kotlin Foundation](https://kotlinfoundation.org/).
There might be related projects in other mentoring organizations.

### Project Ideas

#### 📦 Maven Central publishing plugin for Gradle with new APIs

[Maven Central](https://central.sonatype.com/) is one of the most popular Maven repositories for publishing JVM-focused libraries and projects. It is actively used by Apache Maven or Gradle-based open-source projects, and based on Sonatype Nexus v2, pending migration to a newer version. There is ongoing migration of open source projects to a new Maven Central Instance, which has a very different API implementation and needs special support in the build tool plugins. Developing a Gradle plugin that is compatible with the new Maven Central publication APIs would help the library authors building with Gradle to have a smooth experience with the new process.

Currently there are multiple implementations of Maven Central publishing plugins in Gradle, e.g. the [Maven Publish Plugin](https://docs.gradle.org/current/userguide/publishing_maven.html) or the [New Maven Central Publishing](https://github.com/GradleUp/nmcp) which already tries to adopt the new APIs . A potential contributor, during the application or the community bonding phase, would need to review the implementations and suggest a plugin to be updated, or decide to build a new plugin / fork. The deliverables would include either a new version of an existing plugin for Maven Central publishing or a new plugin for Gradle. We anticipate the implementation to be in Kotlin or Java and to have proper test coverage and documentation. Additional deliverables may include Kotlin DSL extensions to simplify usage of the plugins and [Declarative Gradle](https://declarative.gradle.org/) extensions.

Summary:

* Deliverables: updated Maven Central publishing plugin or a new plugin  
* Skills to improve: Kotlin, Gradle, Maven Repositories  
* Potential Mentors: Gradle team, respective plugin maintainers

#### 🚅 Improving Configuration Cache and lock contention in key Gradle plugins 

Gradle is working on [Isolated Projects](https://docs.gradle.org/current/userguide/isolated_projects.html) \- a new feature that greatly extends the configuration cache to further improve performance, particularly the performance of Android Studio and Intellij IDEA sync. From the developer experience standpoint, it is one of the most anticipated features in Gradle.

One of the problems for Isolated projects is the lock contention in the Gradle core and plugins sometimes getting in the way of parallel execution. We would like to reduce the lock contention, especially in the key Gradle Build Tool plugins for Java, Kotlin, Android and Kotlin Multiplatform ecosystems. Contributors are welcome to choose the deliverables, based on their interest and the desired project size. Potential deliverables include but not limited to:

* Embed the [Configuration Cache Report](https://github.com/gradle/configuration-cache-report) tool into the Gradle Profiler (or "implement a GitHub Action for it"?)  
* Profile Gradle and a few popular Gradle plugins in various projects, with automation of the test suite on GHA  
* Determine potential areas and plugins where lock contention can be reduced, with or without Configuration Cache  
* While around, contribute to other areas of [Configuration Cache compatibility](https://github.com/gradle/gradle/issues/13490)  
*  in the target plugins  
* Implement some of the discovered improvements

Summary: 

* Complexity: Easy to Large Medium, 90 hrs to 350 hrs  
* Deliverables: Implementing extensibility features in the Kotlin DSL for Gradle and improving support for common project integrations  
* Skills to improve: Kotlin, Gradle, Java, Performance Analysis, Profiling  
* Potential Mentors: Oleg Nenashev, Laura Kassovic

#### 🔌 Gradle Convention plugin for developing Jenkins Plugins

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

#### 📓 Kotlin DSL documentation samples test framework

Many projects, including Gradle, have a lot of Kotlin DSL samples and code snippets (see the Gradle Docs for examples). Testing them against multiple versions poses certain challenges because the snippets often represent incomplete code for the sake of brevity. We would like to build a test framework that simplifies the verification of those samples within a unit test framework (Kotest or JUnit 5) on GitHub Actions and Teamcity.

* Complexity: Easy or Medium, 90 hrs or 175 hrs
* Deliverables: Implementing extensibility features in the Kotlin DSL for Gradle and improving support for common project integrations
* Skills to improve: Kotlin, Gradle, Java, Static Analysis
* Potential Mentors: Oleg Nenashev

#### Suggest your own project idea!

Original project ideas are welcome!
If you are interested, make a suggestion on our Slack channel (see below).

## Communication channels

- `#gsoc` on the [Gradle Community Slack](https://gradle.org/slack-invite)
- `#gsoc` on the [Kotlin Foundation Slack](https://kotlinlang.org/community/)

## Resources

- [Coordination Meeting Notes and Recordings](https://drive.google.com/drive/folders/19PAIb36Bm_9Y300oJ_2JBMFU6kjOwNvX?usp=drive_link)

### For Contributors/Mentees

See the project descriptions for references to particular newcomer-friendly issues or
learning scenarios.
If nothing is available there, it is recommended to start learning Gradle basics, if you aren't already familiar with them.
Then, we recommend looking into some of the newcomer-friendly issues in the target project or in Gradle as whole.
Prior track of contributions during the application phase is important during the project proposal reviews,
because it helps us to build impression about the candidate.

To get started:

1. Join the `#gsoc` channel on the [Gradle community Slack](https://gradle.org/slack-invite).
  If there are such channels in the foundations, please join them too
2. Explore the [Getting Started with Gradle](https://docs.gradle.org/current/userguide/getting_started_eng.html) and the relevant [topic-specific Gradle Guides](https://gradle.org/guides/)
3. Check out the [contributing guidelines](../../contributing/README.md), try addressing some of the newcomer friendly issues
4. Discuss the project ideas with your mentors on the public channels

References:

- [Official GSoC website](https://summerofcode.withgoogle.com/) -
  all official guidelines are here. Please refer there about eligibility, stipend, and other similar matters managed by Google during the GSoC program
- [Best practices for GSoC contributors](https://www.jenkins.io/projects/gsoc/students/),
  by the Jenkins community - we will be using a similar framework

### For Mentors

We invite Gradle community members, if they are interested in mentoring, to submit their project ideas.

Mentoring requires a time commitment of several hours a week.
It is a great opportunity to have someone prototyping your idea
that it is not on the short term roadmap
but remains interesting to you and valuable to the Gradle community.

References:

- [GSoC website](https://summerofcode.withgoogle.com/)
- [Jenkins mentor guide](https://www.jenkins.io/projects/gsoc/mentors/) -
  Realistic expectations from mentors which we maintain in the Jenkins project
- [Mentorship Programs. Growing new community leaders](https://speakerdeck.com/onenashev/mentorship-programs-growing-new-team-and-community-leaders) -
  a presentation by Oleg Nenashev on mentorship programs

## Archive

### Previous Years

- [GSoC 2024](./2024/README.md) - 3 Projects
- [GSoC 2023](./2023/README.md) - 1 projects


