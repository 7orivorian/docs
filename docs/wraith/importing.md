# Importing

## Maven

* Include JitPack in your maven build file.

```xml

<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
```

* Add Wraith as a dependency.

```xml

<dependency>
    <groupId>com.github.7orivorian</groupId>
    <artifactId>Wraith</artifactId>
    <version>3.3.0</version>
</dependency>
```

## Gradle

=== "Groovy"

    * Add JitPack to your root `build.gradle` at the end of repositories

    ```groovy
    repositories {
        //...
        maven {
            url 'https://jitpack.io'
        }
    }
    ```
    
    * Add the dependency
    
    ```groovy
    dependencies {
        implementation 'com.github.7orivorian:Wraith:3.3.0'
    }
    ```

=== "Kotlin"

    * Add JitPack to your root `build.gradle.kts` at the end of repositories
    
    ```groovy
    repositories {
        //...
        maven {
            url = uri("https://jitpack.io")
        }
    }
    ```
    
    * Add the dependency
    
    ```groovy
    dependencies {
        implementation("com.github.7orivorian:Wraith:3.3.0")
    }
    ```

## Other

Download a `.jar` file
from GitHub [releases](https://github.com/7orivorian/Wraith/releases/tag/3.3.0)