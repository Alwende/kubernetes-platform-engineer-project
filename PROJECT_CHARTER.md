# PROJECT CHARTER: WAKWETU KUBERNETES MODERNIZATION (EXTENDED)

**Project Name:** K8s-Platform-Hardening & Cloud Migration
**Project Manager:** Dan Alwende, PMP, CSPO
**Sponsor:** IT Steering Committee / Wakwetu General Stores Ltd.

## 1. PROJECT PURPOSE & JUSTIFICATION
The initial standalone container architecture lacked scalability. While Phases 1-5 established the baseline on Minikube, Phase 6 was authorized to pivot the entire platform to **Google Kubernetes Engine (GKE)** to support real-world production traffic, ensure high availability, and implement automated GitOps delivery.

## 2. HIGH-LEVEL PROJECT DESCRIPTION
A 6-phase implementation transitioning from a local laboratory (Minikube) to a production-grade GKE cluster. This includes advanced networking, automated vulnerability scanning, GitOps synchronization via ArgoCD, and strict resource governance.

## 3. MEASURABLE OBJECTIVES & SUCCESS CRITERIA
- **Obj 1-3:** (Achieved in Phases 1-5: RBAC, Persistence, mTLS).
- **Obj 4 (Phase 6):** Achieve 100% automated deployment via GitOps. (Success: ArgoCD Synced).
- **Obj 5 (Phase 6):** Enforce cloud-cost governance. (Success: ResourceQuotas active).
- **Obj 6 (Phase 6):** Establish public edge routing. (Success: Ingress IP 35.194.3.0 reachable).

## 4. UPDATED SCOPE
- **In-Scope:** All previous items + GKE Cluster Management, Helm-based Observability, ArgoCD GitOps, NGINX Ingress Controller, and GCP Storage Orchestration.

## 5. SUMMARY MILESTONE SCHEDULE
- **Phases 1-5:** Completed March 19, 2026.
- **Phase 6 (The Production Pivot):** GKE Migration, GitOps implementation, and Governance lockdown. Completed March 20, 2026.

## 6. RISKS & CONSTRAINTS
- **Revised Risk:** Multi-attach storage errors in GKE due to RWO volume limits. (Mitigated via HPA alignment).
- **Constraint:** All cloud infrastructure must remain under strict ResourceQuota limits.

**AUTHORIZATION:** IT Steering Committee / Dan Alwende, PMP - March 20, 2026
