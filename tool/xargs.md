# xargs

`xargs` -- construct argument list(s) and execute utility

## Replacement

`-I replstr`. Declare a placeholder `replstr` and replace one or more occurrences
to utility with the entire line of input. For example, declare `{}` as
placeholder, and replace all the occurreences of `{}` of each line by the input
argument (fruit):

```sh
> echo "apple banana coconut" | tr ' ' '\n' | xargs -I {} sh -c "echo /fruits/{}/{}-123"
/fruits/apple/apple-123
/fruits/banana/banana-123
/fruits/coconut/coconut-123
```

```sh
> echo "apple banana coconut" | tr ' ' '\n' | xargs -I % sh -c "echo /fruits/%/%-123"
/fruits/apple/apple-123
/fruits/banana/banana-123
/fruits/coconut/coconut-123
```
