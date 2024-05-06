
# GSoC 2024. Gradle Build Server - DevX and Language Support in Buildship

- **Project GitLab** - https://gitlab.eclipse.org/eclipsefdn/emo-team/gsoc-at-the-ef/-/issues/5
- **Proposal** - https://docs.google.com/document/d/1ptbZvt8_dW0bgUAZfh7m-Oo3RtC4XTiY9frIrf2_OBQ/edit?usp=sharing 

With the introduction of Build Server for Gradle in VS Code as a combined initiative between Microsoft & Gradle in 2023 which focused mainly on providing correct classpath for Java Projects, the following issues were addressed : 

* Compiled files are output to the ‘bin’ directory, which differs from Gradle project’s default output location.
* Support for code generation, such as Annotation Processing, is suboptimal.

However, there’s a lot of potential in extending this build server. This project aims to extend this implementation to provide comprehensive support for Gradle features using the Build Server approach. The additional IDE agnostic build server capabilities proposed in this project will provide the following support :

* Describe the Gradle Build structure, allowing easy integration to project imports
* Execute tasks with cancellation support
* Execute tests
* Support additional languages

We will also implement the new fully-powered Gradle BSP for Eclipse Buildship


## Authors

- [@Sidhaarthsr](https://github.com/Sidhaarthsr)

## Mentors

- [@oleg-nenashev](https://github.com/oleg-nenashev)
- [@donat](https://github.com/donat)
- [@reinsch82](https://github.com/reinsch82)
- [@hegyibalint](https://github.com/hegyibalint)
- [@jdneo](https://github.com/jdneo)

## Repositories

- [@build-server-for-gradle](https://github.com/microsoft/build-server-for-gradle)
- [@Eclipse_Buildship](https://github.com/eclipse/buildship)


## Architecture - BSP Gradle

![Architecture Image](https://raw.githubusercontent.com/Sidhaarthsr/gradle-bsp-resources/main/img/BSP_Gradle_Architecture.jpg)

**NOTE :** The items in blue indicate the newer components indicate the component built as part of this initiative.
