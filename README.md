# TP4 devops

A project made to practice kubernetes.

## Installation

You need to clone this repository:

```
git clone https://github.com/Ayriko/WIK-DPS-TP04.git
```

## Usage

### POD

You can launch and access the pod with the following commands :

```
kubectl apply -f my_pod.yaml
kubectl port-forward pod/api -n tp 8181:8080
```

It will be available on : 127.0.0.1:8181 (/ping)  

### REPLICASET

You can launch and access the replicaset with the following commands :

```
kubectl apply -f replica.yaml
kubectl port-forward replicaset/api -n tp 8181:8080
```

It will be available on : 127.0.0.1:8181 (/ping) 

### DEPLOYMENT

You can launch and access the deployment with the following commands :

```
kubectl apply -f deployment.yaml
kubectl port-forward replicaset/api-deployment -n tp 8181:8080
```

It will be available on : 127.0.0.1:8181 (/ping) 

### SERVICE

You can set up the service with the following command :

```
kubectl apply -f service.yaml
```

Whether you use it with the replicaset or the deployment applied, make sure that they have "app.kubernetes.io/name: api" in their template's labels.  

### INGRESS

You need the deployment and the service to be applied too.

You can set up ingress with the following commands :

```
minikube addons enable ingress (if needed)
kubectl apply -f ingress.yaml
```

You also have to edit your "/etc/hosts" with the right ip from the command : `minikube id` and the host from ingress.yaml.

The api can now be joined at : "http://your-hostame/ping"