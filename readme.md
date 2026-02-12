🚀 Kubernetes Bootcamp – Day 9
📌 Project Overview

In this project, I worked with Kubernetes using Minikube and kubectl.
I created deployments, services, ConfigMaps, and Secrets.
I also connected environment variables from ConfigMap and Secret into a running pod.

This project shows how Kubernetes manages containerized applications in a simple and practical way.

1️⃣ Core Concepts
Kubernetes

Kubernetes is an open-source platform used to deploy, scale, and manage containerized applications automatically.

Minikube

Minikube runs a single-node Kubernetes cluster locally or on a VM (like AWS EC2).
It is mainly used for learning and testing.

kubectl

kubectl is the command-line tool used to interact with a Kubernetes cluster.

Node

A node is a machine (virtual or physical) where Kubernetes runs applications.

Pod

A pod is the smallest unit in Kubernetes.
It can run one or more containers.

Deployment

A deployment manages pods.
It:

Keeps the desired number of replicas running

Supports scaling

Supports rolling updates

Service

A service exposes applications inside or outside the cluster.

Types of services:

ClusterIP (internal access)

NodePort (external access through node IP)

LoadBalancer (used in cloud environments)

ConfigMap

Stores non-sensitive configuration data.

Secret

Stores sensitive data like passwords and tokens.

2️⃣ kubectl Commands Used
kubectl get pods
kubectl get deploy
kubectl get svc
kubectl describe pod <pod-name>
kubectl scale deployment <name> --replicas=5
kubectl delete deployment <name>
kubectl exec -it <pod-name> -- /bin/bash

3️⃣ Apache Deployment (YAML)

I created an Apache deployment with 3 replicas.

📄 File: 

apache-deployment

This deployment:

Uses httpd:latest image

Runs 3 replicas

Exposes port 80

To apply:

kubectl apply -f apache-deployment.yaml

4️⃣ Nginx Deployment with ConfigMap and Secret
ConfigMap

📄 File: 

nginx-configmap

Stores:

WELCOME_MSG: "Hello from ConfigMap!"

Secret

📄 File: 

nginx-secret

Stores:

SECRET_MSG: "Hello from Secret!"

Nginx Deployment

📄 File: 

nginx-deployment

This deployment:

Runs 3 replicas

Uses nginx image

Reads values from ConfigMap and Secret

Injects them as environment variables

Environment variables:

WELCOME_MSG from ConfigMap

SECRET_MSG from Secret

5️⃣ Nginx Service

📄 File: 

nginx-service

This service:

Type: ClusterIP

Exposes port 80

Connects to pods with label app: aman-nginx

6️⃣ Verifying Inside the Pod

To check environment variables:

kubectl exec -it <pod-name> -- /bin/bash
echo $WELCOME_MSG
echo $SECRET_MSG
printenv


Output confirmed:

Hello from ConfigMap!
Hello from Secret!

7️⃣ What I Learned

In this project, I:

Installed and used Minikube

Used kubectl to manage resources

Created deployments with replicas

Scaled deployments

Exposed applications using services

Created ConfigMaps and Secrets

Injected environment variables into pods

Verified configurations using kubectl exec

Used YAML files for Infrastructure as Code

🎯 Conclusion

This project helped me understand how Kubernetes manages applications in a real environment.

I learned how deployments, services, ConfigMaps, and Secrets work together to create a complete application setup.
