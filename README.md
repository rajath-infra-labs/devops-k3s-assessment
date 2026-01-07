# devops-k3s-assessment

# Infrastructure DevOps Intern Assessment

## Part 1: VM & Cluster Setup

### Docker Installation
**Commands:**
```bash
apt update && apt upgrade -y
apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt update
apt install -y docker-ce docker-ce-cli containerd.io
systemctl enable docker
systemctl start docker

## Validation:

docker version
docker ps

<img width="734" height="546" alt="image" src="https://github.com/user-attachments/assets/d57472d1-2444-4bec-b588-69b644a261c1" />

## k3s Installation

kubectl get nodes
kubectl get all -n openwebui

Commands:

curl -sfL https://get.k3s.io | sh -
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
kubectl get nodes
kubectl get pods -A

<img width="755" height="511" alt="image" src="https://github.com/user-attachments/assets/fdd0a04c-3607-4580-8cef-89eb9a1c83d6" />

kubectl get nodes
  kubectl get all -n openwebui
root@hgrajath123:~# kubectl get nodes
  kubectl get all -n openwebui
NAME          STATUS   ROLES           AGE    VERSION
hgrajath123   Ready    control-plane   151m   v1.34.3+k3s1
NAME                                       READY   STATUS    RESTARTS   AGE
pod/open-webui-0                           1/1     Running   0          133m
pod/open-webui-ollama-5d99896fd7-6fqlj     1/1     Running   0          133m
pod/open-webui-pipelines-7d8757f9c-wb8v9   1/1     Running   0          133m
pod/open-webui-redis-c47dbfbcd-cb2x9       1/1     Running   0          133m

NAME                           TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)     AGE
service/open-webui             ClusterIP   10.43.21.32    <none>        80/TCP      133m
service/open-webui-ollama      ClusterIP   10.43.214.38   <none>        11434/TCP   133m
service/open-webui-pipelines   ClusterIP   10.43.21.108   <none>        9099/TCP    133m
service/open-webui-redis       ClusterIP   10.43.130.31   <none>        6379/TCP    133m

NAME                                   READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/open-webui-ollama      1/1     1            1           133m
deployment.apps/open-webui-pipelines   1/1     1            1           133m
deployment.apps/open-webui-redis       1/1     1            1           133m

NAME                                             DESIRED   CURRENT   READY   AGE
replicaset.apps/open-webui-ollama-5d99896fd7     1         1         1       133m
replicaset.apps/open-webui-pipelines-7d8757f9c   1         1         1       133m
replicaset.apps/open-webui-redis-c47dbfbcd       1         1         1       133m

NAME                          READY   AGE
statefulset.apps/open-webui   1/1     133m

---------------

debugging
got syntax error in yaml file, changes usage of space to tab.
it do nothave ocid complete requirement like id, password,domain name in issuer so after opening the web it will should crashloopback off .currently everything was in running state after using tab so no fix needed for pod.

used log checking command while debugging.

also below is all command used history:
history
    1  apt update && apt upgrade -y
    2  curl -fsSL https://get.docker.com | sh
    3  sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
    4  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    5  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    6  sudo apt update
    7  sudo apt install -y docker-ce docker-ce-cli containerd.io
    8  sudo systemctl start docker
    9  sudo systemctl enable docker
   10  sudo usermod -aG docker $USER
   11  newgrp docker
   12  docker version
   13  docker ps
   14  curl -sfL https://get.k3s.io | sh -
   15  sudo systemctl status k3s
   16  mkdir -p $HOME/.kube
   17  sudo cp /etc/rancher/k3s/k3s.yaml $HOME/.kube/config
   18  sudo chown $(id -u):$(id -g) $HOME/.kube/config
   19  kubectl get nodes
   20  kubectl get pods -A
   21  curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
   22  helm repo add open-webui https://helm.openwebui.com/
   23  helm repo update
   24  helm install --dry-run --debug webui open-webui/open-webui --namespace openwebui --set service.type=ClusterIP
   25  kubectl get all -n openwebui
   26  kubectl create namespace openwebui
   27  helm install webui open-webui/open-webui --namespace openwebui --set service.type=ClusterIP
   28  kubectl create namespace openwebui
   29  helm install webui open-webui/open-webui --namespace openwebui --set service.type=ClusterIP
   30  kubectl create namespace openwebui
   31  kubectl get all -n openwebui
   32  kubectl get nodes
   33  docker version
   34  docker ps
   35  exit
   36  ls
   37  exit
   38  du
   39  kubectl get nodes
   40  helm install webui open-webui/open-webui --namespace openwebui --set service.type=ClusterIP
   41  curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
   42  history

