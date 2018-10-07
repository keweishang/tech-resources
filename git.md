# Git Commands

## Global Configuration

```sh
git config --global user.name <user-name>
git config --global user.email <user-email>
git config --global core.excludesfile ~/.gitignore_global

# Using GPG Key
git config --global commit.gpgsign true
git config --global user.signingkey <GPGKey>

# Proxy
git config --global http.proxy <proxy-url>
git config --global --unset http.proxy
```

## Git Alias

```sh
git config --global alias.amend 'commit --amend'
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.pr 'pull --rebase'
git config --global alias.wip 'commit -a -m wip'
git config --global alias.cpick cherry-pick
git config --global alias.last 'log -1 HEAD'
git config --global alias.lg 'log --oneline'
git config --global alias.graph 'log --graph --all --oneline --decorate'

# Using GPG Key
git config --global alias.last 'log --show-signature -1 HEAD'
git config --global alias.lg 'log --format="%C(auto,yellow)%h%C(auto,magenta)% G? %C(auto,reset)%s%C(auto,red bold)% gD% D"'

# Proxy
git config http.proxy <proxy-url>
git config --unset http.proxy
```

## Initialization

```sh
git init
git init --bare
```

## GPG Signed Commit

Disable GPG signature for a single repository:

    git config commit.gpgsign false

## Reset

```sh
# Use reset when your changes cannot be seen by other developers (e.p. by convention or because it is local). If it's seen by others, use revert instead.
# There are 3 types of reset: soft, mixed, hard.

# Soft: reset git commit history to a (previous) commit id, put the diff changes in staging directory
git reset --soft <commit-id>

# Mixed: reset git commit history to a (previous) commit id, put the diff changes in working directory
git reset <commit-id>
# git reset without a commit-id will unstage the changes (without losing them)
git reset
# Interactively preview and unstage individual changes. It works even within the same file, part of the file could be unstaged, other parts would stay staged.
git reset -p

# Hard: reset git commit history to a (previous) commit id, revert all changes of tracked files to the previous state, leaves untracked files alone
git reset --hard <commit-id>

```

## Revert

```sh
# Use revert if other developers have seen your changes, and you want to "revert" your changes. This will create a new commit instead of changing the commit history.
```

## Clean

```sh
# Clean untracked files and directories. The option -d and -f means cleaning files and directories respectively
git clean -df

```

## Cheery Pick

```sh
# Use case 1: make a new commit based off another commit from another branch. Typically used when you committed in the wrong branch and want to move the commit to the correct branch. Use reset --hard and clean to revert the wrong branch to the initial state.
git cherry-pick <commit-id>

```

## Add

```sh
# Interactively preview and stage individual changes. It works even within the same file, part of the file could be staged, other parts would not be unstaged.
git add -p
```

## Log

```sh

```