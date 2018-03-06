
- [Performance profiling](#performance-profiling)
    - [Java Mission Control and Flight Recorder Demo Series : link](#java-mission-control-and-flight-recorder-demo-series-link)
    - [JOverflow : link](#joverflow-link)
    - [jps](#jps)
        - [Synopsis](#synopsis)
        - [Examples](#examples)
- [References](#references)

# Performance profiling

## Java Mission Control and Flight Recorder Demo Series : [link](https://www.youtube.com/playlist?list=PLKCk3OyNwIzsEVDq6zErLW7HSkY7aqdeT)

A very practical tool that Kewei has used to profile CPU and Memory usage:
* Find most CPU intensive parts of the application and reduce the time complexity of the algorithm
* Find the most memory intensive parts and reduce the space complexity of the algorithm

## JOverflow : [link](http://bit.ly/2f6eFLN)

Trace heap memory wasted by anti-patteern usage such as sparse array, duplicate string, etc.

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

# References

- [jps - Java Virtual Machine Process Status Tool][jps]

[jps]: https://docs.oracle.com/javase/7/docs/technotes/tools/share/jps.html