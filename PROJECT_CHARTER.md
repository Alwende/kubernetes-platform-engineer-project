# PROJECT CHARTER: Enterprise Kubernetes Frontend Infrastructure (Phase 1)

**Project Title:** Scalable & Secure Containerized Frontend Deployment  
**Project Lead:** Dan Alwende, PMP, CSPO  
**Designation:** Project Manager | Solutions Architect | Platform Engineer  
**Date:** March 18, 2026  

---

## 1. Project Justification & Business Case
The organization requires a standardized, repeatable, and secure deployment framework for frontend microservices to reduce Time-to-Market (TTM) and ensure 99.9% service availability. Current manual deployment methods pose significant risks to operational stability and security compliance.

## 2. High-Level Project Objectives (S.M.A.R.T.)
* **Security & Governance:** Achieve 100% logical isolation of the 'lfs158' workload via RBAC and Namespace-level restrictions.
* **Operational Reliability:** Implement self-healing capabilities via Liveness/Readiness probes to reduce Mean Time to Repair (MTTR).
* **Resource Optimization:** Transition 100% of deployment replicas from 'BestEffort' to 'Burstable/Guaranteed' QoS via defined Resource Quotas.
* **Decoupled Configuration:** Externalize 100% of environment-specific variables via ConfigMaps to ensure portability across Dev/Test/Prod environments.

## 3. High-Level Requirements & Scope
* **In-Scope:** Namespace creation, RBAC Role/Binding, Multi-container Pod (Sidecar Pattern), LoadBalancer Service, and ConfigMap injection.
* **Out-of-Scope:** Persistent Storage (Phase 2), Ingress Controller setup, and CI/CD Pipeline integration.

## 4. Key Stakeholders
* **Sponsor:** Head of Platform Engineering / PMO Director.
* **Primary User:** DevOps/Site Reliability Engineering (SRE) Teams.
* **Project Lead:** Dan Alwende (Architectural Design & Implementation).

## 5. Success Criteria & Quality Standards
* Successful `2/2 READY` status across all 3 replicas during rolling updates.
* Verification of RBAC restrictions (Bob user restricted to 'List/Watch' pods only).
* Zero-collision connectivity across Port 80 (Nginx) and Port 8080 (Admin Sidecar).

## 6. Constraints & Assumptions
* **Constraint:** Implementation must be compatible with CNCF-compliant Kubernetes distributions.
* **Assumption:** Minimum of 2 vCPUs and 4GB RAM available on the hosting node (Minikube).

## 7. Preliminary Risk Assessment
* **Technical Risk:** Port 80 collision within the shared Network Namespace. (Mitigated: Environment variable reassignment to 8080).
* **Resource Risk:** Node pressure leading to pod eviction. (Mitigated: Implementing Resource Limits/Requests).

---
**Approved By:** __________________________  
**Dan Alwende, PMP, CSPO**

---

## 8. Change & Incident Management Log
| Date | Incident/Change ID | Description | Resolution/Mitigation | Status |
| :--- | :--- | :--- | :--- | :--- |
| 2026-03-18 | INC-001 | GitGuardian: Detected Metadata Exposure | Executed Git history scrub (BFG/Filter-Branch equivalent) and force-pushed to origin. | **CLOSED** |
| 2026-03-18 | CHG-001 | Security Hardening | Implemented .gitignore protocols to prevent future exposure of sensitive audit artifacts. | **COMPLETED** |

---
**Audit Note:** *All non-production metadata exposed was localized to the 'lfs158' lab environment and posed zero risk to enterprise production systems. Security protocols now align with CIS Kubernetes Benchmarks.*

## 9. Phase 4: Hardening & Observability (Current)
* **Security:** TLS/SSL Termination via cert-manager (HTTPS).
* **Observability:** Prometheus & Grafana Stack for real-time telemetry.
* **Connectivity:** Istio Service Mesh for advanced traffic control.
* **Automation:** CI/CD via GitHub Actions.
