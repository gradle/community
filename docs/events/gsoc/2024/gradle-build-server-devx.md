
# GSoC 2024. Gradle Build Server - DevX and Language Support in Buildship

## Goal/Objective
- Implement a fully powered version of Gradle BSP for Eclipse Buildship to support DevX & Language Support in Buildship.
- We will add more functionalities to the existing BSP Implementation for providing the required support in Eclipse Buildship.

## Status
Selected

## Team
#### Authors
- [@Sidhaarthsr](https://github.com/Sidhaarthsr)

#### Mentors
- [@oleg-nenashev](https://github.com/oleg-nenashev)
- [@donat](https://github.com/donat)
- [@reinsch82](https://github.com/reinsch82)
- [@hegyibalint](https://github.com/hegyibalint)
- [@jdneo](https://github.com/jdneo)

## Rationale
The Eclipse buildship currently orchestrates the Gradle Build Tasks directly without using the BSP Interface. The Build Server Protocol promises excellent, pluggable, IDE agnostic tooling for build systems. Recently, a new Build Server for Gradle (Gradle BSP) has been published. Its current functionality, however, is focused only on the Visual Studio Code integration to provide correct classpath for Java projects and optimal support for Code Generation, such as Annotation Processing. However, There’s a lot of potential in extending this build server. 

**A more complete implementation should be able to**:
- Describe the Gradle build structure, allowing easy integration to project import
- Execute tasks with cancellation support
- Execute tests
- Support additional languages

## Implementation

**Eclipse Buildship** - In the updated implementation, the Eclipse Buildship plugin will use the fully-powered BSP Gradle interface to orchestrate all the Gradle Build tasks. In order to leverage Gradle BSP interface, the Eclipse Buildship plugin will use the requests defined in the BSP interface to orchestrate build tasks in Gradle and will process notifications returned by the Build Server for those BSP requests accordingly.

**Extending Gradle Build Server Capabilities** - We will extend the capabilities of the Gradle BSP Server by implementing the requests that are unsupported in the current BSP Implementation for VS Code.

## Deliverables

The Eclipse Buildship plugin with updated code that uses the requests implemented in the BSP Interface to orchestrate the Build Tasks in Gradle projects. We'll reuse the existing BSP requests and implement the newer BSP requests in microsoft's build-server-for-gradle repository.

**The following BSP requests implemented in microsoft's build-server-for-gradle repository:** 
- buildTarget/run
- buildTarget/test
- buildTarget/inverseSources
- debugSession/start

The Eclipse buildship client will be equipped with capabilities to process all possible BSP notifications returned by the Build Server to facilitate support for the targeted requirements.

## Links
- [Contributor Proposal](https://docs.google.com/document/d/1ptbZvt8_dW0bgUAZfh7m-Oo3RtC4XTiY9frIrf2_OBQ/edit?usp=sharing)
- [Project Proposal](https://gitlab.eclipse.org/eclipsefdn/emo-team/gsoc-at-the-ef/-/issues/5)
- [Eclipse Buildship](Placeholder)
- [Gradle BSP Enhancements](Placeholder)
