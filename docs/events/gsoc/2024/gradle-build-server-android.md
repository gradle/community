# Gradle Build Server – support for Android projects

This project aims to enhance [Build Server for Gradle](https://github.com/microsoft/build-server-for-gradle) from Microsoft by integrating powerful Android Studio features. Bridging the gap between Android Studio and [Build Server for Gradle](https://github.com/microsoft/build-server-for-gradle), will significantly improve the development experience for many Android developers using IDEs based on [Build Server Protocol (BSP)](https://build-server-protocol.github.io).

## Status
Accepted

## Goal

1. Implement auto-discovery and task cancelation ([issue #58](https://github.com/microsoft/build-server-for-gradle/issues/58))
2. Retry when user-specified Gradle Java Home is incompatible ([issue #75](https://github.com/microsoft/build-server-for-gradle/issues/75))
3. Show error messages on client when incompatiblity occur ([issue #76](https://github.com/microsoft/build-server-for-gradle/issues/76))

## Team

### Contributor

- [@Tanish-Ranjan](https://github.com/Tanish-Ranjan)

### Mentors

- [@oleg-nenashev](https://github.com/oleg-nenashev)
- [@donat](https://github.com/donat)
- [@hegyibalint](https://github.com/hegyibalint)

## Rationale

As the popularity of Android development grows, the need for efficient build automation tools like the Gradle Build Server becomes increasingly important. However, current limitations in identifying and managing common Gradle functionalities used in Android projects within the server can hinder developer workflows. This project aims to bridge this gap by introducing functionalities specifically tailored to Android development.

## Deliverables

### Auto-discovery

- Implement logic within the Gradle Build Server to automatically identify incoming build requests originating from Android projects.
- Utilize the Build Server Protocol (BSP) messages exchanged between the server and the build tool (Gradle) to analyze project information (e.g., directory structures, file names, build configurations).

### Task Cancellation ([issue #58](https://github.com/microsoft/build-server-for-gradle/issues/58)):

- Design and implement functionalities for cancelling tasks specifically associated with Android builds.
- Develop mechanisms to identify these tasks (e.g., analyzing task names, dependencies, or flags within BSP messages).
- Establish communication channels with Gradle to transmit cancellation requests (potentially extending BSP or implementing custom mechanisms).

### Improved Gradle Java Home Handling ([issue #75](https://github.com/microsoft/build-server-for-gradle/issues/75) and [issue #76](https://github.com/microsoft/build-server-for-gradle/issues/76)):

- Implement logic to handle scenarios where the user-specified Gradle Java Home is incompatible with the server's environment.
- Develop mechanisms to detect incompatibility (e.g., checking version conflicts, missing libraries, unsupported configurations).
- Implement retry logic (e.g., using a default Gradle Java Home or prompting the user for a compatible version).
- Enhance error messages. Provide clear and informative messages displayed on the client-side to guide users towards resolving incompatibility issues (e.g., suggesting compatible Gradle versions or setting environment variables).

### Documentation:

- Create detailed user guides and developer documentation for the implemented functionalities (auto-discovery, task cancellation, improved Gradle Java Home incompatibility handling).
- Ensure the documentation covers usage instructions and troubleshooting steps for the added functionalities.
- Using clear examples and diagrams to enhance understanding.

### Unit and Integration Testing:

- Implement unit tests to ensure the accuracy and reliability of the implemented functionalities.
- Unit tests should thoroughly cover specific components like auto-discovery logic, task identification mechanisms, and Gradle Java Home handling logic.
- Conduct integration tests to verify seamless functionality within the Gradle Build Server environment.
- Integration tests should simulate real-world build scenarios and interactions between different server components.

## Links

- [Project Proposal](https://kotlinlang.org/docs/gsoc-2024.html#gradle-build-server-support-for-android-projects-medium-or-hard-175-hrs-or-350-hrs)
- [Contributor Proposal](https://gradle-community.slack.com/files/U06R0NWDM4J/F06S9HX9VMZ/gsoc_proposal.pdf)
