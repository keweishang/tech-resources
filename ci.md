# Continuous Integration

## Git

Version control system.

## Jira

Ticket tracking with Kanban board.

## Jenkins

Detect git push, merged pull request, then checkout the code, SBT/Maven(compile, unit tests, integration tests, build artifact, push to Nexus repo, automatically deploy to staging environment).

## Nexus

Repository where we put our built artifacts, also the repo where we get our dependencies from.

## Sonar

SonarQube (formerly Sonar) is an open source platform for continuous inspection
of code quality to perform automatic reviews with static analysis of code to
detect bugs, code smells and security vulnerabilities on 20+ programming
languages. SonarQube offers reports on duplicated code, coding standards, unit
tests, code coverage, code complexity, comments, bugs, and security
vulnerabilities.

When using SonarQube with Java in Maven, you can use Java agent [JaCoCo Maven
Plugin][jacoco-maven-plugin] to create a test coverage report and associate it
with SonarQube.

## Confluence

Team's internal wiki.

[jacoco-maven-plugin]: http://www.eclemma.org/jacoco/trunk/doc/maven.html
