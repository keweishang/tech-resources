# How to install oh-my-zsh
https://github.com/robbyrussell/oh-my-zsh

# iTerm2
| Shortkey        | Description                         |
| --------------- | ----------------------------------- |
| CMD + D         | Split screen vertically             |
| CMD + Shift + D | Split screen horizontally           |
| CMD + ;         | Auto-complete menu                  |
| CMD + Shift + H | Show paste history                  |
| CMD + /         | Find the cursor                     |
| CMD + OPT + E   | Search all tabs ( aka Expose tabs ) |
| CMD + 1         | Switch to tab 1                     |
| CMD + Enter     | Toggle/Untoggle full screen mode    |
| CMD + Shift + Enter | Toggle/Untoggle full screen mode for current session |
| CMD + T         | New tab                             |
| CMD + W         | Close the current tab               |

# oh-my-zsh (Git)
| Shortkey | Command                                          | Comment                                                                             |
| -------- | ------------------------------------------------ | ----------------------------------------------------------------------------------- |
| gaa      | git add -A                                       |                                                                                     |
| gb       | git branch                                       |                                                                                     |
| gcb      | git checkout -b                                  |                                                                                     |
| gcmsg    | git commit -m                                    |                                                                                     |
| gco      | git checkout                                     |                                                                                     |
| gcount   | git shortlog -sn                                 | Check number of commits per person                                                  |
| gd       | git diff                                         |                                                                                     |
| gf       | git fetch                                        |                                                                                     |
| gpsup    | git push --set-upstream origin $(current_branch) |                                                                                     |
| gl       | git pull                                         |                                                                                     |
| glo      | git log --oneline --decorate --color             |                                                                                     |
| glol     | TL;DR                                            | Check commits with graph and date                                                   |
| gp       | git push                                         |                                                                                     |
| gst      | git status                                       |                                                                                     |
| gclean   | git clean -df                                    | Clean the working tree by recursively removing untracked files and directories (-d) |
| grhh     | git reset HEAD --hard                            | <sup>[1](#myfootnote1)</sup>                                                        |

# oh-my-zsh
| Command     | Description                                       |
| ----------- | ------------------------------------------------- |
| take newDir | Create a new directory, go into the new directory |

# zsh (navigation)
| Command     | Description                                                        |
| ----------- | ------------------------------------------------------------------ |
| Ctrl + A    | Move to the beginning of the line                                  |
| Ctrl + E    | Move to the end of the line                                        |
| Opt + left  | Move one word backward                                             |
| Opt + right | Move one word forward                                              |
| Ctrl + U    | Clear the entire line                                              |
| Ctrl + K    | Clear the characters on the line after the current cursor position |
| Ctrl + W    | Delete the word in front of the cursor                             |
| Ctrl + L    | Clear screen                                                       |

# zsh
| Command             | Description                                     |
| ------------------- | ----------------------------------------------- |
| ls -l \**/*scala    | list all files under current folder recursively |
| ls -l \*(py\|scala) | list all files whose suffix is py or scala      |
| kill java[tab]      | Choose and kill process related to java         |

# fzf
| Command     | Description                                       |
| ----------- | ------------------------------------------------- |
| Ctrl + R    | Fuzzy search command line history                 |

# Footnotes
<a name="myfootnote1">1</a>: If you do `git reset --hard <SOME-COMMIT>` then Git will:
Make your current branch (typically master) back to point at <SOME-COMMIT>.
Then make the files in your working tree and the index ("staging area") the same as the versions committed in <SOME-COMMIT>.
HEAD points to your current branch (or current commit), so all that git reset --hard HEAD will do is to throw away any uncommitted changes you have.
