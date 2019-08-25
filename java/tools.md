# Java Tools

Different useful Java tools.

## jar

The Java Archive Tool. Usage:

    jar {ctxui}[vfmn0PMe] [jar-file] [manifest-file] [entry-point] [-C dir] files ...

Create a new Java archive (flag `-c`), save as file `fake.jar` (flag `-f`),
using the file `.content`. Useful for creating a fake JAR for testing:

    $ jar -cf fake.jar .content

View the table of contents (flag `-t`) for archive `fake.jar` (flag `-f`):

    $ jar -tf fake.jar
    META-INF/
    META-INF/MANIFEST.MF
    .content

## jshell

```
$ jshell --help
Usage:   jshell <option>... <load-file>...
where possible options include:
    --class-path <path>   Specify where to find user class files
    --module-path <path>  Specify where to find application modules
    --add-modules <module>(,<module>)*
                          Specify modules to resolve, or all modules on the
                            module path if <module> is ALL-MODULE-PATHs
    --enable-preview      Allow code to depend on preview features of this release
    --startup <file>      One run replacement for the startup definitions
    --no-startup          Do not run the startup definitions
    --feedback <mode>     Specify the initial feedback mode. The mode may be
                            predefined (silent, concise, normal, or verbose) or
                            previously user-defined
    -q                    Quiet feedback.  Same as: --feedback concise
    -s                    Really quiet feedback.  Same as: --feedback silent
    -v                    Verbose feedback.  Same as: --feedback verbose
    -J<flag>              Pass <flag> directly to the runtime system.
                            Use one -J for each runtime flag or flag argument
    -R<flag>              Pass <flag> to the remote runtime system.
                            Use one -R for each remote flag or flag argument
    -C<flag>              Pass <flag> to the compiler.
                            Use one -C for each compiler flag or flag argument
    --version             Print version information and exit
    --show-version        Print version information and continue
    --help, -?, -h        Print this synopsis of standard options and exit
    --help-extra, -X      Print help on non-standard options and exit

A file argument may be a file name, or one of the predefined file names: DEFAULT,
PRINTING, or JAVASE.
A load-file may also be "-" to indicate standard input, without interactive I/O.

For more information on the evaluation context options (--class-path,
--module-path, and --add-modules) see:
	/help context

A path lists the directories and archives to search. For Windows, use a
semicolon (;) to separate items in the path. On other platforms, use a
colon (:) to separate items.
```

### Import External Library in JShell

Using `--class-path` option from JShell, different JARs are separated by colon
(`:`)

```
$ jshell --classpath /opt/libs/guava-19.0.jar:/opt/libs/commons-lang3-3.4.jar
```

Specify `CLASSPATH` environment variable:

```
$ CLASSPATH="/opt/libs/commons-lang3-3.4.jar:/opt/libs/guava-19.0.jar" jshell
```

## References

- shizhz, "How to import external libraries in jshell java 9?", _Stack
  Overflow_, 2017. <https://stackoverflow.com/questions/43111018>
