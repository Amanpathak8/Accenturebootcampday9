# 🚀 Kubernetes Bootcamp -- Day 9 Project

## 📌 Project Overview

In this project, I worked with Kubernetes using Minikube and kubectl. I
created deployments, services, ConfigMaps, and Secrets. I also connected
environment variables from ConfigMap and Secret inside a running Nginx
pod.

This project helped me understand how Kubernetes manages containerized
applications in a practical way.

------------------------------------------------------------------------

## 🏗️ Technologies Used

-   Kubernetes
-   Minikube
-   kubectl
-   Docker Images (nginx, httpd)
-   YAML (Infrastructure as Code)

------------------------------------------------------------------------

## 📂 Project Files

### 1️⃣ Apache Deployment

-   Uses `httpd:latest`
-   Runs 3 replicas
-   Exposes container port 80

Apply with:

kubectl apply -f apache-deployment.yaml

------------------------------------------------------------------------

### 2️⃣ Nginx ConfigMap

Stores non-sensitive configuration:
metadata:
  name: aman-nginx-config

WELCOME_MSG: "Hello from ConfigMap!"

------------------------------------------------------------------------

### 3️⃣ Nginx Secret

Stores sensitive data:

SECRET_MSG: "Hello from Secret!"

------------------------------------------------------------------------

### 4️⃣ Nginx Deployment

-   Uses `nginx` image
-   Runs 3 replicas
-   Reads values from ConfigMap and Secret
-   Injects them as environment variables

Environment variables used:

-   WELCOME_MSG (from ConfigMap)
-   SECRET_MSG (from Secret)

Apply with:

kubectl apply -f nginx-deployment.yaml

------------------------------------------------------------------------

### 5️⃣ Nginx Service

-   Type: ClusterIP
-   Exposes port 80
-   Connects to pods with label `app: aman-nginx`

Apply with:

kubectl apply -f nginx-service.yaml

------------------------------------------------------------------------

## 🖥️ Important kubectl Commands Used

kubectl get pods kubectl get deploy kubectl get svc kubectl describe pod
`<pod-name>`{=html} kubectl scale deployment `<name>`{=html}
--replicas=5 kubectl delete deployment `<name>`{=html} kubectl exec -it
`<pod-name>`{=html} -- /bin/bash

------------------------------------------------------------------------

## 🔍 Verifying ConfigMap and Secret

To verify environment variables inside the pod:

kubectl exec -it `<pod-name>`{=html} -- /bin/bash echo \$WELCOME_MSG
echo \$SECRET_MSG printenv

Output confirmed:

Hello from ConfigMap! Hello from Secret!

------------------------------------------------------------------------

## 📚 What I Learned

-   How to create and manage deployments
-   How to scale applications
-   How services expose applications
-   How ConfigMap stores configuration
-   How Secret stores sensitive data
-   How to inject environment variables into pods
-   How Kubernetes automatically manages replicas
-   How to use YAML for Infrastructure as Code

------------------------------------------------------------------------

## 🎯 Conclusion

This project helped me understand the core concepts of Kubernetes. I
learned how deployments, services, ConfigMaps, and Secrets work together
to run containerized applications efficiently.
