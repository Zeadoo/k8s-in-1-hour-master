### Repository for the K8s in 1 hour video

# k8s-demo-app

This repository contains instructions and configuration files for deploying a Kubernetes cluster using MongoDB and a Docker container. The Docker image used for this deployment is `nanajanashia/k8s-demo-app:v1.0`.

## Prerequisites

Before deploying the Kubernetes cluster, ensure you have the following software installed:

- Kubernetes
- Docker
- kubectl

Additionally, you need an active Kubernetes cluster to deploy the application to.



#### K8s manifest files 
* mongo-config.yaml

-The "mongo-config.yaml" file is likely used to define configuration parameters and settings for MongoDB. This file allows administrators or developers to customize various aspects of MongoDB's behavior and functionality

* mongo-secret.yaml

-The "mongo-secret.yaml" file is typically used to define Kubernetes Secrets, which are a way to securely store and manage sensitive data within a Kubernetes cluster. 

* mongo.yaml

-The "mongo.yaml" file is typically a YAML configuration file used to specify various settings and parameters for the MongoDB server or client application.

* webapp.yaml

-"webapp.yaml" file is often used to define the configuration settings and parameters for a web application, specifying various aspects of its behavior, deployment, and dependencies. 


Deploying to Kubernetes
-----------------------

To deploy the application to your Kubernetes cluster, navigate to the `k8s` directory and run the following command:

```
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo.yaml
kubectl apply -f mongo-config.yaml
kubectl apply -f webapp.yaml
```
Open URL
-----------------------
To open the application in your browser

minikube service webapp-service --url


#### K8s commands

##### start Minikube and check status
    minikube start --vm-driver=hyperkit 
    minikube status

##### get minikube node's ip address
    minikube ip

##### get basic info about k8s components
    kubectl get node
    kubectl get pod
    kubectl get svc
    kubectl get all

##### get extended info about components
    kubectl get pod -o wide
    kubectl get node -o wide

##### get detailed info about a specific component
    kubectl describe svc {svc-name}
    kubectl describe pod {pod-name}

##### get application logs
    kubectl logs {pod-name}
    
##### stop your Minikube cluster
    minikube stop

<br />

> :warning: **Known issue - Minikube IP not accessible** 

If you can't access the NodePort service webapp with `MinikubeIP:NodePort`, execute the following command:
    
    minikube service webapp-service

    

<br />

#### Links
* mongodb image on Docker Hub: https://hub.docker.com/_/mongo
* webapp image on Docker Hub: https://hub.docker.com/repository/docker/nanajanashia/k8s-demo-app
* k8s official documentation: https://kubernetes.io/docs/home/
* webapp code repo: https://gitlab.com/nanuchi/developing-with-docker/-/tree/feature/k8s-in-hour



Conclusion
----------
this is just an example on how to deploy a Kubernetes cluster using a docker image
