# Réaliser la création d'un cluster Kubernetes permettant, via un LoadBalancer, d'atteindre 6 replicas d'une application de type site Web

Creer un fichier README.md expliquant les étapes à suivre suite à un clone / pull de votre projet pour créer un cluster K8s comprenent les 6 replicas de votre application et atteignable via un tunnel sur minikube


## Installation du projet : 

```
git init
```
```
git clone https://github.com/marue59/cluster_kubernetes.git
```

## Comment créer l'image sur son PC :

```
docker pull dockerfile/nginx
```
```
docker build -t exo-nginx .
```
```
docker run --name my-custom-nginx-container -d -p 8080:80 exo-nginx
```
## Création de l'image sur Dockerhub aprés avoir crée un repository

```
docker build -t 0811198720119005/exo-nginx .
```
```
docker tag 0811198720119005/exo-nginx new-repo:0811198720119005
```
```
docker login
```
```
docker push 0811198720119005/exo-nginx
```

## Création du cluster K8s : 

``` 
minikube start 
```
```
kubectl create deployment nginx--second-deployment --image 0811198720119005/exo-nginx
```
```
kubectl get deployment
```
```
kubectl get pod
```

### Création du service :

```
kubectl expose deployment/nginx--second-deployment --type LoadBalancer --port 80
```
```
kubectl get svc
```
```
 minikube service nginx--second-deployment
```

### Ajout de replicas :

```
kubectl scale deployment/nginx--second-deployment --replicas 6 
```
```
kubectl get pods
```
```
minikube service nginx--second-deployment 
```

## Minikube ++ 

[![Actions Status](https://github.com/kubernetes/minikube/workflows/build/badge.svg)](https://github.com/kubernetes/minikube/actions)
[![GoReport Widget]][GoReport Status]
[![GitHub All Releases](https://img.shields.io/github/downloads/kubernetes/minikube/total.svg)](https://github.com/kubernetes/minikube/releases/latest)
[![Latest Release](https://img.shields.io/github/v/release/kubernetes/minikube?include_prereleases)](https://github.com/kubernetes/minikube/releases/latest)
 

[GoReport Status]: https://goreportcard.com/report/github.com/kubernetes/minikube
[GoReport Widget]: https://goreportcard.com/badge/github.com/kubernetes/minikube

<img src="https://github.com/kubernetes/minikube/raw/master/images/logo/logo.png" width="100" alt="minikube logo">

Minikube implémente un cluster Kubernetes local sur macOS, Linux et Windows. [Les principaux objectifs](https://minikube.sigs.k8s.io/docs/concepts/principles/) de minikube sont d'être le meilleur outil pour le développement d'applications Kubernetes locales et de prendre en charge toutes les fonctionnalités Kubernetes qui conviennent.

<img src="https://raw.githubusercontent.com/kubernetes/minikube/master/site/static/images/screenshot.png" width="575" height="322" alt="screenshot">

## Caracteristiques

Minikube exécute la dernière version stable de Kubernetes, avec prise en charge des fonctionnalités standard de Kubernetes telles que :


* [LoadBalancer](https://minikube.sigs.k8s.io/docs/handbook/accessing/#loadbalancer-access) - `minikube tunnel`
* Multi-cluster -  `minikube start -p <name>`
* NodePorts -  `minikube service`
* [Dashboard](https://minikube.sigs.k8s.io/docs/handbook/dashboard/) - `minikube dashboard`
* [Container runtimes](https://minikube.sigs.k8s.io/docs/handbook/config/#runtime-configuration) - `minikube start --container-runtime`


En plus des fonctionnalités conviviales pour les développeurs :

* [Addons](https://minikube.sigs.k8s.io/docs/handbook/deploying/#addons) - un marché permettant aux développeurs de partager des configurations pour exécuter des services sur minikube
* [NVIDIA GPU support](https://minikube.sigs.k8s.io/docs/tutorials/nvidia_gpu/) - pour l'apprentissage automatique
* [Filesystem mounts](https://minikube.sigs.k8s.io/docs/handbook/mount/)

**Pour plus d'informations, consultez le [minikube site officiel](https://minikube.sigs.k8s.io)**

## Installation

Voir le [Guide de démarrage](https://minikube.sigs.k8s.io/docs/start/)

## Documentation

Voir https://minikube.sigs.k8s.io/docs/

