# intellij-shortcuts
The most useful IntelliJ shortcuts that I use everyday.

Kewei's setting:

- Set `Navigation Bar` to `Off`: `Find Action (shift + cmd + a)` -> `Navigation Bar ...`
- Set `Tab placement` to `None`: `Find Action` -> `Tab placement ...`
- Install `Presentation Assistant` plug-in to show the shortcut on the screen everytime you type it
- Add additional `Scopes` named `No Test` to optionally exclude test code when searching function usage: `Find Action` -> `Edit Scopes` -> `Add Scope` -> name it `No Test` and include recursively `Library classes` and `Production classes` 

# Navigation
| Shortcut                                                     | Comment                                               |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| cmd + f12                                                    | show class members : functions, fields, inner classes |
| cmd + o                                                      | open class                                            |
| shift + cmd + o                                              | open file                                             |
| opt + cmd + o                                                | open symbol (fields and functions)                    |
| opt + cmd + b                                                | go to implementations of the interface                |
| opt + space                                                  | show definition of method/variable in pop-u           |
| cmd + e                                                      | recent files                                          |
| shift + cmd + e                                              | recent files + file content                           |
| shift + cmd + del                                            | navigate to last edit location                        |
| cmd + b                                                      | go to declaration / go to usages of method            |
| ctrl + h                                                     | type hierarchy                                        |
| shift + cmd + h                                              | method hierarchy                                      |
| ctrl + opt + h                                               | call hierarchy: callers of the function.              |
| opt + f7                                                     | find usages with preview (only prod + lib, no test)   |
| shift + cmd + f7                                             | highlight usages in current file                      |
| ctrl + g                                                     | multi-select next occurrence in current file          |
| ctrl + cmd + g                                               | select all occurrences in current file                |
| ctrl + opt + up/down                                         | next variable occurrence                              |
| shift + cmd + '                                              | maximise tool window                                  |
| shift + cmd + f12                                            | maximise editor window                                |
| opt + f12                                                    | open terminal                                         |
| f2                                                           | next problem                                          |
| shift + cmd + [ or ]                                         | go to left / right editor tab                         |
| cmd + [ or ]                                                 | undo / redo last navigation operation                 |
| fn + up or down arrow                                        | page up / down                                        |
| opt + cmd + [ or ]                                           | move caret to code block start/end, a.k.a { and }     |
| opt + cmd + Left                                             | Navigate back to previous view location               |
| opt + cmd + Right                                            | Navigate forward to next view location                |
| shift + cmd + p                                              | See where is the implicity parameter from             |
| ctrl + opt + shift + "+"/"-"                                 | Show Implicit Hints                                   |
| Press `opt` twice without releasing it, press `up` or `down` | Select multiple lines                                 |

# Search and Replace
| Shortcut        | Comment                 |
| --------------- | ----------------------- |
| cmd + r         | replace in current file |
| shift + cmd + r | replace in project      |

# Edit
| Shortcut              | Comment                                       |
| --------------------- | --------------------------------------------- |
| opt + shift + up/down | move up/down line                             |
| shift + cmd + up/down | move up/down while statement (function)       |
| shift + cmd + enter   | autocomplete the rest of the line             |
| cmd + del             | delete line                                   |
| cmd + d               | duplicate the current line                    |
| cmd + /               | comment the selection in multi-lines style    |
| opt + cmd + /         | comment the block                             |
| opt + ↑               | Incremental expression selection              |
| opt + del             | delete a word                                 |
| ctrl + space          | code completion                               |
| opt + cmd + l         | format code                                   |
| shift + cmd + u       | toggle between lowercase and uppercase        |
| cmd + p               | show constructor/method parameter             |
| opt + cmd + t         | surround statement by if/else, try/catch, etc |
| ctrl + space(twice)   | import static member                          |
| opt + enter           | add static import                             |
| ctrl + shift + p      | type info - what type a function call returns |
| shift + cmd + v       | paste from history                            |
| ctrl + shift + j      | join multiple lines into 1 line               |

# Refactoring
| Shortcut        | Comment  |
| --------------- | -------- |
| shift + cmd + t | add test |
| ctrl + t        | refactor |

# Run
| Shortcut         | Comment                                       |
| ---------------- | --------------------------------------------- |
| opt + cmd + r    | edit run configuration                        |
| ctrl + shift r/d | run / debug context configuration from editor |
| ctrl + r/d       | run / debug                                   |

# Debug
| Shortcut       | Comment                              |
| -------------- | ------------------------------------ |
| opt + cmd + f8 | Evaluating expressions in the editor |
| opt + f8       | Evaluating arbitrary expressions     |

# General
| Shortcut        | Comment             |
| --------------- | ------------------- |
| shift + cmd + a | find action by name |
