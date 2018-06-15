# Vim Commands

## Open

Open Vim to a specific line, e.g. line 42:

    vim +42 myFile

## Navigation
| Command                     | Description                           |
| :-------------------------- | :------------------------------------ |
| `:42`                       | Go to line 42                         |
| `0`                         | Move to beginning of the current line |
| `$`                         | Move to end of the current line       |
| <kbd>⌃</kbd> + <kbd>U</kbd> | Move up half of the page              |
| <kbd>⌃</kbd> + <kbd>D</kbd> | Move down half of the page            |
| `w`                         | Cursor one word forward               |
| `b`                         | Cursor one word back                  |


## Editing
| Command       | Description                                                                                          |
| :------------ | :--------------------------------------------------------------------------------------------------- |
| `ddp`         | Swap the current line with the next. Useful for re-organizing commits in e.p. `git rebase -i HEAD~5` |
| `ddkkp`       | Swap the current line with the previous                                                              |
| `u`           | Undo                                                                                                 |
| `:%s/\t/  /g` | Replace tab by 2 spaces in the current editor.                                                       |
| `:%s/.$//     | Remove the last character from the current editor.                                                   |
| `diw`         | (delete inner word). Delete a word when the cursor is on it                                          |
