## Install Steps In Ubuntu 20.04


## Install ZSH,tmux, neofetch and Oh-My-ZSH framework (OPTIONAL)

```shell
bash <(wget -nv -O - https://gist.githubusercontent.com/MnifR/7d0dcdb0ec1a6351cd05f7cca71c8b2a/raw/47232232a5ecee4636fd68eb7c77f24d3af76a0b/install-zsh.sh)
```

## Install Docker CE

Install Docker CE 

```shell
sudo apt install apt-transport-https ca-certificates curl software-properties-common
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install docker-ce
sudo systemctl status docker
sudo usermod -aG docker ${USER}
```

## Install Kind

```shell
sudo curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.10.0/kind-linux-amd64
sudo chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
which kind
kind version
sudo kind create cluster --name demo
sudo kind get clusters
sudo kubectl get nodes
sudo grep server ~/.kube/config

```
## Install Kubectl

```shell
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
kubectl version

```

## Install Helm 3

```shell
sudo curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
helm version --short
```

## Install metalLB

```shell
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/namespace.yaml
kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/metallb.yaml
kubectl get pods -n metallb-system --watch
kubectl -n metallb-system get all
docker network inspect -f '{{.IPAM.Config}}' kind
vim metallb-conf.yaml
kubectl create -f metallb-conf.yaml
------------- TEST Metal LB--------------
kubectl create deploy nginx --image nginx
kubectl get pods -w
kubectl expose deploy nginx --port 80 --type LoadBalancer
kubectl get all
```
## Install Jenkins with helm

```shell
helm repo add jenkins https://charts.jenkins.io
helm repo update
wget https://raw.githubusercontent.com/jenkinsci/helm-charts/main/charts/jenkins/values.yaml
vim values.yaml
kubectl create ns jenkins
helm install jenkins --namespace jenkins jenkins/jenkins -f values.yaml
kubectl -n jenkins get all
kubectl -n jenkins get secret jenkins -o yaml

```

## Install Sonarqube with helm

```shell
helm repo add oteemocharts https://oteemo.github.io/charts
helm repo update
kubectl create ns sonarqube
wget https://raw.githubusercontent.com/MnifR/SAST-Demo/master/sonarqube/values.yaml
helm install sonarqube --namespace sonarqube  oteemocharts/sonarqube -f values.yaml
kubectl -n sonarqube get all

```

## Install Lens UI 

```shell
wget https://github.com/lensapp/lens/releases/download/v4.2.4/Lens-4.2.4.amd64.deb
sudo dpkg -i Lens-4.2.4.amd64.deb
```
