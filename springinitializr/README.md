# Spring Breezes: Spring Initializr

*Spring* is a set of projects dedicated to solving common problems that we face
when developing enterprise applications. It supports the development of
applications using JVM with Java, Kotlin, or Groovy as the main language.

One of the core components of Spring is *Spring Boot*. This component makes easy
to create stand-alone, production-grade Spring-based applications. As mentioned
on [Spring Boot documentation](https://spring.io/projects/spring-boot): *they
take an ***opinionated*** view of the Spring platform and third-party libraries
so you can get started with minimum fuss*.

The "*opinionated view*" is another way to say
[convention-over-configuration](https://en.wikipedia.org/wiki/Convention_over_configuration).
And it's safe to trust them because this opinion comes from the people behind
Spring.

In other words, this is the easiest way to bootstrap a Spring-based application
worrying less about dependencies, configurations, and all the other boilerplate
that a JVM application usually requires.

## Spring Initializr

It's already easy to simply add *Spring Boot* dependencies in a naked Java
project to enable all the power of Spring Framework. However, the Spring team
made it even easier with [Spring Initializr](https://start.spring.io/).

![](https://cdn-images-1.medium.com/max/1600/1*QdK_PPO3MX3iu-sPg3doeA.png)
<small>*Spring Initializr screen with default configurations*</small>

With *Spring Initializr* you can bootstrap a *Spring Boot* project by simply
describing:

- a build automation tool
- the main programming language
- a Spring Boot version
- the project metadata
- the complementary dependencies

It offers the possibility to generate a project using
[Maven](https://maven.apache.org/) or [Gradle](https://gradle.org/) as the build
automation tool. I personally prefer Gradle because it uses Groovy to define the
build process and it's easier to write extensions. [Feel free to evaluate both and
choose the one of your preference](https://www.baeldung.com/ant-maven-gradle).

As I mentioned earlier, *Spring* focus on the JVM. It supports Java, Kotlin, or
Groovy as the main programming language. **Be aware!** I'll use Java! Most
Spring-related concepts and architectural definitions can be applied to any of
the three languages but some must be adjusted to the respective context and code
style if you choose either Kotlin or Groovy.

The *Spring Boot* version will basically define which *Spring* features you'll
have at your disposal. I'll use version **2.1.3** because it's the current
stable version during this post writing. [I don't recommend versions under 2.0
because you will miss a lot of good
things](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.0-Release-Notes).

The project metadata will be used to bootstrap the basic structure of your
application, such as the base package, the main class, Java version,
description, and other few things that affect your project structure.

As described by the [Java package
notation](https://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html),
companies usually use their reverse internet domain such as `com.google` or
`org.apache` plus the project name. For this series I'll use `com.breezes` plus
each post subtitle. For example, the project generated for this lesson will use `com.breezes.springinitializr`.

We are going to use *Java 8* and the packaging will be *Jar.*

Spring Boot by itself offers only the minimal core capabilities required by a
real application. To enable other capabilities we need to add more dependencies
and [Spring offers a lot of useful dependencies that solves almost every problem
you will face in an enterprise context](https://spring.io/projects).

To keep it simple, we are going to use only the *Web* dependency but in future
posts we'll cover other useful dependencies such as *JPA* and *Actuator*.

## The Final Configuration

Finally, our configuration without dependencies is:

![](https://cdn-images-1.medium.com/max/1600/1*4woC8_2VZSfvVsRK4g68JA.png)
<small>Spring Initializr screen with the following configurations selected: Project
"Gradle Project", Language "Java", Spring Boot "2.1.3", Group "com.breezes",
Artifact "springinitializr", Description "Demo project for Spring Boot", Package
Name "com.breezes.springinitializr", Packaging "Jar", and Java Version "8".</small>

The only selected dependency was *Web*:

![](https://cdn-images-1.medium.com/max/1600/1*N62AyDMT3_5K2Q_41XTbNA.png)
<small>Spring Initializr screen with the "Web" dependency selected.</small>

By clicking on the "**Generate Project**" button, *Spring Initiliazr* will
export a ZIP file with the same name defined in the project metadata.

Unzip this file and you'll have a project ready to run!

## Running the project

Using the command line, enter in the unzipped folder and type `./gradlew build`.
This command will execute all the build process and generate a `build` folder
with the production-ready code for your application.

Note that you don't even need to install Gradle. The first time you run any `./gradlew` command, it will download the required version of Gradle and put in
the `.gradle` folder. After this, your project will use this self-contained
Gradle instance to execute tasks. This is possible thanks to [Gradle
Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html).

Now run `java-jar build/libs/springinitializr-0.0.1-SNAPSHOT.jar` to spin up
your application embedded server and make your application available at
[http://localhost:8080/](http://localhost:8080/). **Be aware!** If you changed
the name of your application, probably you have to
replace `springinitializr-0.0.1-SNAPSHOT.jar` with the name of your application.

At this point, we didn't write any code, so if you try to access any URI it will
display a default 404 page.

![](https://cdn-images-1.medium.com/max/1600/1*5X-Noy6MOIgsuQcRsxFefg.png)
<small>The default 404 page with the following text: "Whitelabel Error Page. This
application has no explicit mapping for /error, so you are seeing this as a
fallback. Fri Mar 08 19:16:49 BRT 2019. There was an unexpected error (type=Not
Found, status=404). No message available"</small>

I strongly recommend that you use a version control system such as
[Git](https://git-scm.com/). By the way, Git is the default version control
system that Spring uses, and your project will come with a `.gitignore` already.

## To be continued…

In the next post, we are going to add our first "Hello World" route and its
respective component and unit tests.

Feel free to check out all the code of this Spring Breeze on
[GitHub](https://github.com/caique/spring-breezes/tree/master/springinitializr).
