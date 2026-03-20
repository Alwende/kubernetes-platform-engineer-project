# PROJECT CHARTER: WAKWETU KUBERNETES MODERNIZATION (ENTERPRISE GKE)

**Project Manager:** Dan Alwende, PMP, CSPO
**Sponsor:** IT Steering Committee / Wakwetu General Stores Ltd.
**Project Status:** COMPLETED / PRODUCTION LIVE

## 1. PROJECT PURPOSE
Transitioning Wakwetu General Stores Ltd. from a fragile local container setup to a hardened, auto-scaling **Google Kubernetes Engine (GKE)** ecosystem. This project authorizes the 6-phase journey from local foundations to Cloud-Native GitOps.

## 2. HIGH-LEVEL OBJECTIVES
- **Phase 1-2:** Establish RBAC Security and GKE Persistent Storage.
- **Phase 3-4:** Implement HPA Scaling and Trivy Security Scanning.
- **Phase 5:** Deploy Istio Service Mesh for Canary Traffic Shifting.
- **Phase 6:** Automate the entire platform via ArgoCD GitOps and enforce Resource Governance (Quotas).

## 3. SUCCESS CRITERIA
- **Deployment:** 100% Automated via ArgoCD (Source of Truth: GitHub).
- **Availability:** Load-balanced traffic via NGINX Ingress at IP: 35.194.3.0.
- **Compliance:** 100% adherence to ResourceQuotas (2 CPU / 2Gi RAM).
- **Observability:** Real-time telemetry via Prometheus/Grafana stack.

## 4. MILESTONES
- **Phases 1-5 (Foundations & Mesh):** Completed March 19, 2026.
- **Phase 6 (GKE Production Pivot):** Completed March 20, 2026.

**AUTHORIZATION:** Dan Alwende, PMP (March 20, 2026)
