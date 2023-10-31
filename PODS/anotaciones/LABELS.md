### LABELS
kubectl get pod tomcat --show-labels
kubectl get pod tomcat --show-labels -L tagName


#### MODO IMPERATIVO
### Agregar etiqueta
kubectl label pod tomcat responsable=cristhian
kubectl label --overwrite pod/tomcat responsable=cvillegas

### ELIMINAR ETIQUETA
kubectl label pod/tomcat responsable-

#### MODO DECLARATIVO