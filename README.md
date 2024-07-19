
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
## Start Minikube and Test Cache

```bash
    minikube tunnel
```
```bash
    kubectl get svc cache-service
```

Get external IP and test if data is served through cache
```bash
    $response = Invoke-WebRequest -Uri http://<external-ip> -UseBasicParsing
    $response.Headers
```
External ip must be like `127.0.0.1`

You should see the `X-Cache` headers indicating cache `hits` and `misses`, and the content should be served from the backend service.

When you do it once `X-Cache` will show `miss` as it is the first time and cache isn't saved yet. After that it must show `hit` as the cache is saved and now data is served via cache.

After 60 mins of no requests, the cache memory gets reset and now it will again show `miss`.
## Documentation

[Kubernetes](https://kubernetes.io/docs/home/)

[Minikube](https://minikube.sigs.k8s.io/docs/)

[Nginx](https://nginx.org/en/docs/)

