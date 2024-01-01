# Install Docker Tools
```
brew install --cask docker
brew install colima
```

# Download Kubenetes tools
```
brew install kubectl
brew install minikube
brew install helm
```

# Start a k8s cluter
## start colima
```
colima start --cpu 8 --memory 32 --disk 100
colima status
docker ps
```

```
minikube start --memory=16384
docker ps # check that minikube is running
```

## Check kube status
```
kubectl get pods --all-namespaces
docker stats
```
# check resources used


### Listing the contexts
```
kubectl config get-contexts
kubectl get pods  -n minikube
```

### To restart minikube
```
minikube stop
minikube delete
minikube start --memory=16g
```

### Restart colima
```
colima restart
```


# Troubleshooting

```
% kubectl get all
Unable to connect to the server: net/http: TLS handshake timeout
Unable to connect to the server: net/http: TLS handshake timeout
Unable to connect to the server: net/http: TLS handshake timeout
Unable to connect to the server: net/http: TLS handshake timeout
Unable to connect to the server: net/http: TLS handshake timeout
Unable to connect to the server: net/http: TLS handshake timeout
```

1. `kubectl status`, if it hangs, we need to go up the stack
2. `minikube status`, if minikube hnags, then, we might need to restart colima
3. Restarging `colima` might be the best option if all else fails
4. If nothing is working, restart computer


# Reference
By default, Colima 24.0.7 has 2 CPUs with 2Gib memory and 60Gib stoage 
```
colima template # to check the default
```
https://github.com/abiosoft/colima/blob/main/docs/FAQ.md#setting-the-default-config