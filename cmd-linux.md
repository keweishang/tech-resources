# Linux Useful Commands

Here's a collection of Linux useful commands. Without specific notice, these
examples are [POSIX](https://en.wikipedia.org/wiki/POSIX), thus portable to Mac
OS.

## File

### grep

    grep -rnw '/path/to/somewhere/' -e 'pattern'

Search files containing pattern. `-r` is recursive; `-n` is line number; `-w` stands for match the whole word; `-l` (lower-case L) can be added to just give the file name of matching files.

### find

    find /home/username/ -name "*.err"

Search for *.err files in the /home/username/ directory and all sub-directories.

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

## Network
- `lsof -i :80`

Show what is using up your current port

- Network I/O: `iftop` or `iftop -i eth0` (on any specific network interface)

Shows the data transfer rate, both for data sent and received, for the past 2 seconds, 10 seconds, and 40 seconds.

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