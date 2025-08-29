## Build images locally and push to registry (from project root):


```
docker build -t abhi25022004/users:1.0 ./users
docker push abhi25022004/users:1.0

docker build -t abhi25022004/posts:1.0 ./posts
docker push abhi25022004/posts:1.0

docker build -t abhi25022004/api-gateway:1.0 ./api-gateway
docker push abhi25022004/api-gateway:1.0

docker build -t abhi25022004/frontend:1.0 ./frontend
docker push abhi25022004/frontend:1.0
```

## Update images in K8s manifests (your-registry/...) to your pushed image names.

## Apply manifests:

```
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/configmap.yaml -n microapp
kubectl apply -f k8s/secret.yaml -n microapp
kubectl apply -R -f k8s/deployments -n microapp
kubectl apply -R -f k8s/services -n microapp
```

## On Minikube, access frontend:
```
minikube service frontend-svc -n microapp
```