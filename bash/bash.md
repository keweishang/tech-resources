# Bash

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
