# CoreDNS Recursive DNS Example

https://github.com/coredns/coredns.io/blob/master/content/blog/quick-start.md

Simple example of recursive dns server exposed on udp/tcp port 12053

Add rule complexity to do more stuff

```
dig -x 10.0.0.1 @127.0.0.1 -p 12053
nslookup -port=12053 10.0.0.1 127.0.0.1
nslookup -port=12053 host1.example.org 127.0.0.1
nslookup -port=12053 google.com 127.0.0.1
```

Increment zone file to cause to reload

```
. {
    proxy . 8.8.8.8:53 {
        protocol https_google
    }
    prometheus
    errors
    log
}
```
