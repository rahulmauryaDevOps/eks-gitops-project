

# AWS EKS GitOps Project using Helm and ArgoCD

## Project Overview

This project demonstrates an end-to-end GitOps workflow on Amazon EKS using Kubernetes, Helm, and ArgoCD. The application is deployed on AWS EKS, packaged using Helm charts, and automatically synchronized from GitHub to the Kubernetes cluster using ArgoCD.

---

## Architecture

GitHub
↓
ArgoCD
↓
Helm Chart
↓
Amazon EKS
↓
Nginx Application

---

## Technologies Used

- AWS EKS
- Kubernetes
- Helm
- ArgoCD
- AWS EBS
- EBS CSI Driver
- GitHub
- kubectl

---

## Implemented Components

### Kubernetes

- Namespace
- Deployment
- ReplicaSet
- Pods
- Service
- LoadBalancer
- ConfigMap
- Secret
- PersistentVolumeClaim (PVC)
- PersistentVolume (PV)
- StorageClass

### AWS

- Amazon EKS Cluster
- Managed Node Group
- Elastic Load Balancer (ELB)
- Amazon EBS
- EBS CSI Driver
- EKS Pod Identity

### Helm

- Helm Chart Creation
- values.yaml Configuration
- Helm Install
- Helm Upgrade

### ArgoCD

- ArgoCD Installation on EKS
- GitHub Repository Integration
- Automatic Synchronization
- GitOps Workflow

---

## Project Features

- Deployed Nginx application on Amazon EKS
- Exposed application using LoadBalancer Service
- Managed application configuration using ConfigMap
- Managed sensitive data using Kubernetes Secrets
- Implemented persistent storage using PVC and AWS EBS
- Packaged application using Helm Charts
- Implemented GitOps workflow using ArgoCD
- Automated deployment updates from GitHub to EKS

---

## Troubleshooting Performed

### Issue 1: PVC Stuck in Pending State

Observed:

- PVC remained in Pending state
- Pod scheduling failed

Investigation:

- Checked PVC status using:

```bash
kubectl describe pvc nginx-pvc -n nginx-project
```

Findings:

- EBS CSI Controller was in CrashLoopBackOff state
- Storage provisioning was failing

Root Cause:

- Missing EKS Pod Identity association for EBS CSI Driver

Resolution:

- Configured EKS Pod Identity association
- Restarted EBS CSI components
- Verified EBS CSI Controller became healthy
- PVC successfully moved to Bound state

---

## Validation Commands

```bash
kubectl get pods -n nginx-project

kubectl get pvc -n nginx-project

kubectl get pv

helm list -n nginx-project

kubectl get pods -n argocd
```

## Learning Outcomes

- Kubernetes Application Deployment
- AWS EKS Administration
- Persistent Storage Management
- EBS CSI Driver Troubleshooting
- Helm Package Management
- GitOps using ArgoCD
- Production-style Kubernetes Troubleshooting