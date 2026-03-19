# PROJECT CHARTER: WAKWETU KUBERNETES MODERNIZATION
**Project Name:** K8s-Platform-Hardening  
**Project Manager:** Dan Alwende, PMP, CSPO  
**Sponsor:** IT Steering Committee / Wakwetu General Stores Ltd.

## 1. PROJECT PURPOSE & JUSTIFICATION
The current standalone container architecture at Wakwetu General Stores Ltd. lacks the scalability, security, and observability required for enterprise growth. This project is authorized to build a resilient Kubernetes-based Service Mesh to centralize governance and protect sales data integrity.

## 2. HIGH-LEVEL PROJECT DESCRIPTION
A 5-phase implementation to establish a production-grade Kubernetes cluster on a local-to-cloud transition path, incorporating advanced networking, automated security, and continuous delivery.

## 3. MEASUREABLE PROJECT OBJECTIVES & SUCCESS CRITERIA
* **Obj 1:** Establish Namespace-level isolation and RBAC within 24 hours. (Success: Zero unauthorized access).
* **Obj 2:** Ensure 100% data persistence for logs. (Success: PVC binding confirmed).
* **Obj 3:** Implement Zero-Trust mTLS. (Success: Handshake verification on port 443).

## 4. HIGH-LEVEL REQUIREMENTS & SCOPE
* **In-Scope:** RBAC, PV/PVC, HPA, Ingress, Monitoring, TLS, Service Mesh, CI/CD.
* **Out-of-Scope:** Frontend application code refactoring; External Cloud Provider costs.

## 5. SUMMARY MILESTONE SCHEDULE
1.  **Phase 1 (Foundation):** Authorization and RBAC environment setup.
2.  **Phase 2 (Persistence):** Storage class and volume orchestration.
3.  **Phase 3 (Scaling):** Ingress and Auto-scaling infrastructure.
4.  **Phase 4 (Hardening):** PKI and Observability stack integration.
5.  **Phase 5 (Traffic Engineering):** Mesh implementation and CI/CD Go-Live.

## 6. PROJECT RISKS, ASSUMPTIONS, & CONSTRAINTS
* **Risk:** Local machine resource limitations (8GB RAM) may impede Mesh performance.
* **Assumption:** Stable Docker/Minikube environment is available.
* **Constraint:** All infrastructure must be defined as code (IaC) and versioned.

## 7. ASSIGNED PROJECT RESOURCES & BUDGET
* **PM/SRE:** Dan Alwende (100% Allocation).
* **Budget:** Open-source tooling (Helm, Istio, Prometheus).

---
**AUTHORIZATION:** *IT Steering Committee Approval - March 15, 2026*
