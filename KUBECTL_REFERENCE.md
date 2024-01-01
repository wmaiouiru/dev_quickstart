

```
kubectl get namespaces
kubectl get pods --all-namespaces -o wide


kubectl get pods
kubectl get services
kubectl get deployments
```



Check pod information:
```
kubectl describe pod <pod_name>
kubectl logs 
```




# Debugging
Restart container:
```
docker image ls
docker restart <container_id>
```


# Check helm history
```
helm history <RELEASE>
helm history dev-trino-cluster
```