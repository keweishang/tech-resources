# gdate

```sh
> gdate --help
Usage: gdate [OPTION]... [+FORMAT]
  or:  gdate [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
Display the current time in the given FORMAT, or set the system date.
```

```sh
> gdate --version
date (GNU coreutils) 8.32
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
```

## Installation

If you use macOS and need to install GNU date, use brew to install
`coreutils` and command `gdate` will be available.

```sh
> brew install coreutils
```

## String-To-Date

Convert an epoch timestamp in seconds to date:

```sh
> gdate --date=@1611360000
Sat Jan 23 01:00:00 CET 2021

> gdate -d @1611360000
Sat Jan 23 01:00:00 CET 2021
```

Convert an ISO-8601 string to date:

```sh
> gdate --date="2021-01-23T00:00:00Z"
Sat Jan 23 01:00:00 CET 2021

> gdate -d "2021-01-23T00:00:00Z"
Sat Jan 23 01:00:00 CET 2021
```

## Date-To-String

Format a date as epoch timestamp in seconds (`%s`):

```sh
> gdate --date="2021-01-23T00:00:00Z" +"%s"
1611360000
```

Format a date as ISO-8601 string format (`--iso-8601`) with precision to seconds
(`seconds`) in timezone UTC (`--utc`):

```sh
> gdate -d @1611360000 --iso-8601=seconds --utc
2021-01-23T00:00:00+00:00
```

## Comparison

_How to compare two dates?_

The easiest way is to convert them into epoch timestamps in seconds and then
compare them using [Bash conditional
expressions](https://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html):
`-eq`, `-ne`, `-lt`, `-le`, `-gt`, or `-ge`.

## References

- Bash Conditional Expressions (Bash Reference Manual)
  <https://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html>
