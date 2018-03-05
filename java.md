# Java

Resources related to Java.

## Performance profiling

### Java Mission Control and Flight Recorder Demo Series : [link](https://www.youtube.com/playlist?list=PLKCk3OyNwIzsEVDq6zErLW7HSkY7aqdeT)

A very practical tool that Kewei has used to profile CPU and Memory usage:
* Find most CPU intensive parts of the application and reduce the time complexity of the algorithm
* Find the most memory intensive parts and reduce the space complexity of the algorithm

#### JOverflow : [link](http://bit.ly/2f6eFLN)

Trace heap memory wasted by anti-patteern usage such as sparse array, duplicate string, etc.

## Java 9 Update

This section describes how to update an existing Maven project to Java 9.

### Install Java 9

- Download JDK 9 from [Java SE Development Kit 9 Downloads][jdk9-download]
- Install JDK 9
- Ensure that Java verion is 9:

      $ java -version
      java version "9.0.4"
      Java(TM) SE Runtime Environment (build 9.0.4+11)
      Java HotSpot(TM) 64-Bit Server VM (build 9.0.4+11, mixed mode)

- Ensure that Java compiler version is 9:

      $ javac -version
      javac 9.0.4

### Update IDE

Ensure that your IDE is using the correct JDK. If you're using IntelliJ IDEA,
you should change the Project SDK:

- Open _Project Settings_ (<kbd>⌘</kbd> + <kbd>;</kbd>)
- Click button _New..._ in section _Project SDK_, choose _JDK_
- IntelliJ should already point to the new JDK: JDK 9. Click _Open_
- Click _OK_ to save changes.

Now we're done.

### Update Maven Project

#### Maven Compiler Plugin

In pom.xml file, change the source and target value from **1.8** to **9** for
Maven compiler plugin:

```xml
<properties>
  <maven.compiler.source>9</maven.compiler.source>
  <maven.compiler.target>9</maven.compiler.target>
</properties>
```

#### Maven Dependency Plugin

Maven dependency plugin does not support Java 9 bytecode analysis yet, due to:
[MDEP-559 Java 9 bytecode cannot be parsed][MDEP-559]. The issue is fixed in
3.1.0, which is not released yet. As a result, the goal `dependency:analyze` and
`dependency:analyze-only` cannot be used. And we need to disable the plugin
completely:

```xml
<mdep.analyze.skip>true</mdep.analyze.skip>
```

### Update Travis CI

Change the JDK version in Travis CI configuration file `.travis.yml` to use the
JDK 9:

```yml
jdk:
  - oraclejdk9
```

### Fix Dependency Issues

The Java EE APIs are no longer contained on the default class path in Java SE 9.
Some APIs like JAXB, Java Activation must be added as dependencies. Java 9
introduces the concepts of modules, and by default the `java.se` aggregate
module is available on the class path (or rather, module path). As the name
implies, the `java.se` aggregate module does not include the Java EE APIs that
have been traditionally bundled with Java 6/7/8.

Add the following dependencies to Maven to resolve
`java.lang.NoClassDefFoundError`:

```xml
<dependency>
  <groupId>javax.xml.bind</groupId>
  <artifactId>jaxb-api</artifactId>
  <version>2.2.11</version>
</dependency>
<dependency>
  <groupId>com.sun.xml.bind</groupId>
  <artifactId>jaxb-core</artifactId>
  <version>2.2.11</version>
</dependency>
<dependency>
  <groupId>com.sun.xml.bind</groupId>
  <artifactId>jaxb-impl</artifactId>
  <version>2.2.11</version>
</dependency>
<dependency>
  <groupId>javax.activation</groupId>
  <artifactId>activation</artifactId>
  <version>1.1.1</version>
</dependency>
```

## jps

`jps` - Java Virtual Machine Process Status Tool.

### Synopsis

    jps [ options ] [ hostid ]

### Examples

Before talking to examples, let's create a small Java program:

```java
import java.util.Scanner;

public class App {
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    System.out.print("Please enter your name: ");
    String name = scanner.next();
    System.out.println("Welcome, " + name);
  }
}
```

Now, compile and execute the program `App`:

```
$ javac App.java
$ java App
```

Open another terminal and list the instrumented JVMs on the local host:

```
$ jps
56113        // IntelliJ IDEA
56312 Jps    // JVM Process Status Tool
56047 App    // App for demo
```

Option `-l` output the full package name for the application's main class or the
full path name to the application's JAR file:

```
$ jps -l
56113                             // IntelliJ IDEA
56322 jdk.jcmd/sun.tools.jps.Jps  // JPS with full path, also PID changed
56047 App                         // App for demo
```

Option `-v` outputs the arguments passed to the JVM:

```
$ jps -v
56113  -Xms1g -Xmx4g -XX:ReservedCodeCacheSize=240m -XX:+UseCompressedOops -Djb.vmOptionsFile=/Users/mincong/Library/Preferences/IntelliJIdea2017.3/idea.vmoptions -Xbootclasspath/a:/Applications/IntelliJ IDEA.app/Contents/lib/boot.jar -Didea.java.redist=jdk-bundled -Didea.home.path=/Applications/IntelliJ IDEA.app/Contents -Didea.executable=idea -Didea.paths.selector=IntelliJIdea2017.3
56047 App
56398 Jps -Dapplication.home=/Library/Java/JavaVirtualMachines/jdk-9.0.4.jdk/Contents/Home -Xms8m -Djdk.module.main=jdk.jcmd
```

Option `-m` outputs the arguments passed to the main method. The output may be
null for embedded JVMs:

```
$ jps -m
56113
56047 App
56410 Jps -m
```

## References

- [jps - Java Virtual Machine Process Status Tool][jps]

[jps]: https://docs.oracle.com/javase/7/docs/technotes/tools/share/jps.html
[MDEP-559]: https://issues.apache.org/jira/browse/MDEP-559
[jdk9-download]: http://www.oracle.com/technetwork/java/javase/downloads/jdk9-downloads-3848520.html
