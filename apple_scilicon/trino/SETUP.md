After following COMPUTER_SERVER_SETUP.md

# Install trino cli
```
brew install trino
```

# Add trino charts to helm
```
helm repo add trino https://trinodb.github.io/charts
```

## Install a cluter
default command
`helm install dev-trino-cluster trino/trino`

custom resource command with overrides
```
helm install -f ./trino-etl-dev.yaml dev-trino-cluster trino/trino
```

update configuration
```
helm upgrade dev-trino-cluster trino/trino --values ./trino-etl-dev.yaml
```

To uninstall
```
helm uninstall dev-trino-cluster
```

## Checking status
```
kubectl get all
```


## get pod names:
```
kubectl get pods -l "app=trino,release=dev-trino-cluster,component=coordinator" -o name
POD_NAME=$(kubectl get pods -l "app=trino,release=example-trino-cluster,component=coordinator" -o name)
```

### Kube Forward to access service
```
kubectl port-forward service/dev-trino-cluster 8080:8080
```

stoping kube forward, exit or try to kill the process
```
ps aux | grep kubectl | grep port-forward
lsof -i :8085
```

### access trino
```
trino --server http://localhost:8080
quit
```

# Reference
https://trino.io/docs/current/installation/kubernetes.html#

Trino recommends using kind


# Seecrets
Use the following to create and utilize secrets
```
kubectl get secret my-secret-name -o yaml
```
