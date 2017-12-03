# Git Commands

## Global Configuration

```sh
git config --global user.name <user-name>
git config --global user.email <user-email>
git config --global core.excludesfile ~/.gitignore_global

# Using GPG Key
git config --global commit.gpgsign true
git config --global user.signingkey <GPGKey>
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

# Using GPG Key
git config --global alias.last 'log --show-signature -1 HEAD'
git config --global alias.lg 'log --format="%C(auto,yellow)%h%C(auto,magenta)% G? %C(auto,reset)%s%C(auto,red bold)% gD% D"'
```
