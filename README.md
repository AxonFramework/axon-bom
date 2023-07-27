# Axon Bill of Materials
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.axonframework/axon-bom/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.axonframework/axon-bom)
![Build Status](https://github.com/AxonFramework/axon-bom/actions/workflows/maven.yml/badge.svg?branch=master)

This project provides Maven managed dependencies for all Axon artifacts.
Using `axon-bom` inside a dependency management system ensures the compatibility of Axon's dependencies.
At this stage, the BOM includes the dependencies for the following projects:

* [Axon Framework](https://github.com/AxonFramework/AxonFramework)
* [Axon Server Connector Java](https://github.com/AxonIQ/axonserver-connector-java)
* [Axon Framework AMQP Extension](https://github.com/AxonFramework/extension-amqp)
* [Axon Framework CDI Extension](https://github.com/AxonFramework/extension-cdi)
* [Axon Framework JGroups Extension](https://github.com/AxonFramework/extension-jgroups)
* [Axon Framework JobRunr Pro Extension](https://github.com/AxonFramework/extension-jobrunrpro)
* [Axon Framework Kafka Extension](https://github.com/AxonFramework/extension-kafka)
* [Axon Framework Kotlin Extension](https://github.com/AxonFramework/extension-kotlin)
* [Axon Framework Mongo Extension](https://github.com/AxonFramework/extension-mongo)
* [Axon Framework Multi-Tenancy Extension](https://github.com/AxonFramework/extension-multitenancy)
* [Axon Framework Reactor Extension](https://github.com/AxonFramework/extension-reactor)
* [Axon Framework Spring Ahead of Time Extension](https://github.com/AxonFramework/extension-spring-aot)
* [Axon Framework Spring Cloud Extension](https://github.com/AxonFramework/extension-springcloud)
* [Axon Framework Tracing Extension](https://github.com/AxonFramework/extension-tracing)

The Bill of Materials always follows at least the Axon Framework release cycle. 
So every new Axon Framework version will lead to a new Bill of Materials version. 
Releases of other dependencies may or may not lead to a new release.

## Getting Started - Maven

For usage with [Maven](https://maven.apache.org/), import the BOM in your project like so:

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

## Getting Started - Gradle

For usage with **[Gradle](https://gradle.org/) up to version 4.x**, apply the `dependency-management-plugin` plugin like so:

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

After this, import the Axon BOM:

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

Beginning with **[Gradle version 5.0](https://docs.gradle.org/5.0/userguide/managing_transitive_dependencies.html#sec:bom_import)**, you can also omit the dependency-management plugin and instead use the `platform` dependency dsl to import maven boms:

```
implementation(platform("org.axonframework:axon-bom:<VERSION>"))
```

## Receiving help

Are you having trouble using the bill of material or any of the contained dependencies?
We'd like to help you out the best we can!
There are a couple of things to consider when you're traversing anything Axon:

* Checking the [reference guide](https://docs.axoniq.io) should be your first stop,
  as the majority of possible scenarios you might encounter when using Axon should be covered there.
* If the Reference Guide does not cover a specific topic you would've expected,
  we'd appreciate if you could file an [issue](https://github.com/AxonIQ/reference-guide/issues) about it for us.
* There is a [forum](https://discuss.axoniq.io/) to support you in the case the reference guide did not sufficiently answer your question.
  Axon Framework and Server developers will help out on a best effort basis.
  Know that any support from contributors on posted question is very much appreciated on the forum.
* Next to the forum we also monitor Stack Overflow for any questions which are tagged with `axon`.

## Feature requests and issue reporting

We use GitHub's [issue tracking system](https://github.com/AxonFramework/axon-bom/issues) for new feature request,
framework enhancements and bugs.
Prior to filing an issue, please verify that it's not already reported by someone else.

When filing bugs:
* A description of your setup and what's happening helps us to figure out what the issue might be
* Do not forget to provide the framework version you're using
* If possible, share a stack trace, using the Markdown semantic ```

When filing features:
* A description of the envisioned addition or enhancement should be provided
* (Pseudo-)Code snippets showing what it might look like help us understand your suggestion better
* If you have any thoughts on where to plug this into the framework, that would be very helpful too
* Lastly, we value contributions to the framework highly. So please provide a Pull Request as well!
