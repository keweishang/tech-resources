# Bash

Without special notice, the following examples are written using the default
Bash shell of macOS:

```
$ bash -version
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin18)
Copyright (C) 2007 Free Software Foundation, Inc.
```

## Arithmetic

```bash
a=$(( 1 + 2 ))  # a=3
```

```bash
a=1
b=$(( $a + 2 ))  # b=3
```

```bash
a=$(( 1 * 2 ))  # a=2
```

## Input Arguments

Capture the first input argument of the bash script:

```sh
#
# bash my_script.sh apple banana coconut
#
fruit="$1"
# apple
```

Iterate over all the input arguments:

```sh
#
# bash my_script.sh apple banana coconut
#
for fruit in "$@"
do
    echo $fruit
done
# apple
# banana
# coconut
```

## If-Statement

### Regular Expression

Normal regular expression:

```bash
if [[ "$date" =~ ^[0-9]{4}-[0-9]{2}-[0-9]{2}$ ]]
```

Negate regular expression:

```bash
# inside
if [[ ! "$date" =~ ^[0-9]{4}-[0-9]{2}-[0-9]{2}$ ]]
# outside
if ! [[ "$date" =~ ^[0-9]{4}-[0-9]{2}-[0-9]{2}$ ]]
```

Contain keyword using `==`, e.g. word "2020":

```sh
if [[ "$date" == *"2020"* ]]
```

### Integer Comparison

Whether integer `a` is equal to interger `b`:

```sh
if [ "$a" -eq "$b" ]
```

Whether integer `a` is not equal to interger `b`:

```sh
if [ "$a" -ne "$b" ]
```

Whether integer `a` is greater than interger `b`:

```sh
if [ "$a" -gt "$b" ]
```

Whether integer `a` is greater than or equal to interger `b`:

```sh
if [ "$a" -ge "$b" ]
```

Whether integer `a` is less than interger `b`:

```sh
if [ "$a" -lt "$b" ]
```

Whether integer `a` is less than or equal to interger `b`:

```sh
if [ "$a" -le "$b" ]
```

## Array

### Create Array

```sh
fruits=(
  apple
  banana
  coconut
)
```

```sh
fruits=(apple banana coconut)
```

```sh
s="apple banana coconut"
fruits=($s)
```

### Iterate Array

```sh
for f in "${fruits[@]}"
do
    # do something
done
```

## For-Loop

Iterating array:

```sh
for f in 'apple' 'banana' 'coconut'
do
    echo $f
done
```

```sh
fruits=(apple banana coconut)
for f in "${fruits[@]}"
do
    echo $f
done
```

Listing PNG files:

```sh
for f in /path/to/images/*.png
do
    echo $f
done
```

Three-expression for-loop:

```sh
for (( i=1; i<=5; i++ ))
do  
    echo $i
done
```

## String Manipulation

### Substring Removal

> Tips:
>
> <kbd># 3</kbd><kbd>$ 4</kbd><kbd>% 5</kbd>
>
> In a standard keyboard layout, keys `3` / `4` / `5` represent `#` / `$` / `%`.
> Since `#` is before `$` and `%` is after `$`, deletion with `#`
> happens from front of string (`$`), and deletion with `%` happens from end
> of string (`$`).

Deleting the shortest match from front of string:

```bash
d=2019-01-02
echo ${d#*-}  # 01-02
```

Deleting the longest match from front of string:

```bash
d=2019-01-02
echo ${d##*-} # 02
```

Deleting the shortest match from back of string:

```bash
d=2019-01-02
echo ${d%-*}  # 2019-01
```

Deleting the longest match from back of string:

```bash
d=2019-01-02
echo ${d%%-*} # 2019
```

## Exit Codes

Determine the exit code of the last command:

```sh
echo $?
```

Exit Code | Meaning                                                    | Example                   | Comments
:-------- | :--------------------------------------------------------- | :------------------------ | :-------
`0`       | OK                                                         | `echo Hi`                 | OK
`1`       | Catchall for general errors                                | `let "var1 = 1/0"`        | Miscellaneous errors, such as "divide by zero" and other impermissible operations
`2`       | Misuse of shell builtins (according to Bash documentation) | `empty_function() {}`     | Missing keyword or command, or permission problem (and diff return code on a failed binary file comparison).
`126`     | Command invoked cannot execute                             | `/dev/null`               | Permission problem or command is not an executable
`127`     | "command not found"                                        | `illegal_command`         | Possible problem with `$PATH` or a typo
`128`     | Invalid argument to exit                                   | `exit 3.14159`            | `exit` takes only integer args in the range 0 - 255 (see first footnote)
`128+n`   | Fatal error signal "n"                                     | `kill -9 $PPID` of script | `$?` returns 137 (128 + 9)
`130`     | Script terminated by Control-C                             | Ctl-C                     | Control-C is fatal error signal 2, (130 = 128 + 2, see above)
`255*`    | Exit status out of range                                   | `exit -1`                 | `exit` takes only integer args in the range 0 - 255

## References

- <http://tldp.org/LDP/abs/html/exitcodes.html>
- StackOverflow: [How to check if a string contains a substring in Bash](https://stackoverflow.com/questions/229551/how-to-check-if-a-string-contains-a-substring-in-bash)
