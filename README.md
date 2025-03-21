# WordPress Deployment with Helm Chart & ArgoCD

## Overview

This project automates the deployment of WordPress across three environments (**dev, staging, and prod**) using **Helm** and **ArgoCD**. With this setup, changes to configuration files in a Git repository automatically sync with the Kubernetes cluster.

## Prerequisites

Before setting up ArgoCD with Helm, ensure you have:

- A Kubernetes cluster (Minikube, EKS, GKE, AKS, etc.)
- Helm installed ([Install Helm](https://helm.sh/docs/intro/install/))
- ArgoCD installed ([Install ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started/))
- A Git repository for storing Helm values files

## Installation Steps

### 1. Install ArgoCD

Check if ArgoCD is running:

### 2. Expose ArgoCD Server

For **Windows CMD**, run:

For **Git Bash**, retrieve the ArgoCD password:

To get the ArgoCD URL in Minikube:

Login to ArgoCD:

### 3. Set Up Repository Structure

Clone or create a Git repository and structure it as follows:

### 4. Define ArgoCD Applications

Create application manifests for each environment:

#### Example: `applications/dev-app.yaml`

Repeat this for `staging-app.yaml` and `prod-app.yaml`, updating `values-staging.yaml` and `values-prod.yaml` accordingly.

### 5. Apply ArgoCD Applications

### 6. Verify in ArgoCD UI

1. Open `https://<ARGOCD_SERVER_IP>`.
2. Login with `admin` and the password from Step 2.
3. You should see `wordpress-dev`, `wordpress-staging`, and `wordpress-prod` applications.
4. Click **Sync** to deploy.

## Conclusion

This project integrates Helm with ArgoCD to provide a **GitOps-based** workflow for managing WordPress deployments in Kubernetes. Any updates to `values.yaml` files will be automatically reflected in the cluster, ensuring a **declarative and automated deployment** process.

