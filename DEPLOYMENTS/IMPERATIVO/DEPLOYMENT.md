# IMPERATIVO

### CREAR DEPLOYMENT
kubectl create deployment name --image=httpd

### VER DESPLIEGUES DE DEPLOYMENTS
kubectl get deploy
kubectl get replicaset // Ver pods deseados, actuales y listos
kubectl get pods
kubectl describe deployment/name
kubectl get deploy apache -o yaml
