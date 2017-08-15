# Gradle

## Dependencies
Gradle follows some special syntax to define dependencies.

To decalre dependecies in your `build.gradle` file you must do the following.

### Declare the repositories
indicate the repositories where we are trying to retrieve our library dependencies.

```
repositories {
   mavenCentral()
}
```

### Declare the library dependencies.

In our example we are listing the in a java utilities library `commons-lang3` and the testing framework `junit`

```
dependencies {
   compile group: 'org.apache.commons', name: 'commons-lang3', version: '3.6'
   testCompile group: 'junit', name: 'junit', version: '4.+'
}
```

**compile** − The dependencies required to compile the production source of the project.

**testCompile** − The dependencies required to compile the test source of the project. By default, it includes compiled production classes and the compile time dependencies.

Alternatively you can delcare dependencies as follows `compile '<GROUP>:<NAME>:<VERSION>'`

```
dependencies {
   compile 'org.apache.commons:commons-lang3:3.6'
   testCompile 'junit:junit:4.+'
}
```

## Where are the dependencies?

gradle will cache the artifacts such as library dependencies to increase performance when performing builds. 

the artifacts are downloaded in `$HOME/.gradle`.

## View dependencies

To view dependencies you can run `./gradlew dependencies` to view the dependency graph.

