
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

Create App of Apps through Argo UI. Therefore create a new app and copy the content of argoapp.yml in.


# Tear down

```
minikube delete --all
```