# Example Using NGINX as your inbound proxy

/etc/nginx/nginx.conf
```
...
stream {
  include /etc/nginx/conf.d/*.stream;
}`
http {
...
```


/etc/nginx/conf.d/demodb.stream
```
upstream k_demodb {
  least_conn;
  server k1:31372;  # k1 - different master kubernetes nodes with exposed port
  server k2:31372;  # k2
  server 10.x.x.c:31372;  # k3
  # fail_timeout=5s, weight=5, backup, slow_start=30s, max_fails=3 fail_timeout=30s(default is 1 attempt),
  # https://docs.nginx.com/nginx/admin-guide/load-balancer/http-health-check/
}
server {
  listen 9001; # port that outside world will actually connect to our application. We can set session controls from here.
  proxy_pass k_demodb;
}
```


Pcap to watch connections and proxy weight settings
```
tcpdump -npi eth0 port 31372 and tcp[13]==2
```

From outside world you could use keepalived or BGP/OSPF for healthy node ip routing.
