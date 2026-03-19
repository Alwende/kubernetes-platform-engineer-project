# PROJECT CHARTER: ENTERPRISE KUBERNETES PLATFORM (LFS158)
**Project Manager:** Dan Alwende, PMP, CSPO  
**Sponsor:** Wakwetu General Stores Ltd. / IT Steering Committee  
**Date:** March 19, 2026

## 1. PROJECT PURPOSE & BUSINESS CASE
To modernize the Wakwetu digital infrastructure by migrating from legacy standalone containers to a secure, observable, and elastic Kubernetes Service Mesh. The goal is to reduce downtime by 95% and ensure 100% encryption of sensitive construction/sales data.

## 2. PROJECT OBJECTIVES (S.M.A.R.T)
* **Infrastructure:** 99.9% availability via Self-Healing Liveness probes and HPA.
* **Security:** Achieve Zero-Trust architecture using Istio mTLS and RBAC.
* **Deployment:** Implementation of Automated CI/CD for sub-5-minute manifest validation.

## 3. HIGH-LEVEL REQUIREMENTS
* Namespace-level isolation for administrative and project workloads.
* Persistent storage backend for critical application logging.
* Automated SSL/TLS certificate lifecycle management.
* Dynamic traffic shifting capabilities (Canary/Blue-Green).

## 4. SUMMARY MILESTONE SCHEDULE
| Milestone | Deliverables | Status |
| :--- | :--- | :--- |
| **Phase 1: Foundation** | RBAC, Namespace Setup, Initial Deployments | COMPLETED |
| **Phase 2: Persistence** | PV/PVC Implementation, Secret/Config Management | COMPLETED |
| **Phase 3: Networking** | Ingress Controller, HPA Setup, Metrics Server | COMPLETED |
| **Phase 4: Hardening** | Prometheus/Grafana Stack, Cert-Manager TLS | COMPLETED |
| **Phase 5: Mesh & CI/CD** | Istio Integration, Canary Logic, GitHub Actions | ACTIVE |

## 5. PROJECT RISKS & CONSTRAINTS
* **Resource Constraints:** Local Minikube environment limitations (CPU/RAM).
* **Technical Risk:** Envoy sidecar injection overhead affecting startup latency.
* **Constraint:** All implementation must remain "Documentation-First."

## 6. CHANGE & INCIDENT LOG (PMBOK ALIGNED)
| Date | ID | Category | Description | Resolution |
| :--- | :--- | :--- | :--- | :--- |
| 2026-03-18 | INC-006 | Network | Ingress Routing Loop | Upstreamed to FQDN service layer. |
| 2026-03-19 | INC-008 | Resource | Sidecar Injection Failure | Optimized replica count to release RAM. |

---
**AUTHORIZATION:** *Digital Signature: Dan Alwende, PMP*
