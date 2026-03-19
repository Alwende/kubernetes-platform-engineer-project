# 🚀 Enterprise Kubernetes Platform Engineering: Full Lifecycle Project
**Architect:** Dan Alwende, PMP, CSPO

## 🏗️ Project Overview
This repository documents the evolution of a production-grade Kubernetes environment, moving from a basic containerized app to a hardened, observable Service Mesh with automated CI/CD.

## 🏁 Phase 1: Foundations & RBAC
* **Namespace Isolation:** Created the `lfs158` environment.
* **Security Governance:** Implemented RBAC for User 'Bob' with limited 'pod-reader' permissions.
* **Workload Deployment:** Deployed a 3-replica Nginx frontend with an administrative Echo-Sidecar.

## 💾 Phase 2: Persistence & Configuration
* **Stateful Storage:** Configured Persistent Volumes (PV) and Claims (PVC) using `hostPath` for log retention.
* **Secrets Management:** Migrated sensitive credentials to Kubernetes Secrets.
* **Decoupled Config:** Utilized ConfigMaps for environment-variable driven port management.

## 📈 Phase 3: Scaling & Ingress
* **Elasticity:** Enabled `metrics-server` and implemented Horizontal Pod Autoscaling (HPA) targeting 50% CPU.
* **Traffic Routing:** Deployed Nginx Ingress Controller to manage `frontend.local` domain traffic.

## 🔒 Phase 4: Hardening & Observability
* **Observability Stack:** Installed Prometheus & Grafana via Helm for real-time telemetry.
* **Automated PKI:** Deployed Cert-Manager with a self-signed ClusterIssuer for internal SSL/TLS.
* **Secure Edge:** Forced HTTPS termination on Port 443 for all ingress points.

## 🕸️ Phase 5: Service Mesh & Canary
* **Istio Integration:** Implemented Istio v1.21.0 with sidecar injection (Triple-container pods).
* **Traffic Engineering:** Configured VirtualServices for 90/10 Canary traffic shifting between v1 and v2.
* **CI/CD:** Integrated GitHub Actions to automate manifest validation on every push.

## ✅ Final Verification
```bash
curl -Iv https://frontend.local -k
# Result: HTTP 200 OK via TLSv1.3 | Pod Count: 3/3 READY
```
