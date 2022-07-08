## apiVersions

| kind                  | apiVersion                   |
| --------------------- | ---------------------------- |
| Pod                   | v1                           |
| ReplicaSet            | apps/v1                      |
| Deployment            | apps/v1                      |
| Job                   | batch/v1                     |
| CronJob               | batch/v1                     |
| Service               | v1                           |
| Ingress               | networking.k8s.io/v1         |
| NetworkPolicy         | networking.k8s.io/v1         |
| PersistentVolume      | v1                           |
| PersistentVolumeClaim | v1                           |
| Role                  | rbac.authorization.k8s.io/v1 |
| RoleBinding           | rbac.authorization.k8s.io/v1 |
| ClusterRole           | rbac.authorization.k8s.io/v1 |
| ClusterRoleBinding    | rbac.authorization.k8s.io/v1 |

---

## Set namespace
```
kubectl config set-context --current --namespace=<namespace>
```

## Delete and re-create a pod
```
kubectl replace --force -f <file>
```

## View logs for a container
```
kubectl logs    <pod> -c <container>  # view
kubectl logs -f <pod> -c <container>  # stream
```

## Filter pods by label
```
kubectl get pods -l         key1=value1,key2=value2
kubectl get pods --selector key1=value1,key2=value2
```

## Update deployment image
```
kubectl set image deployment dep_name container_name=image_name
```

## Managing rollouts for deployments
```
kubectl rollout status  deployment/deployment_name
kubectl rollout history deployment/deployment_name [--revision=revision_num]
kubectl rollout undo    deployment/deployment_name
```

## Recording rollout change-causes
Add `--record` to any modification commands. E.g.
```
kubectl set image ...         --record
kubectl create deployment ... --record
kubectl edit deployment ...   --record
```

## Create service for a deployment
```
kubectl expose deployment <deployment> --name <service-name> --port <port> --target-port <target-port> --type <NodePort/ClusterIP/LoadBalancer>
```

## Check your own permissions
```
kubectl auth can-i <verb> <resource>
kubectl auth can-i delete nodes  # example
```

## Check another user's permissions
```
kubectl auth can-i <verb> <resource> --as <user>
```
