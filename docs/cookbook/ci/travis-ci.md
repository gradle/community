# Executing Gradle builds on Travis CI

!!! tip
    Top engineering teams using Travis CI have been able to reduce CI build time by up to 90% by using the Gradle Build Cache. [Register here](https://gradle.org/training/#build-cache-deep-dive) for our Build Cache training session to learn how your team can achieve similar results.

Building Gradle projects doesn't stop with the developer's machine. [Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) has been a long-established practice for running a build for every single change committed to version control to tighten the feedback loop.

In this guide, we'll discuss how to configure [Travis CI](https://travis-ci.org/) for a typical Gradle project.

## What you'll need

* A text editor
* A command prompt
* The Java Development Kit (JDK), version 1.8 or higher

## Setup a typical project

As example, this guide is going to focus on a Java-based project. More specifically, a Gradle plugin written in Java and tested with [Spek](https://www.spekframework.org/). First, we'll get the project set up on your local machine before covering the same steps on CI.

Just follow these steps:

### Clone the [Gradle Site Plugin](https://github.com/gradle/gradle-site-plugin) repository

```shell
$ git clone https://github.com/gradle/gradle-site-plugin.git
Cloning into 'gradle-site-plugin'...
$ cd gradle-site-plugin
```

### Build the project

As a developer of a Java project, you'll typically want to compile the source code, run the tests and assemble the JAR artifact. That's no different for Gradle plugins. The following command achieves exactly that:

```shell
$ ./gradlew build

BUILD SUCCESSFUL
14 actionable tasks: 14 executed
```

The project provides the [Gradle Wrapper](gradle_wrapper.adoc#gradle_wrapper_reference) as part of the repository. It is a recommended practice for any Gradle project as it enables your project to be built on CI without having to install the Gradle runtime.

### Build scan integration

The sample project is equipped with support for generating [build scans](https://scans.gradle.com/). Running the build with the command line option `--scan` renders a link in the console.

```shell
$ ./gradlew build --scan
Publishing build scan...
https://gradle.com/s/7mtynxxmesdio
```

The following section will describe how to build the project with the help of Travis CI.

## Configure Travis CI

Travis CI is a free, cloud-based CI solution provider making it an excellent choice for open source projects. You can build any project as long as it is hosted on GitHub as a public repository. Travis CI does not provide built-in options to post-process produced artifacts of the build (e.g., host the JAR file or the HTML test reports). You will have to use external services (like S3) to [transfer the files](https://docs.travis-ci.com/user/uploading-artifacts/).

### Create the configuration file

Travis CI requires you to check in a [configuration file](https://docs.travis-ci.com/user/customizing-the-build/) with your source code named `.travis.yml`. This file contains all relevant instructions for building the project.

The following configuration file tells Travis CI to build a Java project with JDK 8, skip the usual [default execution step](https://docs.travis-ci.com/user/customizing-the-build/#Skipping-the-Installation-Step), and run the Gradle build with the Wrapper.

```yaml
language: java
install: skip

os: linux
dist: trusty
jdk: oraclejdk8

script:
  - ./gradlew build --scan -s
```

Select the project from the Travis CI profile. After activating the repository from the dashboard, the project is ready to be built with every single commit.

![Enabling a project](images/travis-enable-project.png)

**NOTE:** Configuring [build scans](https://scans.gradle.com/) is especially helpful on cloud CI systems like Travis CI because it has additional environment and test results information that are difficult to obtain otherwise.

### Enable caching of downloaded artifacts

Gradle's dependency management mechanism resolves declared modules and their corresponding artifacts from a binary repository. Once downloaded, the files will be re-used from the cache. You need to tell Travis CI explicitly that you want to [store and use the Gradle cache and Wrapper](https://docs.travis-ci.com/user/languages/java/#Caching) for successive invocations of the build.

```yaml
before_cache:
  - rm -f $HOME/.gradle/caches/modules-2/modules-2.lock
  - rm -fr $HOME/.gradle/caches/*/plugin-resolution/

cache:
  directories:
    - $HOME/.gradle/caches/
    - $HOME/.gradle/wrapper/
```

### Further reading

You can learn more about advanced Travis CI usage through these resources:

* [Encrypting sensitive data](https://docs.travis-ci.com/user/encryption-keys/)
* [Modelling a pipeline with build stages](https://docs.travis-ci.com/user/build-stages/)

## Summary

Executing Gradle builds on CI can be set up and configured with just a handful of steps. The benefit of receiving fast feedback clearly speaks for itself. If you are not using Travis CI, no problem, many CI products tightly integrate with Gradle as a first-class citizen.