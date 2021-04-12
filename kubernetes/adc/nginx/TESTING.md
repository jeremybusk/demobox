# Testing 

# Netcat

If rate limiting to 1 connection you can open two tcp connections with netcat from client and see that it will drop the second connection
```
apt install netcat

nc adc 9002
nc adc 9002
```

# Nmap
```
sudo nmap -sS -n -p 9002 adc
```

# TCPDUMP
```
tcpdump -nnpi eth0 tcp[13]==2
tcpdump -nnpi eth0 port 9002
```

# TSHARK
````
tshark -i 1 -f "port 53" -Y "dns"
tshark -i internal -f "host 192.168.x.x and port 25" -Y "smtp.req" # https://www.wireshark.org/docs/dfref/s/smtp.html
tshark -i eth0 -f "host 10.x.x.x and tcp port 80 or port 8080" -Y "http.request || http.response"
tshark -i ens160 -f "proto 47" -d ip.proto==47,gre -q -z sip,stat
tshark -l -i eth0 -f 'dst port ( 80 or 8054 or 443 or 993 ) ' -Y 'ssl.handshake.extension.type == "server_name" || http.host' -T fields -e ip.src -e ip.dst -e tcp.dstport -e ssl.handshake.extensions_server_name -e http.host
```

# DIG

