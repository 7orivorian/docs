# Importing

=== "Maven"

    Include JitPack in your maven build file.
    
    ```xml
    
    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>
    ```

    Add the dependency.
    
    ```xml
    
    <dependency>
        <groupId>com.github.7orivorian</groupId>
        <artifactId>Wraith</artifactId>
        <version>4.0.0</version>
    </dependency>
    ```

=== "Gradle"

    Add JitPack to your root `build.gradle` at the end of repositories.

    ```groovy
    repositories {
        //...
        maven {
            url 'https://jitpack.io'
        }
    }
    ```
    
    Add the dependency.
    
    ```groovy
    dependencies {
        implementation 'com.github.7orivorian:Wraith:4.0.0'
    }
    ```

=== "Gradle (Kotlin)"

    Add JitPack to your root `build.gradle.kts` at the end of repositories.
    
    ```groovy
    repositories {
        //...
        maven {
            url = uri("https://jitpack.io")
        }
    }
    ```
    
    Add the dependency.
    
    ```groovy
    dependencies {
        implementation("com.github.7orivorian:Wraith:4.0.0")
    }
    ```

=== "Jar"

    Wraith and its sources can be downloaded from 
    [GitHub](https://github.com/7orivorian/Wraith/releases/latest).
    ![Image title](../assets/wraith/download.png)
