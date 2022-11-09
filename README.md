
# Prerequisites

- minikube
- docker, kubectl, ...
- direnv

# Setup

Create K8s cluster:
```
minikube start
```

Install ArgoCD:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

PortForward to ArgoUi:

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```


# Tear down

```
minikube delete --all
```