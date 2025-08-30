---
title: "Gradle in Google Summer of Code 2025"
description: >
  Gradle participated in GSoC 2025, under the umbrellas of the Kotlin Foundation.
  This page provides details and archive of this program.
---

Gradle participated in GSoC 2025, under the umbrellas of the Kotlin Foundation.
This page provides details and archive of this program.

!!! note

    This is an archive page for Google Summer of Code 2025.
    For the actual state of the program, see [the main GSoC page](../README.md)

## Projects

In the Kotlin Foundation, we had the following Gradle focused projects in 2025:

- [Gradle Convention Plugin for Developing Jenkins Plugins](./jenkins-plugins-toolchain.md) by Aarav Mahajan
- [Improving Configuration Cache and lock contention in key Gradle plugins](./configuration-cache-and-lock-contention.md) by Nouran Atef
- [Enhanced Kotlin Code Quality Reporting with Gradle Problems API: Integration with Detekt and Ktlint](./kotlin-code-quality-with-problems-api.md) by Vanessa Johnson
- [Maven Central publishing plugin for Gradle with new APIs](./maven-central-publishing-with-new-api.md) by Yongjun Hong
- [IntelliJ Platform Gradle Plugin – Gradle Reporting and Parallel Verifications](./intellij-platform-gradle-plugin.md) by Victoria Chuks Alajemba

## Archive

### 2025 Project Ideas

See the list of the project ideas [here](./project-ideas.md).
Not all project ideas have been accepted in 2025,
and we consider repeating some of them in other programs or in later GSoC editions

### Mid-Term Evaluations

Below, there is an exported version of the Mid-term evaluation notes.

#### Gradle Convention Plugin for Developing Jenkins Plugins

