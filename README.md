<img src="https://www.cohesionfirst.org/logo.png" align="right"/>
## commons-jetty<br>![java-commons][java-commons] <a href="https://www.cohesionfirst.org/"><img src="https://img.shields.io/badge/CohesionFirst%E2%84%A2--blue.svg"></a>
> Commons Embedded Jetty Wrapper

### Introduction

This project is a light wrapper of the [Jetty Servlet Container][jetty], which provides helpful patterns to developers that desire a lightweight embedded server solution.

### Why **commons-jetty**?

#### CohesionFirst™

Developed with the CohesionFirst™ approach, **commons-jetty** is built to make a developer's life easier. Made possible by the rigorous conformance to design patterns and best practices in every line of its implementation, **commons-jetty** is simple to use and easy to understand.

#### Cohesive and Simple API for Embedded Servlet Container Initialization

**commons-jetty** is created to take full advantage of the `javax.servlet.annotation.*` annotations defined in the [Java Servlet v3 Specification of 2009][servlet-v3-spec]. Designed specifically to avoid non-cohesive config files, **commons-jetty** creates a direct and easy to understand embedded wrapper of the Jetty Servlet Container. **commons-jetty** provides a simple API to initialize a Servlet Container in a JVM, significantly reducing the headache most people have when attempting to accomplish the same with Jetty's raw APIs.

### Significantly Reduces Boilerplate Code

**commons-jetty** is intended to reduce the number of lines of code dedicated to the initialization of the server, therefore reducing the space of possible errors, and thus allowing the developer to move to his next task, confidently assured the server will start.

### Getting Started

#### Prerequisites

* [Java 7][jdk7-download] - The minimum required JDK version.
* [Maven][maven] - The dependency management system.

#### Example

1. In your preferred development directory, create a [`maven-archetype-quickstart`][maven-archetype-quickstart] project.

  ```tcsh
  mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
  ```

2. Add the `mvn.repo.safris.org` Maven repositories to the POM.

  ```xml
  <repositories>
    <repository>
      <id>mvn.repo.safris.org</id>
      <url>http://mvn.repo.safris.org/m2</url>
    </repository>
  </repositories>
  <pluginRepositories>
    <pluginRepository>
      <id>mvn.repo.safris.org</id>
      <url>http://mvn.repo.safris.org/m2</url>
    </pluginRepository>
  </pluginRepositories>
  ```
  
3. Next, add the `org.safris.commons:jetty` dependency to the POM.

  ```xml
  <dependency>
    <groupId>org.safris.commons</groupId>
    <artifactId>jetty</artifactId>
    <version>1.1.2</version>
  </dependency>
  ```

3. Make `App` extend `org.safris.commons.jetty.EmbeddedServletContainer`, and add a constructor.

  ```java
  public class App extends EmbeddedServletContainer {
    public static void main(final String[] args) {
    }
    
    public App(final int port, final String keyStorePath, final String keyStorePassword, final boolean externalResourcesAccess, final $se_realm realm, final Class<? extends HttpServlet> ... servletClasses) {
      super(port, keyStorePath, keyStorePassword, externalResourcesAccess, realm, servletClasses);
    }
  }
  ```

4. Include the server initialization code in `main()`.

  ```java
  public static void main(final String[] args) {
    final Server server = new Server(8080, null, null, true, null);
    server.start();
    server.join();
  }
  ```

9. Run `App`.

### License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.

[java-commons]: https://img.shields.io/badge/java-commons-orange.svg
[jdk7-download]: http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html
[jetty]: http://www.eclipse.org/jetty/
[maven-archetype-quickstart]: http://maven.apache.org/archetypes/maven-archetype-quickstart/
[maven]: https://maven.apache.org/
[servlet-v3-spec]: http://download.oracle.com/otn-pub/jcp/servlet-3.0-fr-eval-oth-JSpec/servlet-3_0-final-spec.pdf?AuthParam=1480559853_acb6e03a9239ef531494496d67f2d301