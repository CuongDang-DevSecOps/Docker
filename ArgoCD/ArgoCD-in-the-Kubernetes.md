# ArgoCD in the Kubernetes

## Create ArgoCD namespace

```shell
k create namespace argocd
k config set-context --current --namespace=argocd
```

## Install ArgoCD

```shell
k apply -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.11/manifests/install.yaml
k get all
```

## Access ArgoCD

Change ClusterIP to NodePort

```shell
k edit svc argocd-service -n argocd
```

Get admin password

```shell
k get secrets argocd-initial-admin-secret -o json | jq .data.password -r | base64 -d
```

## Install CLI

```shell
wget https://github.com/argoproj/argo-cd/releases/download/v2.4.11/argocd-linux-amd64
mv argocd-linux-amd64 argocd
chmod +x argocd
mv argocd /usr/local/bin/
```
