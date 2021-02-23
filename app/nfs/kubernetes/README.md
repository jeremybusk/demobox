nfs server centos 8 with hostname nas in dns
```
sudo dnf install nfs-utils
systemctl enable --now nfs-server
systemctl status nfs-server
```

/etc/exports
```
# var/nfs 10.x.x.x/32(rw,sync,no_subtree_check,insecure) 10.x.x.x/32(rw,sync,no_subtree_check,insecure) 10.x.x.x/32(rw,sync,no_subtree_check,insecure)
/nas/share    *(rw,sync,no_subtree_check,insecure)
/nas/direct    *(rw,sync,no_subtree_check,insecure)
```

ubuntu kubunernetes hosts 
```
apt install -y nfs-client
mkdir -p /share
echo "nas:/nas/share  /share  nfs" >> /etc/fstab
mount -a
```

Create, View, Delete
```
kubectl -f x1.yml
kubectl get pod x1
kubectl delete -f x1.yml
```

In container is limited because of readonly
```
kubectl exec ...
mkdir /share
root@jnfs:/# mount -t nfs nas:/nas/share /share
mount: /share: cannot mount nas:/nas/share read-only.
```

```
mount -t nfs nas:/nas/share /tmp/s
```

```
kubectl get events
kubectl get demo-nfs-mount
```