* Project page: [https://community.gradle.org/events/gsoc/2025/jenkins-plugins-toolchain/](https://community.gradle.org/events/gsoc/2025/jenkins-plugins-toolchain/)   
* [Mid-term Demo](https://drive.google.com/file/d/1VaGFiRP466RS1FyaT6rT7xskZKXJ50x_/view?usp=drive_link)   
* Main Repo: [https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin)   
* Discussion Channel: `#jenkins-plugin-toolchain` on the Gradle Community Slack   
* Deliverables:  
  * Alpha version of the convention plugin for Gradle Plugin Development in [https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin)   
    * Last commit \- [https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin/commit/39c2a0509a3996a60ba903082924dc1032942360](https://github.com/aaravmahajanofficial/jenkins-gradle-convention-plugin/commit/39c2a0509a3996a60ba903082924dc1032942360) 

#### Building a Modern, Compiler-Integrated Kotlin Language Server

* Project page: [https://github.com/h4-mm-3r/kotlin-lsp](https://github.com/h4-mm-3r/kotlin-lsp)  
* [Mid-term Demo (no audio)](https://drive.google.com/file/d/1vWBwxK8pWeLDJQAuV-B4mSm-ET6R3UnD/view?usp=drive_link)   
* Main Repo: N/A  
* Discussion Channel: `#gsoc-kotlin-lsp-project` on the Kotlin Foundation Slack
* Deliverables:  
  * [https://github.com/H4-MM-3R/kotlin-lsp/releases/tag/v1.5](https://github.com/H4-MM-3R/kotlin-lsp/releases/tag/v1.5)

#### Improving Configuration Cache and Lock Contention in Key Gradle Plugins

* Project page: [https://community.gradle.org/events/gsoc/2025/configuration-cache-and-lock-contention/](https://community.gradle.org/events/gsoc/2025/configuration-cache-and-lock-contention/)   
* [Mid-term Demo Video](https://drive.google.com/file/d/1c8CXnyQpNG0WQOWdWbe-gbxOPOufQAcD/view?usp=drive_link)
* Main Repo: N/A  
* Discussion Channel: `#gsoc-2025-improving-cc` on the Gradle Community Slack  
* Deliverables:  
  * Partial patch for the Nebula Lint Plugin \-  [https://github.com/nebula-plugins/gradle-lint-plugin/pull/433](https://github.com/nebula-plugins/gradle-lint-plugin/pull/433)
  * Blog post with the learnings and tips for developers: [https://dev.to/gradle-community/unlocking-configuration-cache-with-gsoc-contributor-374l](https://dev.to/gradle-community/unlocking-configuration-cache-with-gsoc-contributor-374l)   
  * WiP \- Cookbook page \- [https://github.com/gradle/cookbook/pull/52](https://github.com/gradle/cookbook/pull/52)
  * Fixing Configuration Cache compatibility issue in Play Framework plugin \- [https://github.com/gradle/playframework/pull/207](https://github.com/gradle/playframework/pull/207) 

#### Adding KMP support in Bazel

The project was aborted due to the administrative/compliance issues (unrelated to the contributor's performance)

#### Support Android and iOS targets in Kotlin Multiplatform for Gemini using Vertex AI in Firebase

* Project page: https://summerofcode.withgoogle.com/programs/2025/projects/Ow6J6ami  
* Mid-term Demo: N/A
* Main Repo: https://github.com/SeanChinJunKai/firebase-ai-kmp  
* Discussion Channel: `#gsoc-kmp-gemini-firebase` on the Kotlin Foundation Slack  
* Deliverables:  
  * Sample app: [https://github.com/SeanChinJunKai/firebase-ai-sample](https://github.com/SeanChinJunKai/firebase-ai-sample)  
  * Code:   
    * [https://github.com/SeanChinJunKai/firebase-ai-kmp](https://github.com/SeanChinJunKai/firebase-ai-kmp) (Published to MavenCentral)  
    * [https://github.com/SeanChinJunKai/FirebaseAIBridge](https://github.com/SeanChinJunKai/FirebaseAIBridge)

#### Enhanced Kotlin Code Quality Reporting with Gradle Problems API: Integration with Detekt and Ktlint

* Project page: [https://community.gradle.org/events/gsoc/2025/kotlin-code-quality-with-problems-api/](https://community.gradle.org/events/gsoc/2025/kotlin-code-quality-with-problems-api/)   
* [Mid-term Demo](https://drive.google.com/file/d/1Eulmey166Whm5me3lq7C0IlywSgT5ubr/view?usp=drive_link)
* Main Repo: N/A
* Discussion Channel:   
  * \#problems-api on the Gradle Community Slack  
  * \#detekt on the Kotlin Foundation Slack  
* Deliverables:  
  * [https://github.com/detekt/detekt/pull/8275](https://github.com/detekt/detekt/pull/8275) 

#### IntelliJ Platform Gradle Plugin – Gradle Reporting and Parallel Verifications

* Project page: [https://summerofcode.withgoogle.com/programs/2025/projects/lJoAo8B7](https://summerofcode.withgoogle.com/programs/2025/projects/lJoAo8B7)   
* Mid-term Demo (Raw): [GMT20250718-123713\_Recording\_1920x1080.mp4](https://drive.google.com/file/d/1gUZ_nyLN689sYaEDc4p5QVFpwoDyM0WS/view?usp=sharing)  
* Main Repo: https://github.com/JetBrains/intellij-platform-gradle-plugin  
* Discussion Channel: `#gsoc-ij-gradle-plugin` on the Kotlin Foundation Slack   
* Deliverables:  
  * Integrate Gradle Reporting API  
  * Integrate Problems API

## Maven Central publishing plugin for Gradle with new APIs

* Project page: [https://community.gradle.org/events/gsoc/2025/maven-central-publishing-with-new-api/](https://community.gradle.org/events/gsoc/2025/maven-central-publishing-with-new-api/)   
* [Mid-term Demo](https://drive.google.com/file/d/1McNXyBdIQpEPqTn2ZRjnYJ4E8JNwHMZE/view?usp=drive_link)   
* Main Repo: [https://github.com/YongGoose/kotlin-pom-gradle](https://github.com/YongGoose/kotlin-pom-gradle)   
* Discussion Channel: `#maven-central-publishing` on the Gradle Community Slack  
* Deliverables:  
  * Organization-wide POM Management Options  
  * Artifact POM Validation for compliance with Maven Central requirements  
    * NOTE: signing validation is not yet implemented  
  * [https://github.com/YongGoose/kotlin-pom-gradle](https://github.com/YongGoose/kotlin-pom-gradle) , last commit is [https://github.com/YongGoose/kotlin-pom-gradle/commit/787821af740f17cda3296a6ff88ad3fe78c0c248](https://github.com/YongGoose/kotlin-pom-gradle/commit/787821af740f17cda3296a6ff88ad3fe78c0c248) 
