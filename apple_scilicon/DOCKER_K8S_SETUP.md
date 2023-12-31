# Install Docker Tools
```
brew install --cask docker
brew install colima


```
## start colima
```
colima start
colima status
docker ps
```

# Download Kubenetes tools
```
brew install kubectl
brew install minikube
brew install helm
```


# Start a cluter
```
minikube start
docker ps # check that minikube is running
```

## Check kube status
```
kubectl get pods --all-namespaces
```
### Listing the contexts
```
kubectl config get-contexts
```