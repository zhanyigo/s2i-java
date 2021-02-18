# OpenShift S2I Builder for Java

This Source-to-Image Builder let's you create projects targetting Java OpenJDK 8 and built with:

* maven
* gradle

NOTE: If a project has a pom.xml and a build.gradle, maven will take precedence

This builder/runtime s2i image can be used with SpringBoot, Vert.X, Wildfly Swarm, DropWizard and many other microservices frameworks. 

## BUILD ENV Options

* APP_SUFFIX: Jar file suffix to use to locate the generated artifact to use (e.g. xxxxx${APP_SUFFIX}.jar)
* BUILDER_ARGS: Allows you to specify options to pass to maven or gradle
* MAVEN_MIRROR_URL: Allows configure mirror url

## Defaults

If you do not specify any BUILDER_ARGS, by default the s2i image will use the following:

### Maven

----

MAVEN_ARGS="package -Popenshift -DskipTests -Dcom.redhat.xpaas.repo.redhatga"

----

### Gradle

----

BUILDER_ARGS="build -x test"

----

## Test in OpenShift

* First load all the needed resources in a project.

```bash

oc create -f https://raw.githubusercontent.com/jorgemoralespou/s2i-java/master/ose3/s2i-java-imagestream.json

```

* Once the builder s2i-java has been registered, you can create an app with:
  * Instant app already provided as template
  * Using the s2i-java builder image using a regular Git repository

## Samples

There is a lot of example SpringBoot applications https://github.com/spring-projects/spring-boot/tree/master/spring-boot-samples[here]
