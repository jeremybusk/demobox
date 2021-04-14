https://coredns.io/plugins/dnssec/

# Generate key pair
```
sudo apt install bind9-utils
dnssec-keygen -a ECDSAP256SHA256 example.com
```
You can use same key on multiple domains or just one

```
dig @8.8.8.8 www.example.org. A +dnssec +multiline

dig @127.0.0.1  www.isc.org. A +dnssec +multiline -p 153
```
