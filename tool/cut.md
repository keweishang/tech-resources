# Tool cut

Learning tool `cut`. `cut` cuts out selected portions of each line of file.
Its synopsis is:

    cut -f list [-d delim]

In the following texts, we will use example data coming from `users.csv`,
located in the current directory:

```sh
$ cat users.csv
"User A","10","Paris"
"User B","20","London"
"User C","30","New York"
```

## Cut with Delimiter

Use `-d delim` as the field delimiter character instead of the tab character.

**Example:** Cut the input line with delimiter character: comma `,`, then takes
the 1st field from the results (result-index starts at 1). Rest of the fields
are ignored:

```sh
$ cut -f 1 -d , users.csv
"User A"
"User B"
"User C"
```

**Example:** Cut out the rest of the string after the `=` character:

```sh
$ echo "?id=123" | cut -f2 -d=
123
```

## Cut with Fields

The list specifies fields, separated in the input by the field delimiter
character (see the -d option.) Output fields are separated by a single
occurrence of the field delimiter character.

**Example:** Cut the input with `,` and keep the 1st field and the 2nd field:

```sh
$ cut -f 1,2 -d , users.csv
"User A","10"
"User B","20"
"User C","30"
```

**Example:** Cut the input with `,` and keep all the fields starting from the
2nd one:

```sh
$ cut -f 2- -d , users.csv
"10","Paris"
"20","London"
"30","New York"
```

**Example:** Cut the input with `,` and keep all the fields until the 2nd one
(the end-index `2` is inclusive):

```sh
$ cut -f -2 -d , users.csv
"User A","10"
"User B","20"
"User C","30"
```
