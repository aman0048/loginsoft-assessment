# Spring Beans Submodule Build Steps

## Steps Followed

### 1. Cloning the Spring Framework Repository
Firstly, I cloned the Spring Framework project from GitHub using the following command:

```bash
git clone https://github.com/spring-projects/spring-framework
```

This command created a local copy of the entire Spring Framework project on my machine

### 2. Navigating to the spring-framework directory
Next, I navigated to the spring-framework directory using the following command:

```bash
cd spring-framework
```

### 3. Switching to the Specified Version (v5.3.17): 
To switch to the specified version (v5.3.17), I used the following command:

```bash
git checkout v5.3.17
```
### 4. Importing the Project into IntelliJ IDEA: 
I imported the Spring Framework project into IntelliJ IDEA. The IDE automatically detected and loaded the project's dependencies, and certain resources were built during this process.

### 5. Building the Project:
I navigated to the spring-beans submodule and attempted to build the project using IntelliJ’s Gradle integration. The build was triggered through IntelliJ's built-in Gradle runner.
I could have also built the project using the following command:

```bash
gradlew.bat build
```

### 6. Build Failure:
The build failed due to the following error:

```bash
Plugin [id: 'io.spring.ge.conventions', version: '0.0.9'] was not found in any of the following sources.
```

This indicated that the Gradle plugin io.spring.ge.conventions version 0.0.9 could not be resolved. This plugin was referenced in the main settings.gradle file, and the error originated from there.

### 6. Investigating the Issue:
To investigate further, I ran the build with verbose logging enabled to capture more detailed information about the error:
    
```bash
gradlew.bat build --info --stacktrace
```
This command provided a detailed stack trace, which confirmed that the issue stemmed from the unavailability of the io.spring.ge.conventions plugin in the repositories defined in the settings.gradle file.

### 7. Checking Maven Central for Plugin Availability:
I navigated to the Maven Central repository to verify the availability of the io.spring.ge.conventions plugin version 0.0.9. Upon searching, I found that version 0.0.9 was not available, but other versions such as 0.0.7, 0.0.13, and higher were available.

Link to the Maven Central page: https://mvnrepository.com/artifact/io.spring.ge.conventions/io.spring.ge.conventions.gradle.plugin

### 8. Updating the Plugin Version: 
To resolve the issue, I updated the io.spring.ge.conventions plugin version from 0.0.9 to 0.0.13 in the settings.gradle file:

```bash
id 'io.spring.ge.conventions' version '0.0.13'
```


### 9. Rebuilding the Project:
After updating the plugin version, I re-ran the Gradle build.
This time, the build completed successfully without any errors, and the spring-beans JAR file was generated as expected.


### 
## Note:
These are the required I followed to resolve the dependency issue and successfully build the Spring Beans submodule of the Spring Framework project.
```
