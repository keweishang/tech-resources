# Linux Useful Commands

Here's a collection of Linux useful commands. Without specific notice, these
examples are [POSIX](https://en.wikipedia.org/wiki/POSIX), thus portable to Mac
OS.

## File

### grep

```sh
grep 'key' Hi.java    # Lines containing 'key'
grep -n 'key' Hi.java # Lines containing 'key' and show line

# Recursively search files in the current directory `.` and its sub-directories
# containing the whole word 'key', and display the row number along side with
# the file name, where:
#   -r: recursive search
#   -n: line number
#   -w: match the whole word
grep -rnw '.' -e 'key'
grep --exclude-dir={.git,target} -rnw '.' -e 'key' # Show filename & line
grep --exclude-dir={.git,target} -rl '.' -e 'key'  # Show filename only (-l)
grep --include=\*.{c,h} -rnw '.' -e 'pattern'      # Search *.c and *.h
grep -i 'case.insensitive'                         # Case insensitive
```

### find

```sh
find . -name '*.java'                       # Find *.java in curr dir and sub-dirs
find . -name '*.java' | xargs grep 'key'    # Find *.java containing 'key'
find . -name '*SNAPSHOT.jar' -exec rm {} +  # Remove all the SNAPSHOTs
find . -name '*.sh' -exec chmod +x {} \;    # *.sh are now executable
find ./{a,b} -name 'Test*.java'             # Find Test*.java in dir a, b 
# Find JARs in */target
find . -type d -name target -exec find {} -depth 1 -name '*.jar' ;
# Find how many direct files start with 2017 in module A and B
find /project/module{A,B} -maxdepth 1 -name '2017*' -type f | wc -l
```

### pycopy

```sh
pbcopy < text.txt
```

Copy the file contents to your clipboard.

### touch

```sh
touch file1 file2
```

Create multiple empty files.

### watch

    watch [option(s)] command

`watch` is used to run any designated command at regular intervals. It displays
its output on a console. This makes it easy to observe the changing output of a
command over time.

For example:

    watch ls -l

will run `ls -l` every 2 seconds (by default) and display the result on
terminal. Useful for monitoring file changes during application debug.

## Network
- `lsof -i :80`

Show what is using up your current port

- Network I/O: `iftop` or `iftop -i eth0` (on any specific network interface)

Shows the data transfer rate, both for data sent and received, for the past 2 seconds, 10 seconds, and 40 seconds.

    nslookup <url>

Query the Domain Name System (DNS) to obtain domain name or IP address mapping
or for any other specific DNS record.

## Performance
- `time http www.lemonde.fr`

Show the duration of a command.

- CPU: `top -F -R -o cpu`

Show top CPU usages (sorted).

- CPU: `htop`

More colorful. Show each CPU core and processes' params.

- Memory: `watch -n 5 free -m` (or `htop` can show memory usage per process)

![Screen Shot 2017-09-24 at 13.40.14](https://i.imgur.com/fV3qYqQ.png)

- Disk I/O: `iotop`

Sequential IO (for HDD) is 100 ~ 200 times faster than random IO.

Sequential: SSD is 3 ~ 10 times faster than HDD
SSD Write/Read: 500 MB ~ 2 GB / sec
HDD Write/Read: 100 ~ 200 MB / sec

Random (reading/writing really small files, 4 kB in size, often the lower speed limit). SSD is 100 times faster than HDD:
SSD Write/Read: 200 ~ 400 MB/s
HDD Write/Read: 1 MB / sec
