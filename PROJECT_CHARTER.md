# PROJECT CHARTER: WAKWETU K8S PLATFORM MODERNIZATION

**Project Name:** Wakwetu Cloud-Native Transition (Phases 1-6)
**Project Manager:** Dan Alwende, PMP, CSPO
**Sponsor:** IT Steering Committee / Wakwetu General Stores Ltd.
**Created Date:** March 15, 2026

## 1. PROJECT PURPOSE & JUSTIFICATION
Wakwetu General Stores Ltd. is currently operating on a legacy, standalone container architecture that lacks the high availability and security required for enterprise growth. This project is authorized to transition our infrastructure from a high-risk local environment to a hardened, auto-scaling **Google Kubernetes Engine (GKE)** ecosystem. The primary drivers are risk mitigation (security), operational efficiency (automation), and financial governance (cloud cost control).

## 2. HIGH-LEVEL PROJECT DESCRIPTION
A 6-phase strategic initiative to build a production-grade Kubernetes platform. The project starts with local foundational hardening (RBAC, Persistence) and culminates in a full Cloud Pivot utilizing GitOps delivery, Service Mesh traffic engineering, and strict Resource Quotas.

## 3. MEASURABLE PROJECT OBJECTIVES
* **Security:** Achieve zero-trust architecture via Namespace isolation and mTLS.
* **Resilience:** Maintain 99.9% availability through HPA and Cloud Load Balancing.
* **Velocity:** Reduce deployment time to <1 minute via automated GitOps (ArgoCD).
* **Governance:** Enforce 100% compliance with corporate budget caps using K8s ResourceQuotas.

## 4. HIGH-LEVEL REQUIREMENTS
* Implementation of a 3-node GKE Cluster with a dedicated VPC.
* Deployment of NGINX Ingress Controller for professional edge routing.
* Integration of Trivy for automated vulnerability scanning in the CI pipeline.
* Real-time observability via Prometheus and Grafana dashboards.

## 5. SUMMARY MILESTONE SCHEDULE
| Milestone | Description | Target Date |
| :--- | :--- | :--- |
| **M1: Foundations** | RBAC Setup & Storage Orchestration (Phases 1-2) | March 16, 2026 |
| **M2: Scaling** | HPA and Ingress Controller Integration (Phase 3) | March 17, 2026 |
| **M3: Hardening** | PKI/TLS and Monitoring Stack (Phase 4) | March 18, 2026 |
| **M4: Mesh** | Istio Service Mesh & Canary Logic (Phase 5) | March 19, 2026 |
| **M5: Production** | GKE Pivot & GitOps Go-Live (Phase 6) | March 20, 2026 |

## 6. RISKS, ASSUMPTIONS, & CONSTRAINTS
* **Risk:** Potential for "Multi-Attach" storage errors when scaling RWO volumes on GCP.
* **Assumption:** Stable connectivity between GitHub Actions and GKE Control Plane.
* **Constraint:** All cloud resources must remain within the **2 vCPU / 2Gi RAM** corporate budget.

## 7. AUTHORIZED RESOURCES
* **PM/Lead SRE:** Dan Alwende (Full Authority for IaC and Cluster Architecture).
* **Budget:** Authorization to consume GCP Free Tier and Open Source Tooling.

---
**AUTHORIZED BY:** IT Steering Committee / Dan Alwende, PMP
