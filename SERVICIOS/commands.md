# Servicios
ClusterIP - accesible dentro del cluster {ip, nombre, puerto}
NodePOrt - accesible desde fuera del cluster {ip, nombre, puerto, nodeport}
LoadBalancer - accesible solo desde fuera del cluster (integrado con loadbalancers de terceros)

Los servicios buscan por etiquetas/selector

## Crear servicios de forma imperativa
kubectl create deployment apache1 --image=httpd
kubectl expose deploy apache1 --port=80 --type=NodePort // Por defecto es ClusterIp

### Caso practico ClusterIP con redis
kubectl create deployment redis-master --image=redis
kubectl create deployment redis-slave --image=redis
kubectl expose deploy redis-master --port=6379 --type=ClusterIP

- Conectarse al pod de redis slave
- Abrir una conexion entre el master y el slave con : 
  - redis-cli -h redis-master

## Listar servicios
kubectl get svc

## Ver IP del cluster
minikube ip

## Endpoints
kubectl get endpoints
kubectl get endpoints web-svc -o wide
kubectl get endpoints web-svc -o yaml
kubectl describe endpoints web-svc -o wide