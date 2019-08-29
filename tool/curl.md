# Tool curl

**curl** is a tool to transfer data from or to a server, using one of the
supported protocols (DICT, FILE, FTP, FTPS, GOPHER, HTTP, HTTPS, IMAP, IMAPS,
LDAP,  LDAPS,  POP3, POP3S,  RTMP,  RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS,
TELNET and TFTP). The command is designed to work without user interaction.

## Dump Header

Use option `-D` to dump header to a target file.

```
-D, --dump-header <filename>
```

Example:

```
$ curl -D - https://google.com
HTTP/2 301
location: https://www.google.com/
content-type: text/html; charset=UTF-8
date: Thu, 25 Jul 2019 08:07:16 GMT
expires: Sat, 24 Aug 2019 08:07:16 GMT
cache-control: public, max-age=2592000
server: gws
content-length: 220
x-xss-protection: 0
x-frame-options: SAMEORIGIN
alt-svc: quic=":443"; ma=2592000; v="46,43,39"

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
```

## Show Header Only

Use option `-I` to display only header.

```
-I, --head
```

Example:

```
$ curl -I https://google.com
HTTP/2 301
location: https://www.google.com/
content-type: text/html; charset=UTF-8
date: Thu, 25 Jul 2019 08:10:05 GMT
expires: Sat, 24 Aug 2019 08:10:05 GMT
cache-control: public, max-age=2592000
server: gws
content-length: 220
x-xss-protection: 0
x-frame-options: SAMEORIGIN
alt-svc: quic=":443"; ma=2592000; v="46,43,39"
```

## Encode Query Parameter

Encode query parameter via option `--data-urlencode`:

```
$ curl -G https://example.com/search --data-urlencode "query=SELECT * FROM table"
```

This is useful when parameter is too long, and you want to delegate the URL
encoding to curl. For GET request, `-G` or `--get` is necessary, which will make
all data specified with `-d`, `--data`, `--data-binary`, or `--data-urlencode`
to be used in an HTTP request instead of the POST request. The data will be
appended to the URL with a '?' separator.

## Capture Output

Use option `-o, --output <file>` to write HTTP response body to file instead of
stdout.

For a single file, you can use `-O` instead of `-o <file>` to use the
last segment of the URL path as the filename. The file will be save inthe
current working directory. If you want the file saved in a different directory,
make sure you change the current working directory before invoking curl with
this option.

```
$ curl https://mincong-h.github.io/feed.xml -o feed.xml
$ curl https://mincong-h.github.io/feed.xml -O
```

## References

- damphat, "Any way to encode the url in curl command?", _Stack Exchange_, 2013.
  <https://unix.stackexchange.com/a/86737/220624>
- Greg Bray, "How to capture Curl output to a file?", _Stack Overflow_, 2017.
  <https://stackoverflow.com/a/47344751/4381330>
- Alex2php, "How to capture Curl output to a file?", _Stack Overflow_, 2012.
  <https://stackoverflow.com/a/13735150/4381330>
