# Tool sed

Learning tool **sed**. It is a stream editor, it reads the specified files, or
the standard input if no files are specified, modifying the input as specified
by a list of commands. The input is then written to the standard output.

A single command may be specified as the first arguments to **sed**. Multiple
commands may be specified by using the **-e** or **-f** options. All commands
are applied to the input in the order they are specified regardless of their
origin.

## Substitution

Substitutes the first occurrence of pattern 1 with pattern 2.

    s/pattern1/pattern2

**Example:** Use option **-e** to do a replace operation. You can also omit it,
because it's the default behavior:

```sh
$ echo hello | sed -e 's/ello/i/g'
hi
$ echo hello | sed 's/ello/i/g'
hi
```

**Example:** Multiple commands can be used together by using option **-e**:

```sh
$ echo ab | sed -e 's/a/1/g' -e 's/b/2/g'
12
```

## Regular Expressions

### Matching Characters

| No. | Expression and Description |
| --- | -------------------------- |
| 1   | `/a.c/` Matches lines that contain strings such as a+c, a-c, abc, match, and a3c |
| 2   | `/a*c/` Matches the same strings along with strings such as ace, yacc, and arctic |
| 3   | `/[tT]he/` Matches the string The and the |

**Example 1**: Matches characters that contains `.at` and replace it with `___`.
Dot `.` means any character:

```sh
$ echo 'cat in hat' | sed 's/.at/___/g'
___ in ___
```

**Example 2**: Matches characters that contains at least 0 character `a`,
followed with character `t`:

```sh
$ echo 'cat in hat' | sed 's/a*t/_/g'
c_ in h_
```

**Example 3**: Match character t and T in character class `[tT]`, followed by
`he`:

```sh
$ echo 'The the he' | sed 's/[Tt]he/_/g'
_ _ he
```

**Example 4**: Remove all the double-quote `"` from CSV file:

```sh
$ cat users.csv
"User A","10","Paris"
"User B","20","London"
"User C","30","New York"
"User d","40","Toulouse"

$ sed 's/"//g' users.csv
User A,10,Paris
User B,20,London
User C,30,New York
User d,40,Toulouse
```

**Example 5**: Remove all the matches starting with `User ` and following by at
least one alphabetic. Notice that flag **-E** must be enabled, because
`[[:alpha:]]` is modern regular expression. `[[:alpha:]]` is equivalent to
`[a-zA-Z]`:

```sh
$ cat users.csv
"User A","10","Paris"
"User B","20","London"
"User C","30","New York"
"User d","40","Toulouse"

$ sed -E 's/User [[:alpha:]]+//g' users.csv
"","10","Paris"
"","20","London"
"","30","New York"
"","40","Toulouse"

$ sed -E 's/User [a-zA-Z]+//g' users.csv
"","10","Paris"
"","20","London"
"","30","New York"
"","40","Toulouse"
```

### Matching Groups

**Example 1**: Find all the matched groups and use `\?` to print the `?`th
match. In the CSV file, group value surrounded by double quotes `"`, note as
group `\1`, group `\2`, and group `\3`. Then reverse the output order:

```sh
$ sed -E 's/"(.*)","(.*)","(.*)"/\3 \2 \1/g' users.csv
Paris 10 User A
London 20 User B
New York 30 User C
Toulouse 40 User d
```

## Sed Functions

### Flag d: Deletion

Deletes the line

**Example:** Delete all the lines (nothing left):

```sh
$ sed 'd' users.csv
```

**Example:** Delete the 2nd line from the input:

```sh
$ sed '2d' users.csv
"User A","10","Paris"
"User C","30","New York"
"User d","40","Toulouse"
```

### Flag p: Paste

Write the pattern space to standard output:

    [2addr]p

**Example 1**: Paste line 1 to 3 to standart output. Additionally with all the
lines:

```sh
$ sed '1,3p' users.csv
"User A","10","Paris"
"User A","10","Paris"    // pasted
"User B","20","London"
"User B","20","London"   // pasted
"User C","30","New York"
"User C","30","New York" // pasted
"User d","40","Toulouse"
```

**Example 2**: Paste line 1 to 3 to standart output and suppress the default
output behavior using flag `-n`. Useful for capturing an excerpt from a long
file.

```sh
$ sed -n '1,3p' users.csv
"User A","10","Paris"
"User B","20","London"
"User C","30","New York"
```

## References

```
$ man sed
```
