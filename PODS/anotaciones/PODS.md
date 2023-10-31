##### PODS
-- CREAR DE FORMA AUTOMATIC - IMPERATIVA
kubectl run nginx1 --image=nginx
kubectl run apache --image=httpd --port=8080
kubectl run apache --image=httpd --port=8080  # ????

## listar PODS
kubectl get pods
kubectl get pods -o wide

## DESCRIBIR PODS
kubectl describe pod/podName

## EJECUTAR COMANDOS CONTRA UN POD
kubectl exec podname -- ls
kubectl exec podname -- ls
kubectl exec apache -it -- bash

## MODO INTERACTIVO CON EL POD/IMAGE
kubectl exec nginx1 -it -- bash  ### nginx1 = pod name

## LOGS 
kubectl logs podName
kubectl logs -f podName ### keep reading logs
kubectl logs apache --tail=30

### PROBAR PODS CON KUBECTL PROXY ASI SE PUEDE VER DESDE EL NAVEGADOR
kubectl proxy // muestra un json con todas las cosas declaradas en k8s
http://localhost:8001/api/v1
http://localhost:8001/api/v1/namespaces
http://localhost:8001/api/v1/namespaces/default/pods
http://localhost:8001/api/v1/namespaces/default/pods/podName
http://localhost:8001/api/v1/namespaces/default/pods/podName/proxy ### deja ver la ejecucion del pod


### CREAR SERVICIO PARA EXPONER PODS
kubectl get services
kubectl get svc
kubectl delete svc/svcName
kubectl expose pod podName --port=80 --name=nginx-svc --type=LoadBalancer // PARA DOCKER DESKTOP USAR NodePort, LOADBALANCER AYUDA A REDIRIGIR
minikube ip // acceder LA IP de minikube DESDE EL PUERTO EXPUESTO POR EL SERVICIO

### EXPONER POR PORT FORWARDING
kubectl port-forward nginx 9999:80  // 9999 local 80 docker/remoto, se usa localhost para acceder

### VER PODS DESDE UN NODO CLUSTER
minikube ssh // o lo que esten usando
docker ps // para ver lo que hay en el docker del cluster
ps -ef