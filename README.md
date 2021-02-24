# Axon Bill of Material
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.axonframework/axon-bom/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.axonframework/axon-bom)
![Build Status](https://github.com/AxonFramework/axon-bom/actions/workflows/maven.yml/badge.svg?branch=master)

This project provides Maven managed dependencies for all Axon artifacts.

## How to use it in Maven

Import the BOM in your project:

```xml
...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.axonframework</groupId>
                <artifactId>axon-bom</artifactId>
                <version>${version.axon}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>

            ...

        </dependencies>
    </dependencyManagement>
...
```

Then add the dependencies you need without specifying the version:

```xml
...
    <dependencies>
        <dependency>
            <groupId>org.axonframework</groupId>
            <artifactId>axon-configuration</artifactId>
        </dependency>
        <dependency>
            <groupId>org.axonframework</groupId>
            <artifactId>axon-server-connector</artifactId>
        </dependency>
        <dependency>
            <groupId>org.axonframework.extensions.kafka</groupId>
            <artifactId>axon-kafka</artifactId>
        </dependency>
        <dependency>
            <groupId>org.axonframework.extensions.mongo</groupId>
            <artifactId>axon-mongo</artifactId>
        </dependency>
            ...

    </dependencies>
...
```

## How to use it in Gradle

Apply the `dependency-management-plugin` plugin:

```groovy
buildscript {
  repositories {
    jcenter()
  }
  dependencies {
    classpath "io.spring.gradle:dependency-management-plugin:0.5.1.RELEASE"
  }
}

apply plugin: "io.spring.dependency-management"
```
Import the Axon BOM:

```groovy
dependencyManagement {
  imports {
    mavenBom 'org.axonframework:axon-bom:<VERSION>'
  }
}
```

Then add the dependencies you need without specifying the version:

```groovy
dependencies {
    compile 'org.axonframework:axon-configuration'
    compile 'org.axonframework:axon-server-connector'
    compile 'org.axonframework.extensions.kafka:axon-kafka'
    compile 'org.axonframework.extensions.mongo:axon-mongo'
    ...
}
```
