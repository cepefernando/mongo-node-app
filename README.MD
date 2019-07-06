# Deploying MongoDB on K8s

Deploys a MongoDB and a Node API application in a K8s cluster.

1 - Create the namespace

```
kubectl apply -f namespace.yaml
```

2 - Configure kubectl to work on the recently created namespace. Assuming you are already connected to a running k8s you just need to modify the `current-context` (kubectl config current-context). The objects in the YAML files have already the namespace object but we run this in order to manipulate them without adding the `--namespace` everytime we run `kubectl`	

```
kubectl config set-context CLUSTER_CONTEXT --namespace dubai
```

3 - Create the MongoDB instance

```
kubectl apply -f mongodb.yaml
```

4 - Create the Node API application

```
kubectl apply -f nodeapi.yaml
```

5- Once you are done with above mentioned steps, do check if these endpoints are working properly:
- GET - /users - retrieve users from MongoDB
- POST - /users - create new user