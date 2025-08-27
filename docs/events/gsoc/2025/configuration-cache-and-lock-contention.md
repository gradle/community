---
Title: "Improving Configuration Cache in Key Gradle Plugins"
Description: "A project by Nouran Atef for GSoC 2025 focused on optimizing Gradle's build performance through enhanced Configuration Cache support in core plugins."
---

# GSoC 2025 - Improving Configuration Cache in Key Gradle Plugins

This project aims to improve Gradle’s build performance by enhancing **Configuration Cache** support in widely-used plugins.The project will help analyze cache behavior and identify areas where multiple processes compete for shared resources, which can slow down builds.

The long-term goal is to improve developer productivity and CI reliability by making Gradle builds faster, more predictable, and easier to optimize—especially in large-scale projects.

<p align="center">
  <img src="https://github.com/Nouran-11/gradle-gsoc.png/blob/main/Gradle-GSOC.png?raw=true" alt="Gradle and GSoC logos" width="600">
</p>

## Project Status

* **Status:** Completed
* **Milestone:** Midterm Evaluation Successfully Passed , waiting for the Final Evaluation
* **Current Focus:** The project is now complete. The final phase involved extending Configuration Cache support to a wider range of community plugins, successfully scaling the architecture and insights gained from the initial work. Furthermore, the process provided invaluable learnings and contributed to a substantial increase in technical expertise.

## Team

### Contributor

* [Nouran Atef](https://www.linkedin.com/in/nouran-atef11/)

### Mentors

* Rodrigo Oliveira
* Rafael Chaves
* Oleg Nenashev


## Organization

* Kotlin Foundation


## Project Goals

* **Survey & Identify:** To survey a list of popular Gradle community plugins and identify common patterns of Configuration Cache incompatibility.
* **Fix & Contribute:** To develop and submit patches for the identified incompatibilities, collaborating with plugin maintainers to get them merged.
* **Document & Share:** To document the process and share key learnings with the wider Gradle community to facilitate future compatibility work.


## Final Project Deliverables
This section lists all the deliverables that were successfully completed for the project.

 ### 1. Nebula Gradle Lint Plugin (`gradle-lint-plugin`)

* **Problem:** The plugin's primary violation of Configuration Cache principles was its direct reference to the Project object and its use of project.configurations to resolve dependencies at configuration time. The direct Project reference has been successfully removed. However, refactoring the usage of project.configurations is still outstanding, as this part of the work requires a more significant redesign of the plugin's logic.
* **Approach to Fix:** The core approach was to decouple tasks and services from Gradle's live, non-serializable Project object during the task's execution phase. This was achieved through a consistent, two-pattern strategy:
Operate on Data Snapshots: The primary fix was to create simple, serializable data containers (ProjectInfo and ProjectTree). These classes act as a "snapshot" of the necessary data, which is safely extracted from the Project object during the configuration phase using Gradle's lazy Provider API. Services like LintService were refactored to be stateless, receiving these data snapshots as input instead of the Project object itself.
Defer Access with a Supplier: For rare cases where a rule absolutely required the live Project model at execution time, the fix was to inject a Supplier<Project>. This lightweight, serializable object provides a "recipe" to get the Project object on-demand, isolating the non-cache-friendly logic and allowing the rest of the process to be cached.
This strategy was applied consistently across all classes. The future work plan is to continue this pattern by creating new data projections for Project.configurations and refactoring the remaining rules incrementally.
* **Pull Request:** [#433](https://github.com/nebula-plugins/gradle-lint-plugin/pull/433)
* **Status:**  **Not Merged**


  ---

### 2. Gradle Play Framework Plugin (`play-framework-plugin`)

* **Problem:** The plugin had multiple Configuration Cache violations. The `PlayDistributionPlugin` resolved dependencies eagerly and held direct references to the non-serializable `Configuration` object. Separately, the `JavaScriptMinify` task violated caching rules by calling `getProject()` during its execution phase to access file operations.

* **Approach to Fix:** A two-part approach was used to address the different issues:
    1.  **For `PlayDistributionPlugin`:** The fix was to create a lazy data pipeline using Gradle's `Provider` API. A new serializable data container, `ComponentIdAndFile`, was introduced to safely hold artifact information. This allowed the plugin to pass dependency information without resolving the `Configuration` object during the configuration phase.
    2.  **For `JavaScriptMinify` Task:** The solution was to use dependency injection. The required `FileSystemOperations` service was injected directly into the task's constructor, eliminating the need to call `getProject()` at execution time.

* **Pull Request:** [#207](https://github.com/gradle/playframework/pull/207)
* **Status:**  **Not Merged**
* **Note:** This pull request is not merged as Gradle team has decided to decommission this plugin in favor of a newer, official plugin within the Play Framework that is already Configuration Cache-compatible.
  
---

### 3. Liquibase Gradle Plugin (`liquibase-gradle-plugin`)

* **Problem**: The plugin was incompatible with the Configuration Cache because its main task, `LiquibaseTask`, and a helper class, `ArgumentBuilder`, directly accessed the non-serializable `Project` object during the execution phase. This was done to read extension properties, resolve classpaths, and get project directories and loggers.

* **Approach to Fix**: The solution was to make the task's execution logic stateless by extracting all necessary data during the configuration phase into **serializable Data Transfer Objects (DTOs)**.
    * Two new data container classes, `LiquibaseInfo` and `ProjectInfo`, were created to hold all the required data from the project and its `liquibase` extension.
    * These DTOs are populated safely at configuration time and passed into the `LiquibaseTask` as lazy `@Input` properties.
    * The `ArgumentBuilder` class was refactored to be stateless, receiving the `LiquibaseInfo` DTO as a method parameter instead of holding a reference to the `Project`.

* **Pull Request**: [#176](https://github.com/liquibase/liquibase-gradle-plugin/pull/176)
* **Status**: ⏳ **Open** (In communication with the maintainer and answering their questions)

---

### 4. Compose Multiplatform Localize (`compose-multiplatform-localize`)

* **Problem**: The plugin's main task contained multiple Configuration Cache violations by accessing the `Project` object during the execution phase. Specifically, it used `project.projectDir` to resolve file paths and `project.logger` for logging messages.

* **Approach to Fix**: A two-part fix was implemented to decouple the task from the `Project` model:
    1.  The `project.projectDir` access was resolved by adding a new lazy **`@Input`** property to the task. This property is populated safely during the configuration phase and then read by the task at execution time.
    2.  The `project.logger` calls were replaced by using the task's own **built-in logger** (`getLogger()`), which is the cache-compatible way to handle logging within a task.

* **Pull Requests**: [#12](https://github.com/hyperether/compose-multiplatform-localize/pull/12), [#13](https://github.com/hyperether/compose-multiplatform-localize/pull/13)
* **Status**: ✅ **Merged**

---



## Technologies

* Java
* Groovy
* Gradle
* Configuration Cache
* Build Performance
* Gradle TestKit

## References

- [Project Page on the GSoC site](https://summerofcode.withgoogle.com/programs/2025/projects/chp2Sbei)
