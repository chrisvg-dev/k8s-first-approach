### GENERAR IMAGEN DSDE UN DOCKERFILE PARA USAR EN KUBERNETES
1. Tener Dockerfile creado
2. docker build -t cvillegas92/nginx:v1 .
3. docker login  // cvillegas92:Pa28d8896f9123.1992
4. docker push

### PROBAR IMAGEN
docker run -d -p 80:80 --name nginx cvillegas92/nginx:0.2.0

### CREAR RECURSO K8S DESDE FICHERO YAML
kubectl create -f nginx.yaml
kubectl apply -f multi.yaml // for pods update and best choice for creating new pods

### ELIMNINAR POD
kubectl delete pod/podName
kubectl detete pod/podName --grace-period=5 // segundos
kubectl detete pod/podName --now
kubectl delete all --all

### EXTRAER INFORMACION DE LOS RECURSOS DE K8S
1. kubectl get pod/nginx -o yaml // YAML o json
1. kubectl get pod/nginx -o yaml > podName.yaml // YAML o json

### VER LOGS DE UN POD CON 2 O MAS CONTENEDORES
kubectl logs podName -c containerName
kubectl logs -f podName -c containerName

## MULTI CONTAINER POD
### EJECUTAR COMANDOS DESDE EL BASH DEL CONTENEDOR
kubectl exec podName -c containerName -- date

### REBOTAR POD O REINICIAR POD
#### Ver yaml3
- never
- onfailure
- always // default