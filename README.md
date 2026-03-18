# 🚀 Enterprise Kubernetes Platform Engineering Case Study

## 🛠️ High-Level Architecture
This platform utilizes a **Triple-Container Pod** pattern (Nginx + Admin Sidecar + Envoy Proxy) to provide a zero-trust, observable environment.

## 📂 Technical Components
* **Service Mesh:** Istio v1.21.0 for mTLS and Canary Routing.
* **Security:** Cert-Manager for automated TLS termination.
* **Observability:** Full Prometheus/Grafana stack via Helm.
* **Automation:** GitHub Actions CI/CD for manifest validation.

## ✅ Verification
Validated via: `curl -Iv https://frontend.local -k` (HTTP 200 OK via TLSv1.3)
