# Tool unzip

`unzip` -- list, test and extract compressed files in a ZIP archive.

## Unzip ZIP File

Unzip the target zip file in the current directory.

```
$ unzip my.zip
```

## List Files inside ZIP

List directories and regular files inside the target zip, without unzipping it.

```
$ unzip -l my.zip
```

## Show Content of Target Path inside ZIP

Show content of target path, e.g. `path/to/file` inside the target zip, without
unziping it.

```
$ unzip -l my.zip path/to/file
```

## References

- danielcraigie, "Read the contents of a zipped file without extraction?",
  _Stack Exchange_, 2012. <https://superuser.com/a/462796>
