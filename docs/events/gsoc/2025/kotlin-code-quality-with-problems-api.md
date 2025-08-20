# GSoC 2025 - Enhanced Kotlin Code Quality Reporting with Gradle Problems API: Integration with Detekt and Ktlint

This project aims to implement a unified and actionable code quality reporting system through the integration of the recently introduced Gradle new [Problems API](https://docs.gradle.org/current/userguide/reporting_problems.html). This API provides structured and rich information about the problems happening during a build. The information provided can be used by different interfaces such as Gradle’s console output, build scans, or IDEs to communicate any issues. With this API integration and structured format of the generated report, developers can experience faster issue identification, streamline debugging, and have improved code maintainability. This project will provide value to the Kotlin development community by upgrading the quality of their error reporting. The integration of the Problems API will done in the plugins: Detekt and Ktlint.

![Kotlin Code](https://github.com/user-attachments/assets/84218a9c-2279-448a-a47a-245978487684)


<p align="center">
<img width="200" alt="gradle" src="https://github.com/user-attachments/assets/960fa6c4-f934-46c1-9569-341394b80ac1" />
</p>


## Team
Contributor
- [Vanessa Johnson](https://github.com/vanessamj99)

Mentors
- [Oleg Nenashev](https://github.com/oleg-nenashev)
- [Donát Csikós](https://github.com/donat)
- [Reinhold Degenfellner](https://github.com/reinsch82)

## Organization
- Kotlin Foundation

## Technologies
- Gradle
- Kotlin
- Problems API

## Rationale
Gradle recently introduced a new Problems API that allows Gradle and third-party plugins to propagate issues and warnings in a unified way. This API provides clean and actionable error reporting and more insights into the console output, dedicated HTML reports, and connected observability tools. We also want the code quality plugins for Kotlin to adopt this API. It would significantly improve the developer experience for 100,000+ Kotlin developers using Gradle. This integration will happen in detekt and ktlint which are 2 popular developer tools.

## Achievements
### Detekt
The problems api integration and testing is currently in a PR in Detekt where it has its own separate module where there is a file that feeds the problems api reporter with the detekt issues that may arise in a project. This PR can be found here [here](https://github.com/detekt/detekt/pull/8275)

### Ktlint
The problems api integration and testing is currently in a PR in Ktlint where a separate file was made to feed the problems api reporter with the ktlint errors that may arise in a project. This PR can be found here [here](https://github.com/JLLeitschuh/ktlint-gradle/pull/927)

## References

- [Project page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/4UqgKDMe)
