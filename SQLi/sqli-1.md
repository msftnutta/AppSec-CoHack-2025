# OWASP Juice Shop Deployment Guide

## Overview

This guide provides step-by-step instructions to deploy OWASP Juice Shop on Azure using either Azure Container Apps or Azure Kubernetes Service (AKS). Choose the deployment method that best fits your requirements and experience level.

## Prerequisites

- Azure CLI installed and configured
- Azure subscription with appropriate permissions
- Docker Desktop (for local testing)
- kubectl (for AKS deployment)

## Option 1: Azure Container Apps (Recommended for Beginners)

Azure Container Apps provides a serverless container platform that's easier to manage and cost-effective for learning environments.

### Step 1: Set Up Environment Variables

```bash
# Set your resource group and location
RESOURCE_GROUP="rg-appsec-cohack"
LOCATION="eastus"
CONTAINER_APP_ENV="env-juice-shop"
CONTAINER_APP_NAME="juice-shop-app"
```

### Step 2: Create Resource Group

```bash
az group create \
  --name $RESOURCE_GROUP \
  --location $LOCATION
```

### Step 3: Create Container Apps Environment

```bash
az containerapp env create \
  --name $CONTAINER_APP_ENV \
  --resource-group $RESOURCE_GROUP \
  --location $LOCATION
```

### Step 4: Deploy OWASP Juice Shop

```bash
az containerapp create \
  --name $CONTAINER_APP_NAME \
  --resource-group $RESOURCE_GROUP \
  --environment $CONTAINER_APP_ENV \
  --image bkimminich/juice-shop \
  --target-port 3000 \
  --ingress external \
  --min-replicas 1 \
  --max-replicas 3 \
  --cpu 0.5 \
  --memory 1Gi
```

### Step 5: Get Application URL

```bash
az containerapp show \
  --name $CONTAINER_APP_NAME \
  --resource-group $RESOURCE_GROUP \
  --query properties.configuration.ingress.fqdn \
  --output tsv
```

## Option 2: Azure Kubernetes Service (AKS)

AKS provides more control and is suitable for advanced users who want to learn Kubernetes deployment patterns.

### Step 1: Set Up Environment Variables

```bash
# Set your variables
RESOURCE_GROUP="rg-appsec-cohack-aks"
CLUSTER_NAME="aks-juice-shop"
LOCATION="eastus"
NODE_COUNT=2
```

### Step 2: Create Resource Group

```bash
az group create \
  --name $RESOURCE_GROUP \
  --location $LOCATION
```

### Step 3: Create AKS Cluster

```bash
az aks create \
  --resource-group $RESOURCE_GROUP \
  --name $CLUSTER_NAME \
  --node-count $NODE_COUNT \
  --node-vm-size Standard_B2s \
  --enable-addons monitoring \
  --generate-ssh-keys \
  --enable-managed-identity
```

### Step 4: Connect to AKS Cluster

```bash
az aks get-credentials \
  --resource-group $RESOURCE_GROUP \
  --name $CLUSTER_NAME
```

### Step 5: Create Kubernetes Deployment

Create a deployment file `juice-shop-deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: juice-shop
  labels:
    app: juice-shop
spec:
  replicas: 2
  selector:
    matchLabels:
      app: juice-shop
  template:
    metadata:
      labels:
        app: juice-shop
    spec:
      containers:
      - name: juice-shop
        image: bkimminich/juice-shop
        ports:
        - containerPort: 3000
        resources:
          requests:
            memory: "512Mi"
            cpu: "250m"
          limits:
            memory: "1Gi"
            cpu: "500m"
---
apiVersion: v1
kind: Service
metadata:
  name: juice-shop-service
spec:
  selector:
    app: juice-shop
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: LoadBalancer
```

### Step 6: Deploy to AKS

```bash
kubectl apply -f juice-shop-deployment.yaml
```

### Step 7: Get External IP

```bash
kubectl get service juice-shop-service --watch
```

Wait until the EXTERNAL-IP is assigned, then access the application at `http://<EXTERNAL-IP>`.

## Security Considerations

⚠️ **Important Security Notes:**

- These deployments are for educational purposes only
- Do not expose these vulnerable applications to the public internet in production
- Consider using Azure Private Endpoints or network security groups to restrict access
- Clean up resources after the workshop to avoid unnecessary costs

## Verification Steps

1. Access the application URL
2. Verify the OWASP Juice Shop welcome page loads
3. Test basic functionality (registration, login)
4. Confirm the application is ready for SQL injection testing


## Next Steps

Once OWASP Juice Shop is deployed, proceed to the [SQL injection exercises](sqli-2.md) to practice identifying and exploiting vulnerabilities in a safe environment.