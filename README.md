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
kubectl -n argo-events edit service webhook-eventsource-svc # change to nodeport
kubectl -n argo-events port-forward service/webhook-eventsource-svc 12000:12000
curl localhost:12000/hello
# https://docs.rancherdesktop.io/how-to-guides/setup-NGINX-Ingress-Controller
# Uncheck Enable Traefik from the Kubernetes Settings page to disable Traefik. You may need to exit and restart Rancher Desktop for the change to take effect.
# Deploy the NGINX ingress controller via helm or kubectl.
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.2/deploy/static/provi
```
