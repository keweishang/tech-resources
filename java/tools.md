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
