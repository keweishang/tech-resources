# npm

Useful command about npm.

Firstly, you need to install NodeJS:

    $ brew install node

## Version

Show the version of npm:

    $ npm -version

## Install

> For more information, see <https://docs.npmjs.com/cli/install>.

Install a package:

    $ npm install <package>

Install a package in a global scope:

    $ npm install -g <package>
    $ npm install --global <package>

## Upgrade to Node 10

Install the specified version of Node (Node 10):

    $ brew install node@10

Unlink the current Node:

    $ brew unlink node@8

Link the new onei (`node@10` is keg-only and must be linked with `--force`):

    $ brew link --force node@10

Check everything works fine:

    $ node --version
    v10.13.0
