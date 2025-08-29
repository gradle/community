---
Title: "Improving Configuration Cache in Key Gradle Plugins"
Description: "A project by Nouran Atef for GSoC 2025 focused on optimizing Gradle's build performance through enhanced Configuration Cache support in core plugins."
---

# GSoC 2025 - Improving Configuration Cache in Key Gradle Plugins

This project aims to improve Gradle’s build performance by enhancing **Configuration Cache** support in widely-used plugins.

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

* Rodrigo @ Gradle
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
Operate on Data Snapshots: The primary fix was to create simple, serializable data containers (ProjectInfo and ProjectTree). These classes act as a "snapshot" of the necessary data, which is safely extracted from the Project object at the end of configuration phase using Gradle's lazy Provider API. Services like LintService were refactored to be stateless, receiving these data snapshots as input instead of the Project object itself.
Defer Access with a Supplier: For rare cases where a rule absolutely required the live Project model at execution time, the fix was to inject a Supplier<Project>. This lightweight, serializable object provides a "recipe" to get the Project object on-demand, isolating the non-cache-friendly logic and allowing the rest of the process to be cached.
This strategy was applied consistently across all classes. The future work plan is to continue this pattern by creating new data projections for Project.configurations and refactoring the remaining rules incrementally.

* **Technical Write-up:** A detailed blog post explaining the refactoring process for this plugin was published here: [Supporting Configuration Cache - my learnings from the Nebula Lint Plugin](https://dev.to/gradle-community/unlocking-configuration-cache-with-gsoc-contributor-374l).

* **Pull Request:** [#433](https://github.com/nebula-plugins/gradle-lint-plugin/pull/433)
* **Status:**  **⏳ Open**


  ---

### 2. Gradle Play Framework Plugin (`play-framework-plugin`)

* **Problem:** The plugin had multiple Configuration Cache violations. The `PlayDistributionPlugin` resolved dependencies eagerly and held direct references to the non-serializable `Configuration` object. Separately, the `JavaScriptMinify` task violated caching rules by calling `getProject()` during its execution phase to access file operations.

* **Approach to Fix:** A two-part approach was used to address the different issues:
    1.  **For `PlayDistributionPlugin`:** The fix was to create a lazy data pipeline using Gradle's `Provider` API. A new serializable data container, `ComponentIdAndFile`, was introduced to safely hold artifact information. This allowed the plugin to pass dependency information without resolving the `Configuration` object during the configuration phase.
    2.  **For `JavaScriptMinify` Task:** The solution was to use dependency injection. The required `FileSystemOperations` service was injected directly into the task's constructor, eliminating the need to call `getProject()` at execution time.

* **Pull Request:** [#207](https://github.com/gradle/playframework/pull/207)
* **Status:**  **⏳ Open**
* **Note:** This pull request is not merged as Gradle team has decided to decommission this plugin in favor of a newer, official plugin within the Play Framework that is already Configuration Cache-compatible.
  
---

### 3. Liquibase Gradle Plugin (`liquibase-gradle-plugin`)

* **Problem**: The plugin was incompatible with the Configuration Cache because its main task, `LiquibaseTask`, and a helper class, `ArgumentBuilder`, directly accessed the non-serializable `Project` object during the execution phase. This was done to read extension properties, resolve classpaths, and get project directories and loggers.

* **Approach to Fix**: The solution was to make the task's execution logic stateless by extracting all necessary data the end of the configuration phase into **serializable Data Transfer Objects (DTOs)**.
    * Two new data container classes, `LiquibaseInfo` and `ProjectInfo`, were created to hold all the required data from the project and its `liquibase` extension.
    * These DTOs are populated safely at configuration time and passed into the `LiquibaseTask` as lazy `@Internal` properties.
    * The `ArgumentBuilder` class was refactored to be stateless, receiving the `LiquibaseInfo` DTO as a method parameter instead of holding a reference to the `Project`.

* **Pull Request**: [#176](https://github.com/liquibase/liquibase-gradle-plugin/pull/176)
*  **Gradle Cookbook Entry**: Based on this work, a guide was created for the Gradle Cookbook: [Example - Configuration Cache compatibility for the Liquibase plugin](https://cookbook.gradle.org/plugin-development/configuration-cache/example-config-cache-liquibase-plugin/).
* **Status**: ⏳ **Open** (In communication with the maintainer and answering their questions)

---

### 4. Compose Multiplatform Localize (`compose-multiplatform-localize`)

* **Problem**: The plugin's main task contained multiple Configuration Cache violations by accessing the `Project` object during the execution phase. Specifically, it used `project.projectDir` to resolve file paths and `project.logger` for logging messages.

* **Approach to Fix**: A two-part fix was implemented to decouple the task from the `Project` model:
    1.  The `project.projectDir` access was resolved by adding a new lazy **`@Internal`** property to the task. This property is populated safely during the configuration phase and then read by the task at execution time.
    2.  The `project.logger` calls were replaced by using the task's own **built-in logger** (`getLogger()`), which is the cache-compatible way to handle logging within a task.

* **Pull Requests**: [#12](https://github.com/hyperether/compose-multiplatform-localize/pull/12), [#13](https://github.com/hyperether/compose-multiplatform-localize/pull/13)
* **Status**: ✅ **Merged**

---

### 5. jsonschema2dataclass Gradle Plugin (`js2d-gradle`)

* **Problem**: The Android portion of the plugin was incompatible with the Configuration Cache. The `ProcessorVersionGeneratorTask` accessed `project.versionCatalogs` at execution time, causing serialization failures.
* **Approach to Fix**: The solution involved fully decoupling the task's execution. A new `@Internal` `Property` was added to the task to hold the resolved dependency identifier. A lazy `Provider.map()` chain was then used to resolve the identifier at configuration time and wire it to the new task property.
* **Pull Request**: [#1072](https://github.com/jsonschema2dataclass/js2d-gradle/pull/1072)
* **Status**: ✅ **Merged**

  ---


### 6. OpenRewrite Gradle Plugin (`rewrite-gradle-plugin`)

* **Problem**: The plugin was fundamentally incompatible with the Configuration Cache. Its core classes—`RewriteExtension`, `AbstractRewriteTask`, and the parsers—were deeply coupled with the live `Project` model, directly accessing project state and holding non-serializable `Project` references.
* **Approach to Fix**: The refactoring is a significant, work-in-progress architectural change focused on completely decoupling the plugin from the `Project` model. The strategy involved several key steps:
    1.  The `RewriteExtension` was made **serializable** by extracting and storing only the necessary primitive data (like the project directory and properties) during its construction.
    2.  A comprehensive, serializable **Data Transfer Object (DTO)**, `ProjectInfo`, was created to act as a safe snapshot of all necessary project data.
    3.  The `AbstractRewriteTask` base class was refactored to consume this `ProjectInfo` DTO as its primary input.
    4.  The `DelegatingProjectParser` was updated to be instantiated with the `ProjectInfo` DTO, using **reflection** to transfer the DTO's data across an isolated classloader boundary.
* **Validation**: A dedicated functional test (`ConfigurationCacheTest`) was added to prove the fix. This test runs a build twice with the configuration cache enabled, verifying that no compatibility problems are found and that the cache is successfully reused on the second run.
* **Pull Request**: Draft PR [#1](https://github.com/Nouran-11/rewrite-gradle-plugin/pull/1) 
* **Status**: 🚧 **Work in Progress**. This is a large and complex refactoring effort. The foundational work of introducing a DTO and decoupling the core components is underway, but more work is needed for full compatibility.
  
 --- 

## Surveyed Plugins 

This section details additional plugins that were investigated for Configuration Cache compatibility, but for which a contribution was not submitted.

### 7. Flyway Gradle Plugin (`flyway-gradle-plugin`)

* **Problem:** The plugin's abstract base task, `AbstractFlywayTask`, is fundamentally incompatible with the Configuration Cache. Its `@TaskAction` logic directly queries the live `Project` model at execution time to access the buildscript classloader, project extensions, and source set outputs. This problematic logic can be seen in the `runTask` and `addClassesAndResourcesDirs` methods in the [source code](https://github.com/flyway/flyway/blob/9df387cfa998ad5e1024151374f226a6185fa78f/flyway-plugins/flyway-gradle-plugin/src/main/java/org/flywaydb/gradle/task/AbstractFlywayTask.java#L591).
* **Proposed Approach to Fix:** The general approach would involve refactoring the Flyway tasks to be stateless. This would require capturing all necessary configuration (like source set outputs and dependent classpaths) at configuration time into serializable data objects (DTOs) and passing them to the tasks as lazy **Providers**.
* **Reason for Not Proceeding:** A contribution was not pursued , Although the original request in [GitHub Issue #3550](https://github.com/flyway/flyway/issues/3550) has since gained significant community interest and upvotes, the maintainers have not yet acted on it or changed their stance on accepting external contributions. The ongoing discussion is also captured in [GitHub Issue #4107](https://github.com/flyway/flyway/issues/4107).

* **Status:** 🛑 **Blocked**

---


### 8. forbidden-apis Gradle Plugin

* **Problem:** When the Configuration Cache is enabled, properties configured via the top-level `forbiddenApis` extension are not correctly applied to the tasks. This causes the task properties to be cached with empty values, leading to an error at execution time because required inputs are missing.
* **Proposed Approach to Fix:** The fix would require refactoring the plugin to use Gradle's modern lazy `Property` APIs. The properties in the `forbiddenApis` extension should be correctly wired to the corresponding properties on the `CheckForbiddenApis` task so that their values are resolved before the task state is cached.
* **Reason for Not Proceeding:** A contribution was not pursued because the plugin maintainer has clearly stated that the plugin is **no longer actively maintained** and that adding Configuration Cache support is not a priority.
* **GitHub Issue:** [#269](https://github.com/policeman-tools/forbidden-apis/issues/269)
* **Status:** 🛑 **Blocked**

## Demos

### Midterm Demo

This video demonstrates the progress made during the first half of the project, showcasing the initial fixes and the overall approach to making community plugins compatible with Gradle's Configuration Cache.

[![Midterm Demo Video](https://img.youtube.com/vi/nhuRXXAnick/hqdefault.jpg)](https://www.youtube.com/watch?v=nhuRXXAnick)

## Collaboration and Learning

This project was a comprehensive endeavor in improving the Gradle ecosystem. The work involved a mix of **surveying** popular community plugins to identify Configuration Cache incompatibilities, **developing technical fixes** to address them, and **collaborating with plugin maintainers** to have those contributions reviewed and merged. This process highlighted the importance of clear communication, persistence, and technical expertise in open-source development.

The effort to make the Gradle ecosystem fully compatible with the Configuration Cache is ongoing, and there are many opportunities for others to help. The Gradle team maintains a curated list of popular plugins that still need compatibility work. For anyone interested in continuing this effort and making a valuable contribution to the Gradle community, the following GitHub issue is the best place to start:

➡️ **[List of Community Plugins with Configuration Cache Issues](https://github.com/gradle/gradle/issues/13490)**

## Post-GSoC Plans

My involvement with the Gradle community will not end with the GSoC program, as I am committed to supporting the contributions I've made and continuing to help improve the ecosystem. This includes maintaining my merged pull requests, as well as continuing the dialogue with the maintainers of the **Liquibase** plugin to help get that contribution merged. Looking ahead, I will continue to explore the community-curated list of plugins for new opportunities to contribute. The GSoC program has been an incredible learning experience, and I look forward to being an active member of the Gradle open-source community for a long time to come.


## References

* **My GitHub Profile:** [github.com/Nouran-11](https://github.com/Nouran-11)
* **Project Blog Post:** A detailed guide on making a Gradle plugin Configuration Cache compatible, based on the work done in this project: [Supporting Configuration Cache - my learnings from the Nebula Lint Plugin](https://dev.to/gradle-community/unlocking-configuration-cache-with-gsoc-contributor-374l)
*  **Gradle Cookbook Guide:** A guide based on the work done on the Liquibase plugin: [Example - Configuration Cache compatibility for the Liquibase plugin](https://cookbook.gradle.org/plugin-development/configuration-cache/example-config-cache-liquibase-plugin/).
* **Gradle's Official Documentation:** A guide on the [Configuration Cache](https://docs.gradle.org/current/userguide/configuration_cache.html), which served as the primary technical reference for this project.
* **Community Plugin Tracking Issue:** The official Gradle issue for tracking [Configuration Cache compatibility in popular community plugins](https://github.com/gradle/gradle/issues/13490).
* **GSoC Project Page:** [Improving Configuration Cache in key Gradle plugins](https://summerofcode.withgoogle.com/programs/2025/projects/chp2Sbei)

