# Description
Cut out selected portions of each line of a file.

## Cut out fields by delimited character

    cut -f list [-d delim] 

**Example:** cut out the rest of the string after the `=` character

```sh
$ echo "?id=123" | cut -f2 -d=
123
```
