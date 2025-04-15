## 🧩 Identifying Challenges with Containers

---

### 1. ⚖️ Scalability Challenges

- **No Auto-Scaling**: Containers on their own don’t scale automatically based on traffic or load.
  
  - **Scaling Up**:
    - When traffic spikes, you have to manually add more containers or scale your infrastructure.
    - Approaches:
      - **Vertical Scaling**: Increase CPU/RAM on the current host.
      - **Horizontal Scaling**: Add more container instances or hosts.

  - **Scaling Down**:
    - During off-peak hours, resources must be manually reduced to cut costs.

---

### 2. 🧃 Lack of Native Load Balancing

- Containers don’t natively distribute traffic.
- Without a load balancer, some containers may receive more requests than others, leading to imbalance.

---

### 3. 🚫 No Built-In Fault Tolerance

- If a container crashes, it won’t restart automatically.
- This creates a **single point of failure**, risking downtime and service disruption.

---

### 4. 🚑 Absence of Self-Healing

- Containers require manual recovery if they fail.
- No automatic detection or replacement leads to more maintenance overhead.

---

## ✅ Solution: Use Container Orchestration (e.g., Kubernetes)

To address these limitations, we use orchestration platforms like **Kubernetes**.

---

## ☸️ Kubernetes Overview

- **What is Kubernetes?**  
  An open-source system for automating deployment, scaling, and management of containerized apps.

- **Why use it?**  
  It ensures scalability, fault tolerance, high availability, and automated management of containers.

---

## ✨ Key Features of Kubernetes

1. **Orchestration** – Automates container deployment and lifecycle management.
2. **Auto Scaling** – Adjusts container count based on real-time demand.
3. **Load Balancing** – Efficiently distributes network traffic across services.
4. **Self-Healing** – Restarts failed containers and reschedules them on healthy nodes.
5. **Platform-Agnostic** – Runs on any cloud or on-premise setup.

---

## ⚙️ Kubernetes Cluster Setup (AWS EKS Example)

### 📋 Prerequisites

- A Bastion/Jump Server
- Installed tools:
  - `kubectl` – CLI to interact with Kubernetes
  - `eksctl` – CLI for managing EKS clusters
  - `awscli` – AWS command-line interface

---

### 🚀 Steps to Create a Kubernetes Cluster

```bash
# Create a shell script for setup
vi cluster.sh
chmod 777 cluster.sh
sh cluster.sh

# Configure AWS credentials
aws configure

# Create the EKS cluster
eksctl create cluster \
  --name vaishakh-cluster \
  --version 1.31 \
  --region eu-north-1 \
  --nodegroup-name test-linux \
  --node-type t3.micro \
  --nodes 3 \
  --nodes-min 3 \
  --nodes-max 5 \
  --managed

# Verify nodes
kubectl get nodes
```

## 🚀 Deploying Apps on Kubernetes
### 1️⃣ Deploy a Pod from Manifest
```bash
git clone https://github.com/Tejas1546/gitses.git
cd vaishakh-k8s-manifests

kubectl apply -f pod.yaml
kubectl get pods -o wide
kubectl describe pod sample-pod
```
### 2️⃣ Deploy a Sample Retail Application
```bash
git clone -b master https://github.com/Tejas1546/gitses.git
cd Retail-App_kubernetes

kubectl apply -f userprofile-deployment.yml
kubectl apply -f usernode-js-service.yml

kubectl get deployments
kubectl get svc
```
## 🏗️ Kubernetes Cluster Architecture

---

### 🔹 What is a Cluster?

- A **cluster** is a set of machines (nodes) managed by Kubernetes.
  
- It includes:
  - **Control Plane (Master Node)** – Manages the cluster.
  - **Worker Nodes** – Run your containerized apps.

---

### 🧠 Master Node Components

1. **API Server** – Entry point for all admin commands and external communication.
2. **ETCD** – Stores configuration data and cluster state.
3. **Controller Manager** – Maintains desired state (e.g., ensures correct pod count).
4. **Scheduler** – Assigns pods to suitable nodes based on resource availability.

---

### 🧱 Worker Node Components

1. **Kubelet** – Agent that interacts with the master and manages pods.
2. **Container Runtime** – Runs containers (e.g., Docker, containerd).
3. **Kube-Proxy** – Handles networking and forwards traffic between services and pods.

---

### 📦 Pod

- The smallest deployable unit in Kubernetes.
  
- Contains one or more containers with shared storage/network settings.
  
- Scheduled and run on worker nodes.
