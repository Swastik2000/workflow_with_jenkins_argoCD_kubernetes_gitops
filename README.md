# workflow with jenkins argoCD kubernetes gitops
## What this does?
This repo along with [https://github.com/Swastik2000/kubernetesmanifest](https://github.com/Swastik2000/kubernetesmanifest) creates a Jenkins pipeline with GitOps to deploy code into a Kubernetes cluster. CI part is done via Jenkins and CD part via ArgoCD (GitOps).


## Downloading and installing Jenkins on ec2

```
sudo yum update –y
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo dnf install java-11-amazon-corretto -y

sudo yum install jenkins -y

sudo systemctl enable jenkins
```

#### Starting jenkins
```
sudo systemctl start jenkins
```
#### Jenkins Status
```
sudo systemctl status jenkins
```

## Installing Minikube locally 
[https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)
```
brew install minikube
brew unlink minikube
brew link minikube
```

```
minikube start
```

## Install Argo cd
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

#### Argo CD CLI
```
brew install argocd
```

#### Access Argo CD Api server
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
