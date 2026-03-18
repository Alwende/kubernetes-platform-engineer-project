# Kubernetes Platform Engineering Project: Secure Multi-Container Architecture

## 🚀 Overview
This project demonstrates a production-grade Kubernetes deployment focused on **Security, Observability, and Resource Management**. It was developed to simulate a high-availability environment suitable for enterprise platforms like Safaricom.

## 🛠️ Key Architectural Features
* **RBAC Governance:** Implemented a dedicated namespace (`lfs158`) with restricted user access (User: Bob).
* **Multi-Container Pods:** Utilized the **Sidecar Pattern** by deploying an Nginx frontend with an Echo-Server admin sidecar.
* **Service Discovery:** Configured a **Multi-Port LoadBalancer Service** to manage traffic across HTTP (80) and Admin (8080) ports.
* **Configuration Decoupling:** Used **ConfigMaps** to manage environment variables, ensuring the infrastructure is environment-agnostic.
* **Resource Reliability:** Defined **CPU/Memory Requests & Limits** to move from 'BestEffort' to 'Burstable' QoS.

## 📋 Infrastructure Audit
Below is a snapshot of the pod environment captured during the deployment phase:
```json
{
  "host": {
    "hostname": "localhost",
    "ip": "127.0.0.1"
  },
  "environment": {
    "HOSTNAME": "frontend-deploy-6ccd986ff9-jn24b",
    "FRONTEND_SVC_SERVICE_HOST": "10.99.43.97",
    "KUBERNETES_SERVICE_HOST": "10.96.0.1"
  }
}
```

## 🚦 How to Deploy
1. Create the namespace and RBAC: `kubectl apply -f rbac-config.yaml`
2. Apply configuration: `kubectl apply -f frontend-config.yaml`
3. Deploy the workload: `kubectl apply -f frontend-deployment.yaml`
4. Access the service: `minikube service frontend-svc -n lfs158`

## 🛡️ Fault Resolution
During development, addressed a critical **EADDRINUSE (Port 80 collision)** by implementing environment-variable-driven port reassignment via ConfigMaps.
