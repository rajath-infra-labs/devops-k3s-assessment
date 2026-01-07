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


