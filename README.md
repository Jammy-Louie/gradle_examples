# Gradle

## What is Gradle?

Gradle is a build system That helps your projects and is commonly used with Java projects.

## Gradlew and Gradle
Gradle can be intalled on your machine and used to run the different build tasks. However you can include a self contained version of Gradle, *Gradlew* which can be used without the need to install gradle on the machine.

This guide assumes you are using *gradlew*


## build.gradle
a `build.gradle` is used for build configurations, add plugins, list library dependencies, and defining tasks.

## Useful Gradle Commands

Print out all tasks from the root project

```
./gradlew taks
```

### JAVA PROJECTS

For Java Projects you will want to include the following line in your `build.gradle` file:

```
apply plugin: 'java'
```

By adding the Java Plug-in you gain access to additional tasks to build your java project.

if you were to run `./gradlew tasks`  you will now see the following:

**assemble** - Assembles the outputs of this project.

**build** - Assembles and tests this project.

**buildDependents** - Assembles and tests this project and all projects that depend on it.

**buildNeeded** - Assembles and tests this project and all projects it depends on.

**classes** - Assembles main classes.

**clean** - Deletes the build directory.

**jar** - Assembles a jar archive containing the main classes.

**testClasses** - Assembles test classes.

**check** - Runs all checks.

**test** - Runs the unit tests.

Majority of the time we will only be concerned with the following.

```
./gradlew clean
```

```
./gradlew build
```

```
./gradlew test
```

you can even run multiple commands in the same line.
i.e. 

```
./gradlew clean build
```

you can even exclude tasks from being executed with 

```
./gradlew -x <task_name>
```

for example if you were trying to build a jar without running the tests you can execute the following:

```
./gradlew build -x test
```

## Basic Example

Include in this example is a simple java application which outputs *"Hello World!!"*. This Project uses the `build.gradle` file to build an executable jar.


### Key Points

* when using the `./gradlew clean build` command to build a clean `jar`, the `jar` file will be located under `/build/libs/<jar_name><version_number>.jar`
* To build an executable `jar` you need to do one of the following.
 * create a `MANIFEST.MF` file and point to location of the main class. In our example the contents would look like:
```
Main-Class: io.pivotal.GradleSample
```
The `MANIFEST.MF` is usually create on the following path `META-INF/MANIFEST.MF`

 * Set the location of the main class in the `build.gradle`.
```
jar {
    manifest {
        attributes 'Main-Class': 'io.pivotal.GradleSample'
    }
}
```
* you can now build an executable jar with `./gradlew clean build` and execute the `jar` with `java -jar buid/libs/<jar_name>.jar`
