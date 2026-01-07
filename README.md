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

