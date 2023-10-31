# SELECTORS
Se utilizan para localizar elementos que tengan ciertas etiquetas

### BUSCAR CON SELECTORES
kubectl get pods --show-labels -l selectorName=value
kubectl get pods --show-labels -l app=tomcat,status=dev
kubectl get pods --show-labels -l status!=dev

### BUSCAR POR CONJUNTOS
kubectl get pods --show-labels -l 'estado in(dev,testing)'
kubectl get pods --show-labels -l 'status in(dev,testing)'
kubectl get pods --show-labels -l 'estado notin(dev,testing)'

### ELIMINAR POR SELECTORES
kubectl delete pods -l app=tomcat