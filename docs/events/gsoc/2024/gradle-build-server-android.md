# GSoC 2024. Gradle Build Server – support for Android projects

This project aims to enhance [Gradle Build Server](https://github.com/microsoft/build-server-for-gradle) project from Microsoft by integrating powerful Android Studio features. Bridging the build process gap between [Android Studio](https://developer.android.com/studio) and [Gradle Build Server](https://github.com/microsoft/build-server-for-gradle), will significantly improve the development experience for many Android developers using Text Editors/IDEs which utilize the [Build Server Protocol (BSP)](https://build-server-protocol.github.io).

## Status
Passed mid-term evaluation with successful completion of composite build support, Java Home handling under review and android support in progress.

## Goal

1. Add support for composite builds. ([vscode-gradle issue #1435](https://github.com/microsoft/vscode-gradle/issues/1435))
2. Java Home detection and sending notification on incompatibility. ([issue #75](https://github.com/microsoft/build-server-for-gradle/issues/75) & [issue #76](https://github.com/microsoft/build-server-for-gradle/issues/76))
3. Add Android support with correct classpath resolution and test execution.

## Team

### Contributor

- [@Tanish-Ranjan](https://github.com/Tanish-Ranjan)

### Mentors

- [@donat](https://github.com/donat)
- [@hegyibalint](https://github.com/hegyibalint)
- [@jdneo](https://github.com/jdneo)
- [@reinsch82](https://github.com/reinsch82)
- [@oleg-nenashev](https://github.com/oleg-nenashev) as community advisor

## Rationale

As the popularity of Android development grows, the need for efficient build automation tools like the Gradle Build Server becomes increasingly important. However, current limitations in identifying and managing common Gradle functionalities used in Android projects within the server can hinder developer workflows. This project aims to bridge this gap by introducing functionalities specifically tailored to Android development.

## Deliverables

### Composite-Build Support ([vscode-gradle issue #1435](https://github.com/microsoft/vscode-gradle/issues/1435))

**Status:** Complete (Merged)

**Pull Requests:** [#154](https://github.com/microsoft/build-server-for-gradle/pull/154), [#160](https://github.com/microsoft/build-server-for-gradle/pull/160)

**Objectives:**

- Add support for building projects with [composite builds](https://docs.gradle.org/current/userguide/composite_builds.html).

**Implemented Features:**

- Took over some work already done by [@Arthurm1](https://github.com/Arthurm1) in [PR#122](https://github.com/microsoft/build-server-for-gradle/pull/122), into [PR#154](https://github.com/microsoft/build-server-for-gradle/pull/154).
- Utilized build actions to retrieve source sets from composite build projects which allowed for dependency susbtitution.
- Fix the language extension downcast issue in [PR#160](https://github.com/microsoft/build-server-for-gradle/pull/160) which was breaking composite builds.

### Improved Gradle Java Home Handling ([issue #75](https://github.com/microsoft/build-server-for-gradle/issues/75) and [issue #76](https://github.com/microsoft/build-server-for-gradle/issues/76))

**Status:** Ongoing (Under Review)

**Pull Request:** [#165](https://github.com/microsoft/build-server-for-gradle/pull/165)

**Objectives:**

- Build the project with default configurations, if Java Home is incompatible try and find a suitable Java Home.
- If incompatible Java Home is detected notify client of the incompatibility. 

**Implemented Features:**

- Probe build the project to find if default java home configuration is compatible.
- In case of incompatibility try to find a compatible java home in the given order:
    1. GradleJavaHome (Gradle Properties)
    2. UserJavaHome (Retrieved from preferences)
- Notify client if project's default java home was incompatible and we switched to a different JavaHome for compatibility.
- Notify client if the fallback logic couldn't find a compatible java home.

### Android Support

**Status:** Ongoing (Under Development)

**Pull Request:** [#173](https://github.com/microsoft/build-server-for-gradle/pull/173)

**Objectives:**

- Correct classpath resolution.
- Test execution.

## Documentation:

- Detailed developer documentation for the implemented functionalities (composite builds, Java Home detection and sending notification on incompatibility, android support).
- Documentation covering usage instructions and troubleshooting steps for the added functionalities.
- Using clear examples and diagrams to enhance understanding.

## Unit and Integration Testing:

- Implement unit tests to ensure the accuracy and reliability of the implemented functionalities.
- Unit tests thoroughly cover specific components like composite builds logic, language extension downcasting, Gradle Java Home handling logic, and build target generation logic for android projects.
- Implement integration tests to verify seamless functionality within the Gradle Build Server environment.
- Integration tests simulate real-world build scenarios and interactions between different server components.

## Demos

### Mid-Term progress

<div class="youtube-video">
  <div>
    <iframe src="https://www.youtube.com/embed/UN0AFCLASZA?si=9aG5tDzj6nL1_IKT&amp;start=371" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
</div>

## Collaboration and Learning

Throughout the program I have collaborated with all of my mentors and gained invaluable insights into open source development - best practices, project management and contributions. They also helped me learn how to explore large project repositories for research.

My work on this project, significantly expanded my skill set, encompassing JSON-RPC, Language Server Protocol, Build Server Protocol, Gradle API, Gradle Tooling API, testing methodologies and merging techniques with git. I successfully applied these learnings to produce the mentioned outcomes.

## Links

- [Project page on the GSoC site](https://summerofcode.withgoogle.com/programs/2024/projects/Guphkt1v)
- [Contributor Proposal](https://summerofcode.withgoogle.com/media/user/26d3ca3d8061/proposal/gAAAAABmsQWz_dGzhC0daKp4GFsORe9U10ZgqSOGgQGSaw30QKtvHfJLzNJaCwX1V636VneDqtGGEHM-hvYcOU0V5sOwwvvE6p7wXyrj7fX7bSUkIH-DRKI=.pdf)
- [Mid-Term Project Demo](https://youtu.be/UN0AFCLASZA?si=9aG5tDzj6nL1_IKT&t=371)