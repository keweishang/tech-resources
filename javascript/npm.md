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

## Configuration

Configuring npm can be done using `.npmrc` file. 4 relevant files:

- per-project config file (`/path/to/my/project/.npmrc`)
- per-use config file (`~/.npmrc`)
- global config file (`$PREFIX/etc/npmrc`)
- npm builtin config file (`/path/to/npm/npmrc`)

A typical usage is to use a custom registry URL instead of the official one. For
example:

```ini
# last modified: 01 Jan 2016
; Set a new registry for a scoped package
@myscope:registry=https://mycustomregistry.example.org
```

## Dependency

List dependencies of the current package:

    $ npm list

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

## References

- [npm documentation - npmrc](https://docs.npmjs.com/files/npmrc)
- [Stack Overflow - How to view dependency tree of a given npm
  module?](https://stackoverflow.com/questions/25997519/)
