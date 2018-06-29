- [Performance profiling](#performance-profiling)
  - [Java Mission Control and Flight Recorder Demo Series : link](#java-mission-control-and-flight-recorder-demo-series-link)
  - [JOverflow : link](#joverflow-link)
- [jps](#jps)
  - [Synopsis](#synopsis)
  - [Examples](#examples)
- [JConsole](#jconsole)
  - [JConsole Synopsis](#jconsole-synopsis)
  - [JConsole Examples](#jconsole-examples)
    - [JConsole Views](#jconsole-views)
      - [VM Summary](#vm-summary)
      - [Overview](#overview)
      - [Memory](#memory)
      - [Threads](#threads)
      - [MBeans](#mbeans)
- [References](#references)

# Performance profiling

## Java Mission Control and Flight Recorder Demo Series : [link](https://www.youtube.com/playlist?list=PLKCk3OyNwIzsEVDq6zErLW7HSkY7aqdeT)

A very practical tool that Kewei has used to profile CPU and Memory usage:
* Find most CPU intensive parts of the application and reduce the time complexity of the algorithm
* Find the most memory intensive parts and reduce the space complexity of the algorithm

## JOverflow : [link](http://bit.ly/2f6eFLN)

Trace heap memory wasted by anti-patteern usage such as sparse array, duplicate string, etc.

# jps

`jps` - Java Virtual Machine Process Status Tool.

## Synopsis

    jps [ options ] [ hostid ]

## Examples

### Preparation

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

### Understand JPS arguments

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

### List Running Processes

`jps` is a good tool if you want to list the running Java processes.

```
$ jps
4817 server.jar
5038 Jps
```

Once you know the PID, you can send process signals to do some operations. For
example, to attempt to kill a process (more examples can be seen in
[DigitalOcean: How To Use ps, kill, and nice to Manage Processes in Linux][1]):

```
kill <PID>
```

# JConsole

Simple tool to inspect local and remote JVM.

## JConsole Synopsis

    jconsole

## JConsole Examples

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

Open another terminal and simply run the following command:

```
$ jconsole
```

Choose the JVM process you want to connect to, and click "Connect". Then go for "Insecure connection":
![Screen Shot 2018-03-06 at 11.39.20 AM](/assets/Screen%20Shot%202018-03-06%20at%2011.39.20%20AM.png)

### JConsole Views

#### VM Summary

You can see your JVM summary here: VM arguements, OS, Num of processors, JVM version, etc
![Screen Shot 2018-03-06 at 12.03.57 PM](/assets/Screen%20Shot%202018-03-06%20at%2012.03.57%20PM.png)

#### Overview

Inspecting charts of Heap Memory Usage, Threads, Classes, and CPU Usage:
![Screen Shot 2018-03-06 at 12.10.54 PM](/assets/Screen%20Shot%202018-03-06%20at%2012.10.54%20PM.png)

#### Memory

- Memory Usage of different spaces (young, old, etc)
- Perform GC manually

![Screen Shot 2018-03-06 at 12.12.58 PM](/assets/Screen%20Shot%202018-03-06%20at%2012.12.58%20PM.png)

#### Threads

- Number of threads (live and peak)
- For each thread, display thread's name, state, stack trace

![Screen Shot 2018-03-06 at 12.15.51 PM](/assets/Screen%20Shot%202018-03-06%20at%2012.15.51%20PM.png)

#### MBeans

- Call JVM build-in MBeans' methods on the fly
- Call custom MBeans' methods on the fly. So you can basically register an arbitrary function in your own Class as MBean method and call the function on the fly

![Screen Shot 2018-03-06 at 12.17.01 PM](/assets/Screen%20Shot%202018-03-06%20at%2012.17.01%20PM.png)

# References

- [jps - Java Virtual Machine Process Status Tool][jps]

[jps]: https://docs.oracle.com/javase/7/docs/technotes/tools/share/jps.html
[1]: https://www.digitalocean.com/community/tutorials/how-to-use-ps-kill-and-nice-to-manage-processes-in-linux
