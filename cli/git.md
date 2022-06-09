# Git

```
cheat git
```

## Rebase or Merge

- Rebase if:
    - Company branching strategy doesn't care if commits come from a branch
- Merge if:
    - Company branching strategy cares if commits come from a branch

## zsh

In Oh-My-Zsh (https://ohmyz.sh/), if you use the default settings, you will see something like:

```
➜  automation git:(master)
```

But if you want to know more about the current status of your workspace, you can install plugin
builtin plugin `gitfast` and export the following environment variables in the `~/.zshrc` file:

```diff
  plugins=(
    git
+   gitfast
  )
+ export GIT_PS1_SHOWDIRTYSTATE=1
+ export GIT_PS1_SHOWUNTRACKEDFILES=1
+ export GIT_PS1_SHOWSTASHSTATE=1
+ export GIT_PS1_SHOWUPSTREAM="verbose"
```

It shows the new files (`%`), untracked changes (`*`), tracked but uncommited changes (`+`), stashed changes (`$`), upstream branch (`=`):

```
➜  automation git:(master=) echo "Yeah" >> README.md
➜  automation git:(master *=) ✗ git add .
➜  automation git:(master +=) ✗ git stash
Saved working directory and index state WIP on master: 9cd3554 ...
➜  automation git:(master $=) git checkout -b topic
Switched to a new branch 'topic'
➜  automation git:(topic $)
```
