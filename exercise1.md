-Some common steps in a CI setup include linting, testing, and building. What are the specific tools for taking care of these steps in the ecosystem of the language you picked?

Java is a compiled language, so the build stage must compile the source into JVM bytecode. Here’s a starter pipeline: Compile -> Check Code -> Generate JAR.
The leading popular build tools in Java are Apache Maven and Gradle, both are included in Semaphore’s machines
Java developers use powerful IDEs that lint code in realtime. Powerful as they are, they are not enough. Quality checks must also be part of the CI pipeline. We can use checkstyle to add a linting job. Or, if you are using Maven, there’s a plugin for automatic linting. To enable it, add the maven.checkstyle.plugin to properties in your pom.xml.
Another nice checker to use in your CI environment is PMD. PMD works with Java, JavaScript, and Oracle’s SQL. 
Infer was created by Facebook to find code that can lead to runtime errors, things such as race conditions and resource leaks. Infer works with Java and Android. Facebook has open-sourced this tool and uses it to fix their mobile client and the main Facebook app.
Find Security Bugs uses a security database to detect almost 140 different vulnerability types in Java web applications.
We can generate a JAR file with: mvn package

-What alternatives are there to set up the CI besides Jenkins and GitHub Actions?

CircleCI
Bamboo (Atlassian)
Azure Pipelines
GitLab CI
Buddy
Buildkite
Travis CI
Drone

-Would this setup be better in a self-hosted or a cloud-based environment? Why? What information would you need to make that decision?


In general, if you have a small to medium software project that doesn't have any special requirements (e.g. a need for a graphics card to run tests), a cloud-based solution is probably best. The configuration is simple and you don't need to go to the hassle or expense of setting up your own system. For smaller projects especially, this should be cheaper.

For larger projects where more resources are needed or in larger companies where there are multiple teams and projects to take advantage of it, a self-hosted CI setup is probably the way to go.