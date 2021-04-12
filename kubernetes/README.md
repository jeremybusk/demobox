# demo-kubernetes

A playground of kubernetes fun with examples.

# Getting Started Links
- https://kubernetes.io/docs/reference/kubectl/cheatsheet/
- https://kubernetes.io/docs/tutorials/kubernetes-basics/
- https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/

# Kubernetes Multi-Master Setup
- Hosting OS
  - Ubuntu 20.04
- Virtual Environment
  - LXD
Kubernetes 
- Kubernetes Nodes 
  - k1
  - k2
  - k3


# Examples
- postgres
- mysql
- nginx tcp proxy and http reverse proxy


Some examples
```
kubectl exec --stdin --tty postgres-5c64546cbf-tmrgl -- /bin/bash
```

Nice aliases at bottom of ~/.bashrc
```
alias kubectl='microk8s kubectl'
alias k='microk8s kubectl'
```

# Considerations

## Kubernetes Options
  - Probably use CNCF official Kubeadm but all are pretty good.
  - https://www.reddit.com/r/kubernetes/comments/be0415/k3s_minikube_or_microk8s/
  - Kubeadm - https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/

## Helm
  - I would beware of helm. Be careful what you use.
