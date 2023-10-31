Minikube
https://minikube.sigs.k8s.io/docs/start/

1. curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
2. sudo install minikube-linux-amd64 /usr/local/bin/minikube

COMANDOS Minikube
3. minikube version
4. minikube start --driver=docker # para local, pero baja el rendimiento al estar en contenedor
5. minikube status
5. minikube logs
5. minikube ip

 docker-env       Provides instructions to point your terminal's docker-cli to the Docker Engine inside minikube.
 
(Useful for building docker images directly inside minikube)
  podman-env       Configure environment to use minikube's Podman service
  cache            Manage cache for images
  image            Manage images

Configuration and Management Commands:
  addons           Enable or disable a minikube addon
  config           Modify persistent configuration values
  profile          Get or list the current profiles (clusters)
  update-context   Update kubeconfig in case of an IP or port change

Networking and Connectivity Commands:
  service          Returns a URL to connect to a service
  tunnel           Connect to LoadBalancer services

Advanced Commands:
  mount            Mounts the specified directory into minikube
  ssh              Log into the minikube environment (for debugging)
  kubectl          Run a kubectl binary matching the cluster version
  node             Add, remove, or list additional nodes
  cp               Copy the specified file into minikube

Troubleshooting Commands:
  ssh-key          Retrieve the ssh identity key path of the specified node
  ssh-host         Retrieve the ssh host key of the specified node
  ip               Retrieves the IP address of the specified node
  logs             Returns logs to debug a local Kubernetes cluster
  update-check     Print current and latest version number
  version          Print the version of minikube
  options          Show a list of global command-line options (applies to all commands).

Other Commands:
  completion       Generate command completion for a shell
  license          Outputs the licenses of dependencies to a directory



-- minikube profile list
-- minikube start --driver=docker -p devcluster --nodes=2  # new profile
-- minikube config set memory 3G -p minikube # cambiar propiedades del perfil, en este caso la memoria, need delete and start, be careful
-- minikube config get memory # get property
### Directorios de minikube
¬/.kube
¬/.minikube

-- cambiar de cluster
minikube profile devcluster

-- obtener los nodos de un cluster
kubectl get nodes

### MINIKUBE DASHBOARD
minikube dashboard

### CHANGE container runtime
- containerd
- cri-o
- docker
minikube start --container-runtime=cri-o -p crioCluster ### new cluster
minikube start --driver=docker --container-runtime=cri-o -p crioCluster

## Eliminar cluster
minikube delete -p profile


##### PODS
-- CREAR DE FORMA AUTOMATIC - IMPERATIVA
kubectl run nginx1 --image=nginx
kubectl run apache --image=httpd --port=8080
kubectl run apache --image=httpd --port=8080  # ????


-- listar PODS
kubectl get pods
kubectl get pods -o wide

-- DESCRIBIR PODS
kubectl describe pod/podName

-- EJECUTAR COMANDOS CONTRA UN POD
kubectl exec podname -- ls
kubectl exec podname -- ls
kubectl exec apache -it -- bash

--- MODO INTERACTIVO CON EL POD/IMAGE
kubectl exec nginx1 -it -- bash  ### nginx1 = pod name

-- LOGS 
kubectl logs podName
kubectl logs -f podName ### keep reading logs
kubectl logs apache --tail=30