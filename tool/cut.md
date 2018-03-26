# Description
Cut out selected portions of each line of a file.

## Cut out fields by delimited character

    cut -f list [-d delim] 

**Example:** cut out the rest of the string after the `=` character

```sh
$ echo "?client_id=198427177986-senvks6uulo5opucbli1q3qs6ig00r2a.apps.googleusercontent.com" | cut -f2 -d=
198427177986-senvks6uulo5opucbli1q3qs6ig00r2a.apps.googleusercontent.com
```