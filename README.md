# 🚀 Enterprise Kubernetes Platform: Global GKE Deployment
**Architect:** Dan Alwende, PMP, CSPO
**Status:** PRODUCTION LIVE (Verified Phase 6)

## 🏗️ Project Overview
This repository chronicles the strategic transformation of **Wakwetu General Stores Ltd.** from a fragile, local container setup to a hardened, observable, and automated **Terraform & Google Kubernetes Engine (GCP)** ecosystem. This is a full-lifecycle engineering project, demonstrating mastery of cloud-native infrastructure, GitOps delivery, and enterprise governance.

---

## 🗺️ The 6-Phase Engineering Journey

### 🏁 Phase 0: Infrastructure as Code (Terraform Layer)
* **The Problem:** Manual infrastructure provisioning (ClickOps) is error-prone and non-auditable.
* **The Solution:** Defined the entire GCP environment using **Terraform**. Provisioned a custom VPC, Subnets, and a regional 3-node GKE cluster to ensure reproducibility and state-lock governance.

### 🏁 Phase 1-2: Foundations & Persistent State
* **The Problem:** Ephemeral data and lack of security boundaries.
* **The Solution:** Established `lfs158` namespace isolation with strict **RBAC**. Migrated from local storage to **GCP Persistent Disks (RWO)**, ensuring sales data survives pod restarts.

### 📈 Phase 3-4: Elasticity & Security Hardening
* **The Problem:** Manual scaling and unknown vulnerabilities.
* **The Solution:** Implemented **HPA** based on CPU metrics. Integrated **Trivy Vulnerability Scanning** into the CI pipeline to ensure zero "Critical" CVEs reach production.

### 🕸️ Phase 5: Service Mesh & Traffic Engineering
* **The Problem:** Blind "all-or-nothing" deployments.
* **The Solution:** Deployed **Istio Service Mesh**. Developed **Canary Deployment** logic allowing 90/10 traffic shifting between versions.

### 🚀 Phase 6: The Production Pivot (GitOps & Governance)
1. **GitOps with ArgoCD:** Eliminated "Configuration Drift" via a Pull-based delivery model.
2. **Public Edge Routing:** Established **NGINX Ingress** at Static IP **35.194.3.0**.
3. **Enterprise Guardrails:** Enforced **ResourceQuotas** (2 CPU / 2Gi RAM) to prevent runaway costs.
4. **Advanced Observability:** Deployed a full **Prometheus & Grafana** stack.

---

## 🛠️ Technical Stack
* **Cloud & IaC:** Terraform, Google Kubernetes Engine (GCP)
* **CD/GitOps:** ArgoCD
* **Security:** RBAC, Trivy, ResourceQuotas
* **Mesh:** Istio v1.21.0
* **Monitoring:** Prometheus & Grafana
* **Edge:** NGINX Ingress

---

## 🚦 Quick Start & Verification
* **Production URL:** http://35.194.3.0
* **Grafana Dashboards:** `kubectl port-forward deployment/prometheus-grafana -n monitoring 3000:3000`

---
**Verified by Dan Alwende, PMP (March 20, 2026)**
