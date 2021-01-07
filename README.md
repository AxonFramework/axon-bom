# Axon Bill of Material

This project provides Maven managed dependencies for all Axon artifacts.

## How to use it in Maven

Import the BOM in your project:

```xml
...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>io.axoniq</groupId>
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
    mavenBom 'io.axoniq:axon-bom:<VERSION>'
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