# schemacrawler-additionnallints 
[![Build Status](https://travis-ci.org/mbarre/schemacrawler-additionnallints.svg?branch=master)](https://travis-ci.org/mbarre/schemacrawler-additionnallints) [![Coverage Status](https://coveralls.io/repos/mbarre/schemacrawler-additionnallints/badge.png?branch=master&service=github)](https://coveralls.io/github/mbarre/schemacrawler-additionnallints?branch=master)

Some additionnal lints for [Schemacrawler](http://sualeh.github.io/SchemaCrawler/)

# Main purpose

The main purpose of this lint library is to enhance native schemacrawler lints
with some more hardcore constraints and some specific postgres types. That's
why a postgreSQL database instance is required to test.

This project has been created to be used at our office
[Mairie de la Ville de Nouméa](http://www.noumea.nc/) to test our database
schema quality in a more easy way and make it possible for our partners to
apply our database quality policy the easy way.


# Build and install lint

**Notice that this version is designed to run on schemacrawler `14.x.x`...
and hence is requiring JDK-1.8 to be built and run.**

For now the jar is not available on maven central repo, so you'll have to build it yourself :

    git clone https://github.com/mbarre/schemacrawler-additionnallints.git schemacrawler-additionnallints
    cd schemacrawler-additionnallints
    export LINT_VERSION=1.1-SNAPSHOT

Build without testing as a local postgres install is required to test.

    mvn install -Dmaven.test.skip=true
    cp target/schemacrawler-additionnallints-${LINT_VERSION}.jar $SCHEMACRAWLER_HOME/lib

... and you're done, you just have to pass your
normal  [schemacrawler lint](http://sualeh.github.io/SchemaCrawler/lint.html)
command and enjoy.

# Build and test

To ba able to test locally, assuming you have a locally postgreSQL instance
up and running with the proper `superuser` account, then run the following
commands

    dropdb --if-exists sc_lint_test
    createdb sc_lint_test
    mvn install
    cp target/schemacrawler-additionnallints-${LINT_VERSION}.jar $SCHEMACRAWLER_HOME/lib

# Pre-release tasks

Check that dependencies are up-to-date :

    mvn versions:display-dependency-updates

Check that plugins are up-to-date :

    mvn versions:display-plugin-updates