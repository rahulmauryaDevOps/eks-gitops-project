# EKS GitOps Project

This project demonstrates deployment of applications on AWS EKS using Kubernetes.

## Technologies Used

- AWS EKS
- Kubernetes
- kubectl
- GitHub

## Project Components

- Namespace
- Deployment
- Service

## Future Enhancements

- ConfigMap
- Secret
- PVC
- Helm
- ArgoCD
- HPA

## Project Features

- AWS EKS Cluster
- Kubernetes Deployment
- LoadBalancer Service
- ConfigMap Integration
- Secret Integration

## Troubleshooting:
- PVC remained in Pending state.
- Investigated using kubectl describe pvc.
- Identified EBS CSI controller CrashLoopBackOff.
- Root cause was IAM permission issue for EBS CSI driver.

Implemented persistent storage using PersistentVolumeClaim (PVC) and dynamically provisioned AWS EBS volumes. Troubleshot EBS CSI Driver CrashLoopBackOff caused by missing EKS Pod Identity association and successfully restored storage provisioning.
