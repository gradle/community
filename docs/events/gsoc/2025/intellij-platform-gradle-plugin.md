---
title: "IntelliJ Platform Gradle Plugin – Gradle Reporting and Parallel Verifications"
description: > 
    The goal of this project is to assess better reporting and parallel verification
    in the plugin,
    and ultimately implement the necessary changes to the `verifyPlugin` task.
---

In 2025, [Victoria Chuks Alajemba](https://github.com/alajemba-vik) worked on improving the [IntelliJ Platform Gradle Plugin](https://plugins.jetbrains.com/docs/intellij/tools-intellij-platform-gradle-plugin.html).

!!! note

    This is **NOT** the official page of the project.
    We keep it for referencing purposes.

## Project abstract

The IntelliJ Platform Gradle Plugin, the official Gradle plugin for building, testing, verifying, configuring environments, and publishing plugins for IntelliJ IDEs, includes a `VerifyPluginTask` that verifies a plugin against one or multiple IDEs.
Currently, reporting is managed by the Verifier CLI, which employs its custom reporting system to generate verification reports; however, the VerifyPluginTask could benefit from Gradle's Reporting API for more configurable reports.
Additionally, integrating Gradle's Worker API for parallel execution of the `verifyPlugin` task could enhance the IDE plugin development experience.

The goal of this project is to assess the benefits and ultimately implement the necessary changes to the `verifyPlugin` task. Lastly, explore further optimizations to enhance the plugin development workflow.

## Team

* Contributor: [Victoria Chuks Alajemba](https://github.com/alajemba-vik)
* Mentors: [Jakub Chrzanowski](https://github.com/hsz)

## References

* [Project Page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/lJoAo8B7) by Victoria Chuks Alajemba
* [Mid-Term Project Demo](https://drive.google.com/file/d/1gUZ_nyLN689sYaEDc4p5QVFpwoDyM0WS/view?usp=sharing)
* [Gradle Cookbook - Reporting API](https://cookbook.gradle.org/plugin-development/reporting-api/) - a new cookbook page created by Victoria
* [Final Project Report](https://dev.to/victoria_chuks_7e772e1688/gsoc-2025-kotlin-foundation-final-report-3p4c)

## Discussion Channels

* `#gsoc-ij-gradle-plugin` channel on the Kotlin Foundation Slack
