# Vim Commands

## Open

Open file and locate to a specific line, e.g. line 42:

    vi +42 myFile

Open Zip file:

    vi app.jar

Open Zip file and locate to a specific zip entry, e.g. log4j.xml in a JAR:

    vi zipfile:/path/to/app.jar::log4j.xml

## Highlight

| Command            | Description         |
| :----------------- | :------------------ |
| `:set syntax=html` | Highlight as `HTML` |
| `:set hls`         | Highlight search    |

## Navigation
| Command                     | Description                                                                       |
| :-------------------------- | :-------------------------------------------------------------------------------- |
| `:42`                       | Go to line 42                                                                     |
| `0`                         | Move to beginning of the current line                                             |
| `$`                         | Move to end of the current line                                                   |
| <kbd>⌃</kbd> + <kbd>U</kbd> | Move up half of the page                                                          |
| <kbd>⌃</kbd> + <kbd>D</kbd> | Move down half of the page                                                        |
| `w`                         | Cursor one word forward                                                           |
| `b`                         | Cursor one word back                                                              |
| `*`                         | Go to the next occurence of the word under cursor (can use `n` or `N` afterwards) |
| `f{char}`                   | Scan line for next character. `;` to repeat, `,` to reverse                       |
| `F{char}`                   | Scan line for previous character. `;` to repeat, `,` to reverse                   |

## Editing
| Command                 | Description                                                                                          |
| :---------------------- | :--------------------------------------------------------------------------------------------------- |
| `ddp`                   | Swap the current line with the next. Useful for re-organizing commits in e.p. `git rebase -i HEAD~5` |
| `ddkkp`                 | Swap the current line with the previous                                                              |
| `:s/target/replacement` | Perform substitution. `&` to repeat                                                                  |
| `:%s/\t/  /g`           | Replace tab by 2 spaces in the current editor.                                                       |
| `:%s/.$//`              | Remove the last character from the current editor.                                                   |
| `diw`                   | (delete inner word). Delete a word when the cursor is on it                                          |
| `:%w !pbcopy`           | On Mac: copy the whole file                                                                          |
| `a`                     | Append after the current cursor position                                                             |
| `A`                     | Append at the end of the current line                                                                |
| `s`                     | Delete the character under the cursor and then enters Insert mode                                    |
| `cw`                    | Delete to the end of the word and then drops us into Insert mode                                     |
| `ciw`                   | Delete the current word where the cursor is positioned and then drops us into Insert mode            |
| `.`                     | Repeat action                                                                                        |
| `u`                     | Undo                                                                                                 |
| `o`                     | Start a new line, move the cursor to the new line, then enters Insert mode                           |
