# Selenium Basics
Learn Selenium for Automated Testing.

## Steps
While Selenium supports a wide range of programing languages, Java would be used in this tutorial.

### Install Java
Since Java is the programming language of choice it this tutorial, it is required to have Java installed. You can check for an existing Java installation using:
```
java --version
```

If you don't already have Java installed, you can find steps to install Oracle's free, open-source JDK [here](https://openjdk.java.net/install/).

### Install Maven
Apache Maven is used to manage the project build in this tutorial. You can check fro an existing installation using:
```
mvn --version
```

A quick guide on how to install and use Maven can be found [here](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html).

### Create a Maven Project
To create a new Maven project, run:
```
mvn archetype:generate -D groupId=org.codecreek.dev -D artifactId=selenium_learn \
-D archetypeArtifactId=maven-archetype-quickstart \ 
-D achetypeVersion=1.4 -D interactiveMode=False
```

This gives a [standard project structure](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html) under the directory *./selenium_learn*.


### Maven POM
The Project Object Model (POM) {*pom.xml*} is the core of a project's configuration in Maven. Here, we want to add a dependency for Selenium as specified in the [official documentation](https://www.selenium.dev/documentation/en/selenium_installation/installing_selenium_libraries/) as a child of the *<dependencies />* element:
```xml
<dependency>
  <groupId>org.seleniumhq.selenium</groupId>
  <artifactId>selenium-java</artifactId>
  <version>3.141.59</version>
</dependency>
```

To use Java 9 or later, we need some more modification of *pom.xml*. To use version 3.8.1 and target Java 11, we add the following as children of the *<project />* element:
```xml
<properties>
    <maven.compiler.release>11</maven.compiler.release>
</properties>

<build>
    <pluginManagement>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
            </plugin>
        </plugins>
    </pluginManagement>
</build>
```

### Building the Project
To build the project, we run:
```
mvn package
```
To run the project while injecting dependencies, we run:
```
mvn exec:java -D exec.mainClass=org.codecreek.dev.App
```

Now we have a *selenium_learn-1.0-SNAPSHOT.jar* in the */target* directory. To run the *org.codecreek.dev.App* class within this .jar artifact, we run:
```
java -cp ./target/selenium_learn-1.0-SNAPSHOT.jar org.codecreek.dev.App
``` 

### WebDriver Setup
Selenium supports all major web browsers through WebDriver. 
For details on how to setup WebDriver for different web browsers, [click here](https://www.selenium.dev/documentation/en/webdriver/driver_requirements/).


