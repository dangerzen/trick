# Flushing your DNS cache in Mac OS X and Linux

## Flushing your cache on Mac OS X

The commands to flush cache in OS X are slightly different depending on the version you're running. First, make sure you've opened up your terminal on your computer.

- [SSH client software](https://help.dreamhost.com/hc/en-us/articles/215360828-SSH-client-software)

Once opened, run the command below that corresponds to your [version of OS X](https://support.apple.com/en-us/HT201260).

### OS X 12 (Sierra) and later

```
macbook$ sudo killall -HUP mDNSResponder;sudo killall mDNSResponderHelper;sudo dscacheutil -flushcache
```

### OS X 11 (El Capitan) and OS X 12 (Sierra)

```
macbook$ sudo killall -HUP mDNSResponder
```

### OS X 10.10 (Yosemite)

#### Versions 10.10.4+

```
macbook$ sudo dscacheutil -flushcache;sudo killall -HUP mDNSResponder
```

#### Versions 10.10.1, 10.10.2, 10.10.3

```
macbook$ sudo discoveryutil udnsflushcaches
```

## Older versions

### OS X 10.9 (Mavericks)

```
macbook$ dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

### OS X 10.7 (Lion) and 10.8 (Mountain Lion)

```
macbook$ sudo killall -HUP mDNSResponder
```

### OS X 10.5 (Leopard) and 10.6 (Snow Leopard)

```
macbook$ dscacheutil -flushcache
```

### OS X 10.4 (Tiger)

```
macbook$ lookupd -flushcache
```

## Flushing your DNS cache in Linux

Most current Linux distributions do not use a DNS resolver cache in the same way that Windows and Mac OS X use. To confirm which particular daemon is installed for your Linux distribution, check the website or its forum pages.

However, a common DNS caching application sometimes used is the [Name Service Caching Daemon (nscd)](http://linux.die.net/man/8/nscd). It’s most likely not installed by default so there is no need to flush the cache. But, if you’ve already installed it you can flush the cache by running the following command in a terminal:

```
[local]$ sudo service nscd restart 
```

Alternatively, you can try these commands:

```
[local]$ /etc/rc.d/init.d/nscd stop
[local]$ /etc/rc.d/init.d/nscd start
```

## See also

- [Flush DNS overview](https://help.dreamhost.com/hc/en-us/articles/215680477-Flush-DNS-overview)
- [Flushing your DNS cache in Windows](https://help.dreamhost.com/hc/en-us/articles/214981268-Flushing-your-DNS-cache-in-Windows)
- [How to clear your browser's cache](https://help.dreamhost.com/hc/en-us/articles/216456827-How-to-clear-your-browser-s-cache)
- [Find your macOS version](https://support.apple.com/en-us/HT201260)