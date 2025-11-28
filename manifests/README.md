# Kubernetes Multi-Namespace Frontend–Backend Project

This project demonstrates how to build a multi-tier application in Kubernetes using separate namespaces, deployments, services, and cluster networking.
It includes a frontend (Nginx) and backend (HTTP echo API), deployed inside a custom multi-node cluster created using Kind.

------------------------------------------------------------------------------------------------------------------------------------------------------
# Project Highlights

Multi-node Kubernetes cluster using Kind

Clean namespace separation:

frontend-ns

backend-ns

Frontend served using Nginx

Backend served using http-echo

Communication between namespaces using Kubernetes DNS

ClusterIP + NodePort Services

Full deployment files in manifests/

Perfect for learning, DevOps practice & interviews

------------------------------------------------------------------------------------------------------------------------------------------------------
# 🛠 Cluster Setup

1️⃣ Create a Kind Multi-Node Cluster:

kind create cluster --name demo-cluster --config manifests/cluster-config.yaml

kubectl get nodes


You should see:

1 control-plane

2 worker nodes

🏗 Deploy Frontend & Backend

2️⃣ Create namespaces:

kubectl apply -f manifests/frontend/namespace.yaml

kubectl apply -f manifests/backend/namespace.yaml

3️⃣ Deploy the Frontend:

kubectl apply -f manifests/frontend/frontend-deploy.yaml

kubectl apply -f manifests/frontend/frontend-service.yaml

4️⃣ Deploy the Backend:

kubectl apply -f manifests/backend/backend-deploy.yaml

kubectl apply -f manifests/backend/backend-service.yaml

------------------------------------------------------------------------------------------------------------------------------------------------------
# 🔗 Test Communication: Frontend → Backend

1. Get a frontend pod:

kubectl get pods -n frontend-ns

2. Get inside the pod:

kubectl exec -it <frontend-pod> -n frontend-ns -- sh

3. Install curl (if missing):

apt update && apt install -y curl

4. Test backend connectivity:

curl http://backend-svc.backend-ns.svc.cluster.local

------------------------------------------------------------------------------------------------------------------------------------------------------
