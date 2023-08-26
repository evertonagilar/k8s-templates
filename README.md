### Instalar kind

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x kind
sudo cp kind /usr/local/bin

------------------------------------

### Instalar kubectl


### Url instalação: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/


curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl


------------------------------------

### Criar mycluster

kind create cluster --name mycluster --config mycluster-config.yaml


------------------------------------

# Usar o cluster

kubectl cluster-info --context kind-mycluster

------------------------------------

# Importar o configmap profile-replica

kubectl create configmap profile-replica --from-env-file profile-replica.env

------------------------------------

# Se precisar entrar em um pod

kubectl exec -ti nome_do_pod -- bash

------------------------------------

### Consultar os recursos de api que podemos usar e a versão para usar no apiVersion 

kubectl api-resources

------------------------------------

### Fazer undo

kubectl rollout undo deployment web-page

### Ver os pods de determinado node

k get pods -o wide --field-selector spec.nodeName=mycluster-worker2


------------------------------------

### Definir labels nos nodes

kubectl label nodes mycluster-worker2 disktype=ssd

------------------------------------

### Consultar os nodes e seus labels

kubectl nodes --show-labels


------------------------------------

### Exclui um recurso pelo arquivo yaml

kubectl delete -f apache-daemonset-worker2.yaml
