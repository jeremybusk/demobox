Example of Kubernetes with mysql from url below

https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/


```
# ip=$(kubectl get svc | grep "^mysql " | awk '{print $3}')
ip=$(kubectl get pod -o wide | grep "^mysql-" | awk '{print $6}')
mysql -ppassword -h $ip 
```

 kubectl get pods -o wide -l app=mysql | awk '{print $6}'
