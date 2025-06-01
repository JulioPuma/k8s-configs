# k8s-config (Repository)
Repositorio que contiene las plantillas de los manifiestos para levantar los recursos en un cluster de K8S.

## kubectl commands
command to exec a yaml manifest
```
kubectl apply -f ./nginx-deployment.yaml
```

command to exec a yaml kustomization
```
kubectl apply -k ./
```


## Manual commands

Crear un deployment:
```
kubectl create deployment <nombre> --image=nginx
```

Exponer el servicio:
```
kubectl expose deployment <nombre> --type=NodePort --port=80
```
--type=NodePort: expone el servicio fuera del clúster en un puerto aleatorio entre 30000–32767.
--port=80: indica el puerto del contenedor (donde escucha nginx dentro del pod).

## minikube cluster

Ver configuracion
```
minikube config view
```

Ver IP del cluster
```
minikube ip
```

Dashboard
```
minikube dashboard
```

Ver puerto asignado:
```
kubectl get service <nombre-del-servicio>
```

Si el cluster esta en tu pc local, podras visualizar el servicio en:
```
http://<IP_DE_MINIKUBE>:<PUERTO_NODEPORT>
```

Si el cluster esta levantando usando WSL2 con contenedor mediante docker, entonces se tiene que ejecutar un comando adicional:
```
minikube service <nombre-del-servicio>
minikube service <nombre-del-servicio> --url
```