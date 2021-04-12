Simple example of postgres on kubernetes with statefulsets

From kubernetes do

Start
```
./apply
./test
```

delete resources
```
./delete
```

Other methods of interacting
```
ip=$(kubectl get svc | grep "^postgres-service " | awk '{print $3}')

apt install postgres-client
psql -h 10.152.183.170 -U demouser -d demodb 

sudo microk8s.kubectl run psql -it --rm=true --image=postgres:12 --command -- psql -h $ip -U demouser demodb
```

Connect to node port or dnat to nodeport
```
psql -h 10.64.9.152 -p 31372 -U demouser -d demodb
```

Jump on container
```
kubectl exec --stdin --tty postgres-5c64546cbf-tmrgl -- /bin/bash
```

What node is it on?
```
kubectl describe pod postgres-5c64546cbf-knh8z | grep "Node: "
```

Directing traffic to Kubernetes cluster around nodeport for fun (dangerous)

routing
```
sudo ip route add 10.152.183.170(nodeport) via 10.x.x.x(kubegateway)
```

dnat
```
```


Tear down and build up
```
./delete && ./apply
```
