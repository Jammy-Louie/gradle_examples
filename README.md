# Gradle

## Gradle build Life cycle

gradle build life cycle has 3 phases

1. Initialization - determines which projects are part of the build (i.e sub-projects) 
1. Configuration - the projects are all configured. Will start applying such things as plug ins and getting dependencies.
1. Execution - determines which tasks need to executed and executes the selected tasks (i.e. clean, build)

Example from [Gradle Documentation] (https://docs.gradle.org/3.3/userguide/build_lifecycle.html)

settings.gradle

```
println 'This is executed during the initialization phase.'

```

build.gradle

```

println 'This is executed during the configuration phase.'

task configured {
    println 'This is also executed during the configuration phase.'
}

task test {
    doLast {
        println 'This is executed during the execution phase.'
    }
}

task testBoth {
    doFirst {
      println 'This is executed first during the execution phase.'
    }
    doLast {
      println 'This is executed last during the execution phase.'
    }
    println 'This is executed during the configuration phase as well.'
}

```

if you were to execute `./gradlew test testBoth`

you should see the following output

```
This is executed during the initialization phase.
This is executed during the configuration phase.
This is also executed during the configuration phase.
This is executed during the configuration phase as well.
:test
This is executed during the execution phase.
:testBoth
This is executed first during the execution phase.
This is executed last during the execution phase.
```
