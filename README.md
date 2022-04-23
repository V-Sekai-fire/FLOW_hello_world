# FLOW_hello_world

1. https://rancherdesktop.io/
1. Install kubernetes with nerd.
1. Execute commands

```
kubectl create ns argo
kubectl apply -n argo -f https://raw.githubusercontent.com/argoproj/argo-workflows/stable/manifests/quick-start-postgres.yaml
kubectl -n argo port-forward deployment/argo-server 2746:2746
scoop install argo kube
kubectl get pods -n argocd
argo submit -n argo --watch https://raw.githubusercontent.com/argoproj/argo-workflows/stable/examples/hello-world.yaml
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-events/stable/manifests/install-validating-webhook.yaml
kubectl create ns argo-events
kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj/argo-events/stable/examples/event-sources/webhook.yaml
kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj/argo-events/stable/examples/sensors/webhook.yaml
kubectl -n argo port-forward deployment/argo-server 12000:12000
```
