# Gradle tutorial

Gradle is a build automation tool.

A Gradle project is identified by the presence of a `build.gradle` file.

## Initializing a project

In order to initialize a Gradle project, you can use the `gradle init` command.

This generates several files.

* `build.gradle` - this is the primary build script and identifies a Gradle project.
* `settings.gradle` - used for multi-project build configurations.
* `gradlew`, `gradlew.bat`, `gradle directory` - allows for the Gradle wrapper usage. 
  * A wrapper allows for project specific Gradle versions.
* `.gradle folder` - contains build related data.

## Tasks

To check what tasks there are, you can use `gradle tasks`.

To run a specific task, you can do `gradle <task name>`.