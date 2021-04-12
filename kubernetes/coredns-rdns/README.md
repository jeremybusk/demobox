# Steps

NFS host fqdn nas.uvoo.io

File
```
/nas/demo-coredns-rdns/conf/Corefile
```

/etc/exports
```
...
/nas/demo-coredns-rdns    *(rw,sync,no_subtree_check,insecure)
```

You obviously would want to lock this down if needed. This is just an example.

See NFS README.md for more info on setting up server


You could also rebuild docker container, push and rebuild containers with updates in pipeline.

This is easy to do and is nice because you don't have to worry about storage beyond the container.
