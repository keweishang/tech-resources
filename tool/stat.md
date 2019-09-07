# stat

Display file status.

```
STAT(1)                   BSD General Commands Manual                  STAT(1)

NAME
     readlink, stat -- display file status

SYNOPSIS
     stat [-FLnq] [-f format | -l | -r | -s | -x] [-t timefmt] [file ...]
     readlink [-n] [file ...]

DESCRIPTION
     The stat utility displays information about the file pointed to by file.  Read, write or execute per-
     missions of the named file are not required, but all directories listed in the path name leading to
     the file must be searchable.  If no argument is given, stat displays information about the file
     descriptor for standard input.

     When invoked as readlink, only the target of the symbolic link is printed.  If the given argument is
     not a symbolic link, readlink will print nothing and exit with an error.

     The information displayed is obtained by calling lstat(2) with the given argument and evaluating the
     returned structure.
```

## Show All Detail

Display information in a more verbose way as known from some Linux distributions.

```
$ stat -x README.md
  File: "README.md"
  Size: 5707         FileType: Regular File
  Mode: (0644/-rw-r--r--)         Uid: (  501/ mincong)  Gid: (   20/   staff)
Device: 1,4   Inode: 8608922817    Links: 1
Access: Sat Sep  7 21:11:42 2019
Modify: Thu Sep  5 20:48:59 2019
Change: Thu Sep  5 20:48:59 2019
```

## Show Time

a: the time _file_ was last accessed

```
$ stat -f "%a" README.md
1567883502
```

m: the time _file_ was last modified

```
$ stat -f "%m" README.md
1567709339
$ stat -f '%Sm' README.md
Sep  5 20:48:59 2019
```

c: the time of when the inode was last changed

```
$ stat -f "%c" README.md
1567709339
$ stat -f '%Sc' README.md
Sep  5 20:48:59 2019
```

B: the birth time of the inode

```
$ stat -f "%B" README.md
1567709339
$ stat -f '%SB' README.md
Sep  5 20:48:59 2019
```

## Show Size

z: the size of file in bytes

```
$ stat -f "%z bytes" README.md
5707 bytes
```
