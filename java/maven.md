# Maven Commands

Useful Maven commands.

## Test

Run unit tests and integration tests:

    mvn clean verify

Skip all tests:

    mvn clean install -DskipTests

Skip all the unit-tests and run integration-tests only. Useful when you're
fixing some bugs in integration tests, and you don't want to spend extra time on
unit tests execution.

    mvn clean test-compile failsafe:integration-test

Skip all the integration-tests and run unit-tests only. Flag
`failIfNoTests=false` is useful for multi-modules project, since some modules do
not have any tests:

    mvn clean install -DfailIfNoTests=false -DskipITs

Skip all the integration-tests and run a single unit-test `<TestName>`:

    mvn clean install -DfailIfNoTests=false -DskipITs -Dtest=<TestName>

Debug unit test in Surefire:

    mvn -Dmaven.surefire.debug test

Debug integration test in Failsafe:

    mvn -Dmaven.failsafe.debug verify

## Dependency

[Apache Maven Dependency Plugin][maven-dependency-plugin] can be used for
analyse and manipulate artifacts. Here're some examples.

List dependencies used to console:

    mvn dependency:tree

List dependencies used to a file (single-module):

    mvn dependency:tree -DoutputFile=/path/to/file

List dependencies used to a file (multi-modules):

    mvn dependency:tree -DoutputFile=/path/to/file -DappendOutput=true

## Debug

Debug Maven build by enabling the debug level log (flag `-X`):

   mvn -X <goal>

## Help

[Apache Maven Help Plugin][maven-help-plugin] can be used to get relative
information about a project or the system.

Show the effective POM:

    mvn help:effective-pom

## Enforcer

[Apache Maven Enforcer Plugin][maven-enforcer-plugin] enforces the Maven build
by adding rules to the POM. For example:

- Require Java version.
- Require Maven version.
- Ban duplicate Maven dependency declaration.

The plugin can be executed as:

    mvn enforcer:enforce

## References

- Maven, "Apache Maven Dependency Plugin", _Apache Maven_, 2018.
  <https://maven.apache.org/plugins/maven-dependency-plugin/>
- Maven, "Apache Maven Enforcer Plugin", _Apache Maven_, 2018.
  <https://maven.apache.org/enforcer/maven-enforcer-plugin/>
- Maven, "Apache Maven Help Plugin", _Apache Maven_, 2018.
  <https://maven.apache.org/plugins/maven-help-plugin/>
- Maven, "Maven Surefire Plugin - Debugging Tests", _Apache Maven_, 2018.
  <http://maven.apache.org/surefire/maven-surefire-plugin/examples/debugging.html>
- Maven, "Maven Failsafe Plugin - Debugging Tests", _Apache Maven_, 2018.
  <http://maven.apache.org/surefire/maven-failsafe-plugin/examples/debugging.html>

[maven-dependency-plugin]: https://maven.apache.org/plugins/maven-dependency-plugin/
[maven-enforcer-plugin]: https://maven.apache.org/enforcer/maven-enforcer-plugin/
[maven-help-plugin]: https://maven.apache.org/plugins/maven-help-plugin/
