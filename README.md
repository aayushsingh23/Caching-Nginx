
# Caching using Nginx

I generated a backend service which renders a HTML file

It works such that if the request is made for the data withing 60 minutes, it is fetched from cache memory.

## Deploying pods and services

Deploy all the pods, configMaps and services. 

```bash
    kubectl apply -f backend.yaml
    kubectl apply -f backend-service.yaml
    kubectl apply -f backend-configMap.yaml
    kubectl apply -f deploy.yaml
    kubectl apply -f service.yaml
    kubectl apply -f configMap.yaml
```
## Start Minikube and Backend service


## Documentation

[Kubernetes](https://kubernetes.io/docs/home/)

[Minikube](https://minikube.sigs.k8s.io/docs/)

[Nginx](https://nginx.org/en/docs/)

