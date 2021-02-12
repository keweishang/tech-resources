# Tool file

`file` -- determine file type.

## Encoding

Use option `--mime-encoding` to know the MIME encoding of the file:

```
$ file --mime-encoding foo.csv
foo.csv: utf-8

$ file --mime-encoding bar.csv
bar.csv: iso-8859-1
```

## Execution

Use option `-exec` followed by a command to execution another logic:

```sh
# Inside a personal blog powered by Jekyll, find out all the blog posts located inside directory
# "_posts" and replace the configuration "image: ..." by "cover: ..." inplace using a sed command.
# Tested on macOS.
find _posts -type f -exec sed -i '' -E 's/^image:(.*)/cover:\1/' {} +
```
