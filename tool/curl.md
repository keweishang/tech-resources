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
