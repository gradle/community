# GSoC 2024. Declarative Syntax and Enhancements for the Checkstyle Plugin

## Goal
- **Enhanced Functionality**: Enhance the Checkstyle plugin to support more of Checkstyle's features.
- **Better Declarativity**: improve the declarative nature of Kotlin DSL when integrating plugins.

## Status
Selected

## Team
#### Authors
- [Hongjie Wei](https://github.com/JayWei1215) - `@JayWei1215`

#### Mentors
- [@oleg-nenashev](https://github.com/oleg-nenashev)

## Background
- Checkstyle is a powerful tool, but currently, the Checkstyle plugin in Gradle may not support all of Checkstyle's features.
- Kotlin DSL does not provide good declarative support when it comes to integrating plugins.

## Implementation

- **Enhanced Functionality** - The CheckstyleExtension class is the extension class of the Gradle Checkstyle plugin.It is used to configure various options of the Checkstyle plugin.By Creating a new subclass of CheckstyleExtension and add some new properties, we can make the Checkstyle plugin support more of Checkstyle's features.

- **Better Declarativity** - Create a Kotlin class to serve as the entry point for the DSL. This class can inherit from CheckstyleExtension. Within the DSL class, define properties and methods specific to the DSL, allowing for the configuration of Checkstyle's various options.

## Target Repositories


## Deliverables

- Create a new branch in the project repository specifically for developing the Checkstyle plugin functionality, which will contain the code necessary for implementing and testing the Checkstyle plugin.

-  Provide an enhanced version of the Gradle Checkstyle plugin. It will support additional Checkstyle features, such as code complexity, duplication, and dependency checks.

-  Provide an improved Kotlin DSL, particularly enhancing its declarativity when integrating plugins.

## Links
- [Contributor Proposal](https://docs.google.com/document/d/1q0NFuoR1F9wcQxyFEC0m1qOspBSyq9TbyuOZhldHybk/edit?usp=sharing)
- [Project Proposal](https://kotlinlang.org/docs/gsoc-2024.html#kotlin-dsl-improvements-for-declarative-gradle-medium-175-hrs)
- [Declarative Gradle](https://blog.gradle.org/declarative-gradle)
- [Checkstyle](https://github.com/checkstyle/checkstyle)
- [Checkstyle Plugin](https://docs.gradle.org/current/userguide/checkstyle_plugin.html)
