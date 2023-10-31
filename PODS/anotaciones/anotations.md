# ANOTACIONES
Son descriptivas y documentar nuestros componentes clave: "valor con comillas"

apiVersion: v1
kind: Pod
metadata:
  name: tomcat4
  labels:
    app: tomcat
  annotations:
    name: "cristhian villegas"
spec:
  containers:
   - name: tomcat     
     image: tomcat
  restartPolicy: Always


### COMANDO PARA BUSCAR POR ANOTACIONES
kubectl get pod tomcat4 -o jsonpath={.metadata.annotations}