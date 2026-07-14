# Kubernetes with Aru

A hands-on Kubernetes repository containing practical manifests, Helm charts, networking configurations, storage examples, and application deployments created during my Kubernetes learning journey.

This repository focuses on understanding how Kubernetes resources work together rather than only using prebuilt deployment files.

---

## Overview

The project contains Kubernetes configurations for:

* Pods
* Deployments
* ReplicaSets
* Services
* Namespaces
* ConfigMaps
* Secrets
* Jobs and CronJobs
* Persistent Volumes
* Persistent Volume Claims
* Ingress
* Horizontal Pod Autoscaling
* Kubernetes Dashboard
* Helm Charts
* Application deployments

---

## Technologies Used

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge\&logo=kubernetes\&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge\&logo=helm\&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge\&logo=docker\&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=for-the-badge\&logo=nginx\&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge\&logo=linux\&logoColor=black)
![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge\&logo=yaml\&logoColor=white)

---

## Repository Structure

```text
kubernetes-with-aru/
├── dashboard/
├── helm/
│   ├── apache-helm/
│   └── node-js-app/
├── ingress/
├── nginx/
├── storage/
├── configmaps/
├── secrets/
└── other Kubernetes manifests
```

The exact structure may continue to grow as more Kubernetes concepts and applications are added.

---

## Kubernetes Resources Covered

### Core Workloads

* Pods
* ReplicaSets
* Deployments
* Jobs
* CronJobs

### Networking

* ClusterIP Service
* NodePort Service
* Ingress
* HTTP routing
* Port forwarding

### Configuration

* ConfigMaps
* Secrets
* Environment variables
* Namespace-based isolation

### Storage

* Persistent Volumes
* Persistent Volume Claims
* Volume mounts

### Scaling

* Replica scaling
* Horizontal Pod Autoscaler

### Package Management

* Helm chart creation
* Helm templates
* Custom `values.yaml`
* Helm package generation
* Namespace-based Helm releases

---

## Helm Charts

This repository contains custom Helm charts for application deployment.

### Apache Helm Chart

```text
helm/apache-helm/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    ├── ingress.yaml
    ├── hpa.yaml
    ├── serviceaccount.yaml
    └── tests/
```

Install the Apache chart:

```bash
helm install dev-apache ./helm/apache-helm \
  --namespace dev-apache \
  --create-namespace
```

Check the release:

```bash
helm list -n dev-apache
```

Check the resources:

```bash
kubectl get all -n dev-apache
```

---

### Node.js Helm Chart

Install the Node.js application chart:

```bash
helm install dev-node-js-app ./helm/node-js-app \
  --namespace dev-node-app \
  --create-namespace
```

Check the application resources:

```bash
kubectl get pods -n dev-node-app
kubectl get svc -n dev-node-app
```

Access the application using port forwarding:

```bash
kubectl port-forward \
  svc/dev-node-js-app \
  8000:8000 \
  -n dev-node-app \
  --address=0.0.0.0
```

---

## Getting Started

### Prerequisites

Install the following tools:

* Docker
* kubectl
* Minikube or another Kubernetes cluster
* Helm
* Git

Verify the installations:

```bash
docker --version
kubectl version --client
minikube version
helm version
```

---

## Start a Local Cluster

```bash
minikube start
```

Check the cluster:

```bash
kubectl get nodes
```

---

## Deploy Kubernetes Manifests

Apply a resource:

```bash
kubectl apply -f path/to/file.yml
```

Apply all manifests from a directory:

```bash
kubectl apply -f path/to/directory/
```

Check running resources:

```bash
kubectl get pods
kubectl get deployments
kubectl get svc
```

---

## Namespace Commands

Create a namespace:

```bash
kubectl create namespace development
```

View namespaces:

```bash
kubectl get namespaces
```

View resources inside a namespace:

```bash
kubectl get all -n development
```

---

## Useful Debugging Commands

View detailed Pod information:

```bash
kubectl describe pod <pod-name> -n <namespace>
```

View application logs:

```bash
kubectl logs <pod-name> -n <namespace>
```

Follow logs continuously:

```bash
kubectl logs -f <pod-name> -n <namespace>
```

Enter a running container:

```bash
kubectl exec -it <pod-name> -n <namespace> -- /bin/sh
```

Check Helm-generated Kubernetes YAML:

```bash
helm template release-name ./helm/chart-name
```

Validate a Helm chart:

```bash
helm lint ./helm/chart-name
```

---

## Helm Release Management

List installed releases:

```bash
helm list --all-namespaces
```

Upgrade a release:

```bash
helm upgrade dev-apache ./helm/apache-helm \
  -n dev-apache
```

Uninstall a release:

```bash
helm uninstall dev-apache -n dev-apache
```

Package a chart:

```bash
helm package ./helm/apache-helm
```

---

## Learning Outcomes

Through this repository, I gained practical experience in:

* Creating Kubernetes objects using YAML
* Deploying and managing containerized applications
* Understanding Pods, Deployments, ReplicaSets, and Services
* Organizing resources using namespaces
* Exposing applications using Services and Ingress
* Managing persistent application data
* Debugging failed Pods and deployments
* Creating reusable Helm charts
* Using Helm values and templates
* Managing application releases using Helm
* Deploying applications across isolated environments

---

## Security Note

Sensitive local files are excluded from this repository.

Files such as the following should never be committed:

```text
.ssh/
.kube/
.minikube/
*.pem
*.key
*.tfstate
.env
```

Always review staged files before committing:

```bash
git status
git diff --cached
```

---

## Future Improvements

* Deploy applications on Amazon EKS
* Add Prometheus and Grafana monitoring
* Add Argo CD for GitOps-based deployments
* Add GitHub Actions CI/CD
* Add cert-manager and HTTPS
* Add Kubernetes NetworkPolicies
* Add RBAC examples
* Add production-ready Helm charts
* Add application health checks
* Add resource requests and limits
* Add automated Helm chart validation

---

## Author

**Arpit Prajapati**

GitHub: [ARPITPRAJAPATI](https://github.com/ARPITPRAJAPATI)

---

## Support

If this repository helped you understand Kubernetes, consider giving it a star.
