# 🚀 Enterprise Kubernetes Platform: Global GKE Deployment
**Architect:** Dan Alwende, PMP, CSPO
**Status:** PRODUCTION LIVE (Verified Phase 6)

## 🏗️ Project Overview
This repository chronicles the strategic transformation of **Wakwetu General Stores Ltd.** from a fragile, local container setup to a hardened, observable, and automated **Terraform, Google Kubernetes Engine (GCP)** ecosystem. This is a full-lifecycle engineering project, demonstrating mastery of cloud-native infrastructure, GitOps delivery, and enterprise governance.

---

## 🗺️ The 6-Phase Engineering Journey

### 🏁 Phase 1-2: Foundations & Persistent State
* **The Problem:** Ephemeral data and lack of security boundaries.
* **The Solution:** Established `lfs158` namespace isolation with strict **RBAC (Role-Based Access Control)**. Migrated from local storage to **GCP Persistent Disks (RWO)**, ensuring sales data survives pod restarts.

### 📈 Phase 3-4: Elasticity & Security Hardening
* **The Problem:** Manual scaling and unknown vulnerabilities.
* **The Solution:** Implemented **Horizontal Pod Autoscaling (HPA)** based on real-time CPU metrics. Integrated **Trivy Vulnerability Scanning** into the CI pipeline to ensure zero "Critical" CVEs reach production.

### 🕸️ Phase 5: Service Mesh & Traffic Engineering
* **The Problem:** Blind "all-or-nothing" deployments.
* **The Solution:** Deployed **Istio Service Mesh**. Developed **Canary Deployment** logic allowing 90/10 traffic shifting between versions, significantly reducing the blast radius of new releases.

### 🚀 Phase 6: The Production Pivot (GitOps & Governance)
**The Ultimate Goal:** Shifting from a developer lab to an automated Enterprise Platform.

1.  **GitOps with ArgoCD:** Eliminated "Configuration Drift" by establishing a Pull-based delivery model. The cluster now synchronizes automatically with this repository.
2.  **Public Edge Routing:** Established the **NGINX Ingress Controller** at Static IP **35.194.3.0**, providing a professional entry point for external traffic.
3.  **Enterprise Guardrails:** Implemented **ResourceQuotas** (2 CPU / 2Gi RAM) and **LimitRanges** to prevent runaway cloud costs and ensure node stability.
4.  **Advanced Observability:** Deployed a full **Prometheus & Grafana** stack to provide a "Single Pane of Glass" view into cluster health.

---

## 🛠️ Technical Stack
* **Cloud:** Terraform, Google Kubernetes Engine (GCP)
* **CD/GitOps:** ArgoCD
* **Security:** RBAC, Trivy, ResourceQuotas
* **Mesh:** Istio v1.21.0
* **Monitoring:** Prometheus & Grafana
* **Edge:** NGINX Ingress

---

## 🚦 Quick Start & Verification

### 1. Access the Application
The platform is live and load-balanced at the following endpoint:
* **Production URL:** http://35.194.3.0

### 2. View Cluster Health (Grafana)
To view the real-time telemetry, initiate a port-forward and visit `localhost:3000`:
```bash
kubectl port-forward deployment/prometheus-grafana -n monitoring 3000:3000
```

### 3. GitOps Synchronization
Monitor the state of the infrastructure via the ArgoCD UI. All manifests in the `workloads/` directory are automatically synced to the `lfs158` namespace.

---
**Verified by Dan Alwende, PMP (March 20, 2026)**
