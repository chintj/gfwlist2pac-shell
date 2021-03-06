gfwlist2pac-shell
=================

Translate the gfwlist in base64 to efficient pac file

This project is mainly created by [@clowwindy](https://github.com/clowwindy/gfwlist2pac) via python

This version is just an implementation of pure shell

Generate O(1) PAC file from gfwlist.

### Dependency
  The cli version of `curl`, `openssl` which was integrated into most popular linux version.

  You can specify the tools customly.

```bash
# curl & openssl cli command path
CURL=/usr/bin/curl
OPENSSL=/usr/bin/openssl
```
  A socks5 proxy is needed to download the gfwlist. 

  You can make one via shadowsocks or ssh -D, the `PROXY` will be used to generate the pac file as well, so it should be an commonly used local address.

```bash
# socks5 proxy ssh -D, shadowsocks or others
PROXY="127.0.0.1:7070"
```
### Custom
  You can add some domains to `custom.txt`, it will be added into the pac file automatically.
  One domain per-line.
```
github.com
dropbox.com
linode.com
stackoverflow.com
linost.com
eigenlogik.com
iceimg.com
jetbrains.com
instagram.com
linkedin.com
agilebits.com
godaddy.com
startssl.com
btdigg.org
digitalattackmap.com
igvita.com
apache.org
jquery.com
speedtest.net
```

### Usage
  after all dependency ready

  Usage. `./gfw.sh [filename.pac]`

  Eg. `./gfw.sh release/proxy.pac`

  The proxy.pac will be generated to `release/proxy.pac`

### Performance

An example of generated PAC file is [here] [1].

The PAC generated by GFWList2PAC is 1267x faster than SwitchySharp.

    Testing pac generated by gfwlist2pac
    total: 46.411584ms
    avg: 0.6706876300578034ns
    
    Testing pac generated by switchsharp
    total: 58828.813476ms
    avg: 850.1273623699423ns

[1]: https://gist.github.com/cuber/7e1cb2864ec139236b59
