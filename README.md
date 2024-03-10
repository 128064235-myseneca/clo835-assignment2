# Assignment2

Task 1:
show the k8 cluster
```
docker ps
```
```
kubectl get all -n kube-system 
```

Task 2: Deploy mysql and app pod

```
kubectl get namespaces
```
```
kubectl apply -f mysql_pod.yaml -n database
```
```
kubectl describe pod/mysql -n database
```
```
10-244-0-13.database.pod.cluster.local
```

```
kubectl apply -f app_pod.yaml -n webapp
```

```
kubectl get all pods -n webapp
```

```
kubectl port-forward web-app 8080:8080 -n webapp
```
In the new termial
```
curl localhost:8080
```

logs
```
kubectl logs web-app -n webapp
```
```
kubectl logs mysql -n database
```

Task 3: Deploy the replica set
```
kubectl apply -f mysql_replicaset.yaml -n database
```
```
kubectl apply -f app_replicaset.yaml -n webapp
```
```
kubectl get all  -n webapp
```
```
kubectl get all  -n database
```

add the selector to the pod manifest
```
mysql-service.database.svc.cluster.local
```

```
kubectl apply -f app_pod.yaml -n webapp
```
```
kubectl apply -f mysql_pod.yaml -n database
```
```
kubectl get all  -n webapp
```
```
kubectl get all  -n database
```

Task 4: create deployment
```
kubectl apply -f app_deployment.yaml -n webapp
```
```
kubectl apply -f mysql_deployment.yaml -n database
```
```
kubectl get all  -n webapp
```
```
kubectl get all  -n database
```

Task 5: service
```
kubectl apply -f app_service.yaml -n webapp
```
```
kubectl apply -f mysql_service.yaml -n database
```
```
kubectl get all  -n webapp
```
```
kubectl get all  -n database
```

Task 6: Update Image version and deploy new version
Update the verison
```
kubectl apply -f app_deployment.yaml -n webapp --record
```
```
kubectl rollout status deployment webapp-deployment -n webapp 
```
```
kubectl rollout history deployment webapp-deployment -n webapp
```
```
kubectl get all  -n webapp
```




