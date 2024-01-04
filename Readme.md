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

Gradle on its own has no knowledge of any language. 
It is through plugins that it knows what to do with different languages.

## Plugins

When you want to add a plugin, then there are two ways:
1. Recommended - the `plugin` block.
2. The old way - `apply plugin: '...'`. This can be placed anywhere, preferably at the top of the file.

To then configure the plugin, you'd add a block with the block name.

```build.gradle
plugins {
    id 'bananaPhone'
}

bananaPhone {
    ...config here
}
```

Custom plugins might have different ways of configuring them.

### Repository

The `repositories` block is used to tell Gradle where to look for dependencies and plugins.

The default repositories can be defined with a method. Ex `mavenCentral()`.

When you're defining a custom one, then you have to define it a bit differently.
```
repositories {
    customRepo {
        url 'https://banana-hpone.com/bob'
        ...otherConfig
    }
}
```

The order matters here. It tries to resolve dependencies based on the order that the repositories are defined in.

### Dependencies

The `dependencies` block is used to tell Greadle what dependencies are needed.

You can define them by different types based on what their purposes are:
* `implementation`: Dependencies required to compile your production code, but are not exposed to consumers of your library.
* `testImplementation`: Dependencies used only for compiling and running tests.
* `api`: Dependencies that are part of your API and required for both compiling the production code and for consumers of the library.
* `compileOnly`: Dependencies only needed for compiling, not at runtime.

The dependencies themselves are defined by `<groupId>:<artifactId>:<version>`.
For ex `implementation 'org.springframework.boot:spring-boot-starter-web:2.3.1.RELEASE'`

Gradle caches the dependencies in your user folder.