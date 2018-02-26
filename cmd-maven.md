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
