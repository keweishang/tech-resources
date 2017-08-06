# linux-command
Most useful Linux commands, iTerm2, oh-my-zsh shortkey that I use everyday.

# How to install oh-my-zsh
https://github.com/robbyrussell/oh-my-zsh

# File
| Command      | Description           |
| ------------- |-------------------|
| pbcopy < text.txt | Copy the file contents to your clipboard |
| touch file1 file2 | Create multiple empty files |

# Network
| Command      | Description           |
| ------------- |-------------------|
| lsof -i :80 | Show what is using up your current port |

# Performance
| Command      | Description           |
| ------------- |-------------------|
| time http www.lemonde.fr | Show the duration of a command |

# iTerm2
| Shortkey      | Description           |
| ------------- |-------------------|
| CMD + D | Split screen |
| CMD + ; | Auto-complete menu |
| CMD + Shift + H | Show paste history |
| CMD + / | Find the cursor |
| CMD + OPT + E | Search all tabs ( aka Expose tabs ) |

# oh-my-zsh (Git)
| Shortkey      | Command           | Comment           |
| ------------- |-------------------|-------------------|
| gaa | git add -A |  |
| gb | git branch |  |
| gcb | git checkout -b |  |
| gcmsg | git commit -m |  |
| gco | git checkout |  |
| gcount | git shortlog -sn | Check number of commits per person |
| gd | git diff |  |
| gf | git fetch |  |
| gpsup | git push --set-upstream origin $(current_branch) |  |
| gl | git pull |  |
| glo | git log --oneline --decorate --color |  |
| glol | git log --graph --pretty = format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit | check commits with graph and date |
| gp | git push |  |
| gst | git status |  |

# oh-my-zsh
| Command      | Description           |
| ------------- |-------------------|
| take newDir | Create a new directory, go into the new directory |

# zsh (navigation)
| Command      | Description           |
| ------------- |-------------------|
| Ctrl + A | Move to the beginning of the line |
| Ctrl + E | Move to the end of the line |
| Opt + left | Move one word backward |
| Opt + right | Move one word forward |
| Ctrl + U | Clear the entire line |
| Ctrl + K | Clear the characters on the line after the current cursor position |
| Ctrl + W | Delete the word in front of the cursor |
| Ctrl + L | Clear screen |

# zsh
| Command      | Description           |
| ------------- |-------------------|
| ls -l \**/*scala | list all files under current folder recursively |
| ls -l \*(py\|scala) | list all files whose suffix is py or scala |
| kill java[tab] | Choose and kill process related to java |
