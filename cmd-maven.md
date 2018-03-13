# Maven Commands

Useful Maven commands.

## Test

Skip all tests:

    mvn clean install -DskipTests

Skip all the unit-tests and run integration-tests only. Useful when you're
fixing some bugs in integration tests, and you don't want to spend extra time on
unit tests execution.

    mvn clean test-compile failsafe:integration-test

Run unit tests and integration tests:

    mvn clean verify

## Dependency

[Apache Maven Dependency Plugin][maven-dependency-plugin] can be used for
analyse and manipulate artifacts. Here're some examples.

List dependencies used to console:

    mvn dependency:tree

List dependencies used to a file (single-module):

    mvn dependency:tree -DoutputFile=/path/to/file

List dependencies used to a file (multi-modules):

    mvn dependency:tree -DoutputFile=/path/to/file -DappendOutput=true

## References

- [Apache Maven Dependency Plugin][maven-dependency-plugin]

[maven-dependency-plugin]: https://maven.apache.org/plugins/maven-dependency-plugin/
