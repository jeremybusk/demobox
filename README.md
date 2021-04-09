# actions-lxd-docker-demo

This is a WIP

# Powerdns
- https://github.com/PowerDNS/pdns
- https://www.dnsdist.org/
- https://www.powerdns.com/recursor.html
- https://www.powerdns.com/auth.html

# CoreDNS
- https://github.com/coredns/coredns
- https://coredns.io/manual/configuration/

On linux host
```
mkdir src
cd src
git clone https://github.com/jeremybusk/demobox
cd demobox/app/coredns
cat Corefile
./start
```

# What is does
- Creates VM using LXD API
- Inits LXD, Docker and actions runner service on VM
- This will also include some examples of redundant application services like coredns

# Routing

```
sudo ip route add 192.168.0.0/16 via 10.x.x.x 
```
With 10.x.x.x being the router or entry vm)


# Or using DNAT
````
define dns_adc_port = 11053
define lxd0_adc_port = 10.x.x.x
define fip2 = 204.x.x.x

chain prerouting
    iifname "bond0" ip daddr $fip2 tcp dport 53 dnat to $lxd0_adc_ip:$dns_adc_port
    iifname "bond0" ip daddr $fip2 udp dport 53 dnat to $lxd0_adc_ip:$dns_adc_port
```

