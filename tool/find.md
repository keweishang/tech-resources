# find

## BSD

```
FIND(1)                   BSD General Commands Manual                  FIND(1)

NAME
     find -- walk a file hierarchy

SYNOPSIS
     find [-H | -L | -P] [-EXdsx] [-f path] path ... [expression]
     find [-H | -L | -P] [-EXdsx] -f path [path ...] [expression]

DESCRIPTION
     The find utility recursively descends the directory tree for each path listed, evaluating an
     expression (composed of the ``primaries'' and ``operands'' listed below) in terms of each file in the
     tree.
```

### Find path

Find recursively the directory tree for each path listed.

```
$ find .git/refs
.git/refs
.git/refs/heads
.git/refs/heads/master
.git/refs/heads/find
.git/refs/tags
.git/refs/remotes
.git/refs/remotes/mincong
.git/refs/remotes/mincong/master
.git/refs/remotes/kewei
.git/refs/remotes/kewei/HEAD
.git/refs/remotes/kewei/master
```

### Find with maxdepth

Descend **at most** 2 directory levels below the command line arguments.

```
$ find .git/refs -maxdepth 2
.git/refs
.git/refs/heads
.git/refs/heads/master
.git/refs/heads/find
.git/refs/tags
.git/refs/remotes
.git/refs/remotes/mincong
.git/refs/remotes/kewei
```

### Find with depth

Descend all levels but only display the results at level 2. If the directory is
large, the traversal will take long time to finish.

```
$ find .git/refs -depth 2
.git/refs/heads/master
.git/refs/heads/find
.git/refs/remotes/mincong
.git/refs/remotes/kewei
```
