---
title: "Gradle in Google Summer of Code 2023"
description: >
  Gradle participated in GSoC 2023 under the umbrella of
  the Kotlin Foundation.
---

# Gradle in Google Summer of Code 2023

In the summer of 2023, The [Kotlin Foundation](https://kotlinfoundation.org/) sponsored four projects for the Google Summer of Code 2023.
The Gradle Kotlin Script Support for Eclipse and BuildShip project by [Nikolai Vladimirov](https://www.linkedin.com/in/vladimir0v/) was one of them!
Gradle, a Kotlin Foundation member, and [Donát Csikós](https://github.com/donat) provided mentoring support for this project.

The project's initial goal was to improve user interaction with Gradle Kotlin scripts inside the Eclipse IDE.
The project aimed to implement several key functionalities, including syntax highlighting for Kotlin scripts, content assistance, go-to-definition, accurate diagnostics for syntax errors, signature help, and hovering.
Nikolai successfully delivered these features by implementing support for Kotlin scripts based on the existing [kotlin-language-server](https://github.com/fwcd/kotlin-language-server) project,
creating a new system to separate compilation environments for each build script.
[Read more](https://kotlinfoundation.org/news/gsoc-2023-eclipse-gradle-kotlin/) about this project by Nikolai and the team.

![Syntax highlighting for .kts scripts in Eclipse IDE](./buildship-syntax-demo.png "Syntax highlighting for .kts scripts in Eclipse IDE")
