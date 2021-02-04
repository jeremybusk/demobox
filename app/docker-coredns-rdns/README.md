# CoreDNS Recursive DNS Example

Simple example of recursive dns server exposed on udp/tcp port 12053

Add rule complexity to do more stuff

```
dig -x 10.0.0.1 @127.0.0.1 -p 12053
nslookup -port=12053 10.0.0.1 127.0.0.1
nslookup -port=12053 host1.example.org 127.0.0.1
nslookup -port=12053 google.com 127.0.0.1
```
