# EDITAR DEPLOYMENT
kubectl edit deploy name

# Escalado de deployments
kubectl scale deploy nginx-d --replicas=5
kubectl scale deploy -l status=1 --replicas=10
