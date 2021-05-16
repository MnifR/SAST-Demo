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
user@hostname:~$ kind create cluster --config kind-cluster.yaml
user@hostname:~$ vim kind-cluster.yaml
user@hostname:~$ grep server ~/.kube/config

```
## Install metalLB

```shell
user@hostname:~$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/namespace.yaml
user@hostname:~$ kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
user@hostname:~$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/metallb.yaml
user@hostname:~$ which kind
user@hostname:~$ kind version
user@hostname:~$ kind create cluster --config kind-cluster.yaml
user@hostname:~$ vim kind-cluster.yaml
user@hostname:~$ grep server ~/.kube/config

```
## Contributing

Please read through our [contributing guidelines](https://reponame/blob/master/CONTRIBUTING.md). Included are directions for opening issues, coding standards, and notes on development.

Moreover, all HTML and CSS should conform to the [Code Guide](https://github.com/mdo/code-guide), maintained by [Main author](https://github.com/usernamemainauthor).

Editor preferences are available in the [editor config](https://reponame/blob/master/.editorconfig) for easy use in common text editors. Read more and download plugins at <https://editorconfig.org/>.

## Creators

**Creator 1**

- <https://github.com/usernamecreator1>

## Thanks

Some Text

## Copyright and license

Code and documentation copyright 2011-2018 the authors. Code released under the [MIT License](https://reponame/blob/master/LICENSE).

Enjoy :metal:
