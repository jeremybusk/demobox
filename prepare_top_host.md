# Prepare Host for CI/CD Automation (WIP)

# Networking to support vlans

/etc/netplan/00-installer-config.yaml
````
network:
  bonds:
    bond0:
      dhcp4: yes
      interfaces:
      - enp8s0
      parameters:
        mode: balance-rr
  ethernets:
    enp8s0: {}
  version: 2
  bridges:
    brvlan2:
      interfaces: [ vlan2 ]
    brvlan3:
      interfaces: [ vlan210 ]
  vlans:
    vlan1:
      id: 1
      link: bond0
      accept-ra: no
    vlan3:
      id: 2
      link: bond0
      accept-ra: no
    vlan3:
      id: 3 
      link: bond0
      accept-ra: no

#    brvlanexample:
#      interfaces: [ vlan1 ]
#      dhcp4: no
#      dhcp6: no
#      addresses: [10.x.x.x/24]
#      gateway4: 10.x.x.1
#      nameservers:
#        search: [uvoo.io, uvoo.me]
#        addresses: [10.x.x.1]
```

Create profile with vlan2
```
lxc profile copy default actions
```

profile:actions should look something like
```
config: {}
description: Actions DMZ
devices:
  eth0:
    name: eth0
    nictype: bridged
    parent: brvlan2
    type: nic
  root:
    path: /
    pool: default
    type: disk
name: actions
```

Allow through ufw firewall if needed
```
sudo ufw allow 67,68/udp
```

```
lxc launch ubuntu:focal a1 -p actions
lxc list a1
```
