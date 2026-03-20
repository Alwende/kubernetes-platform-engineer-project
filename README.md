# 🚀 Enterprise Kubernetes Platform Engineering: Full Lifecycle Project
**Architect:** Dan Alwende, PMP, CSPO
**Status:** PRODUCTION LIVE (GKE)

## 🏗️ Project Overview
This repository documents the evolution of a production-grade Kubernetes environment. We moved from a local Minikube proof-of-concept to a hardened, observable, and automated **Google Kubernetes Engine (GKE)** ecosystem.

---

## 🏁 Phase 1: Foundations & RBAC
- **Namespace Isolation:** Created the `lfs158` environment.
- **Security Governance:** Implemented RBAC for User 'Bob' with limited 'pod-reader' permissions.
- **Workload Deployment:** Deployed a 3-replica Nginx frontend with an administrative Echo-Sidecar.

## 💾 Phase 2: Persistence & Configuration
- **Stateful Storage:** Configured PV and PVC using `hostPath` for initial log retention.
- **Secrets Management:** Migrated sensitive credentials to Kubernetes Secrets.
- **Decoupled Config:** Utilized ConfigMaps for environment-variable driven port management.

## 📈 Phase 3: Scaling & Ingress
- **Elasticity:** Enabled `metrics-server` and implemented HPA targeting 50% CPU.
- **Traffic Routing:** Deployed Nginx Ingress Controller for initial local domain traffic management.

## 🔒 Phase 4: Hardening & Observability
- **Observability Stack:** Installed Prometheus & Grafana via Helm for real-time telemetry.
- **Automated PKI:** Deployed Cert-Manager with a self-signed ClusterIssuer for SSL/TLS.
- **Secure Edge:** Forced HTTPS termination on Port 443 for all ingress points.

## 🕸️ Phase 5: Service Mesh & Canary
- **Istio Integration:** Implemented Istio v1.21.0 with sidecar injection.
- **Traffic Engineering:** Configured VirtualServices for 90/10 Canary traffic shifting.
- **CI/CD:** Integrated GitHub Actions to automate manifest validation.

---

## 🚀 Phase 6: The Production Pivot (Cloud & GitOps)
**The Challenge:** Moving from a single-node local lab to a multi-node **GKE Cluster** introduced real-world complexities: storage locks, public routing, and resource contention.

### 1. Cloud Infrastructure & Storage Orchestration
We provisioned a 3-node GKE cluster. We faced a critical **Multi-Attach Error** where the GCP Persistent Disk (RWO) could not be shared across scaling pods.
- **Resolution:** We aligned the **Horizontal Pod Autoscaler (HPA)** with storage physics and implemented a force-clear protocol to reset volume locks during deployment.

### 2. GitOps Delivery via ArgoCD
We moved away from manual `kubectl` commands. We installed **ArgoCD** to enforce a "Source of Truth" model.
- **Implementation:** The cluster now automatically polls this GitHub repo. Any change to the `workloads/` folder is instantly synchronized, ensuring the cluster state never drifts from the code.

### 3. Edge Routing & Ingress Management
We deployed a production-grade **NGINX Ingress Controller** via Helm.
- **Public Entry:** Assigned Static IP **35.194.3.0**.
- **Handshake:** Configured Ingress rules to route public traffic to the `frontend-service`, verified via browser access.

### 4. Enterprise Governance (Guardrails)
To prevent "Runaway Costs" in the cloud, we implemented:
- **ResourceQuotas:** Hard caps on the `lfs158` namespace (Max 2 CPU / 2Gi RAM).
- **LimitRanges:** Mandatory default requests for all new containers to ensure node stability.

### 5. Advanced Monitoring
The Prometheus/Grafana stack was upgraded to monitor GKE-specific metrics, giving us a "Single Pane of Glass" view into cluster-wide resource consumption.

## ✅ Final Production Verification
- **External Access:** http://35.194.3.0 -> **HTTP 200 OK**
- **GitOps Status:** ArgoCD -> **Healthy & Synced**
- **Security:** Trivy Scanning -> **Passed**
