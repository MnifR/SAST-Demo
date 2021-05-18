<p align="center">
  <a href="https://example.com/">
    <img src="https://via.placeholder.com/72" alt="Logo" width=72 height=72>
  </a>

  <h3 align="center">Logo</h3>

  <p align="center">
    Short description
    <br>
    <a href="https://reponame/issues/new?template=bug.md">Report bug</a>
    ·
    <a href="https://reponame/issues/new?template=feature.md&labels=feature">Request feature</a>
  </p>
</p>


## Table of contents

- [Quick start](#quick-start)
- [Status](#status)
- [What's included](#whats-included)
- [Bugs and feature requests](#bugs-and-feature-requests)
- [Contributing](#contributing)
- [Creators](#creators)
- [Thanks](#thanks)
- [Copyright and license](#copyright-and-license)


## Install ZSH,tmux, neofetch and Oh-My-ZSH framework

```shell
user@hostname:~$ bash <(wget -nv -O - https://gist.githubusercontent.com/MnifR/7d0dcdb0ec1a6351cd05f7cca71c8b2a/raw/47232232a5ecee4636fd68eb7c77f24d3af76a0b/install-zsh.sh)
```

## Install Docker CE

Install Docker CE 

```shell
user@hostname:~$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
user@hostname:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
user@hostname:~$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
user@hostname:~$ sudo apt update
user@hostname:~$ sudo apt install docker-ce
user@hostname:~$ sudo systemctl status docker
user@hostname:~$ sudo usermod -aG docker ${USER}
```

## Install Kubectl

```shell
user@hostname:~$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
user@hostname:~$ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
user@hostname:~$ sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
user@hostname:~$ echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
user@hostname:~$ sudo apt-get update
user@hostname:~$ sudo apt-get install -y kubectl
user@hostname:~$ kubectl version

```

## Install Helm 3

```shell
user@hostname:~$ curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
user@hostname:~$ echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
user@hostname:~$ sudo apt-get update
user@hostname:~$ sudo apt-get install helm
user@hostname:~$ helm version --short
```

## Install Kind

```shell
user@hostname:~$ curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.10.0/kind-linux-amd64
user@hostname:~$ chmod +x ./kind
user@hostname:~$ sudo mv ./kind /usr/local/bin/kind
user@hostname:~$ which kind
user@hostname:~$ kind version
user@hostname:~$ kind create cluster --name demo
user@hostname:~$ kind get clusters
user@hostname:~$ k get nodes
user@hostname:~$ grep server ~/.kube/config

```
## Install metalLB

```shell
user@hostname:~$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/namespace.yaml
user@hostname:~$ kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
user@hostname:~$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/metallb.yaml
user@hostname:~$ kubectl get pods -n metallb-system --watch
user@hostname:~$ k -n metallb-system get all
user@hostname:~$ docker network inspect -f '{{.IPAM.Config}}' kind
user@hostname:~$ vim metallb-conf.yaml
user@hostname:~$ k create -f metallb-conf.yaml
------------- TEST Metal LB--------------
user@hostname:~$ k create deploy nginx --image nginx
user@hostname:~$ k get pods -w
user@hostname:~$ k expose deploy nginx --port 80 --type LoadBalancer
user@hostname:~$ k create deploy nginx --image nginx
user@hostname:~$ k get all
```
## Install Jenkins with helm

```shell
user@hostname:~$ helm repo add jenkins https://charts.jenkins.io
user@hostname:~$ helm repo update
user@hostname:~$ wget https://raw.githubusercontent.com/jenkinsci/helm-charts/main/charts/jenkins/values.yaml
user@hostname:~$ code .
user@hostname:~$ k create ns jenkins
user@hostname:~$ helm install jenkins jenkins/jenkins -f values.yaml
user@hostname:~$ k -n jenkins get all -w
user@hostname:~$ k -n jenkins get secret jenkins -o yaml
user@hostname:~$ kubectl exec --namespace jenkins -it svc/jenkins -c jenkins -- /bin/cat /run/secrets/chart-admin-password && echo

```

## Install Sonarqube with helm

```shell
user@hostname:~$ helm repo add oteemocharts https://oteemo.github.io/charts
user@hostname:~$ helm repo update
user@hostname:~$ k create ns sonarqube
user@hostname:~$ helm install sonarqube --namespace sonarqube  oteemocharts/sonarqube -f values.yaml
user@hostname:~$ k -n sonarqube get all -w
user@hostname:~$ k -n sonarqube logs
user@hostname:~$ k -n jenkins get all -w

```

## Install Lens UI 

```shell
user@hostname:~$ wget https://github.com/lensapp/lens/releases/download/v4.2.4/Lens-4.2.4.amd64.deb
user@hostname:~$ sudo dpkg -i Lens-4.2.4.amd64.deb
```

## Copyright and license

