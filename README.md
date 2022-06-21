# tech-resources

Sharing ideas, useful technical resources, and thoughts.

## Cheatsheets

This repository provides cheatsheets to help you remind command lines. To use it
in macOS, you need to:

Install [cheat](https://github.com/cheat/cheat):

```
brew install cheat
```

Add the cheatsheets into your cheatpaths (`~/.config/cheat/conf.yml`):

```diff
  cheatpaths:
+   - name: tech-resources
+     path: /path/to/keweishang/tech-resources/cheatsheets/
+     readonly: true
```

Use as with the command that you want to cheat, e.g. `git`:

```
cheat git
```
