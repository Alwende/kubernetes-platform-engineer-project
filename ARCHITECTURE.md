# 🏗️ Technical Architecture: Enterprise Kubernetes Platform

## 🗺️ System Flow Diagram
```mermaid
graph TD
    User([External User]) -->|HTTPS Port 443| Ing[Nginx Ingress Controller]
    
    subgraph Security_Layer [Security & Observability]
        CM[Cert-Manager] ---|Issues TLS| Ing
        Prom[Prometheus] ---|Scrapes Metrics| Mesh
        Graf[Grafana] ---|Visualizes| Prom
    end

    subgraph Service_Mesh [Istio Service Mesh]
        Ing -->|90% Traffic| VS_v1[VirtualService v1]
        Ing -->|10% Traffic| VS_v2[VirtualService v2]
        
        subgraph Pod_v1 [Frontend Pod v1 Cluster]
            direction LR
            App1[Nginx App] --- Side1[Admin Sidecar]
            Side1 --- Envoy1[Istio Proxy/Envoy]
        end

        subgraph Pod_v2 [Frontend Pod v2 Cluster]
            direction LR
            App2[Nginx App] --- Side2[Admin Sidecar]
            Side2 --- Envoy2[Istio Proxy/Envoy]
        end
    end

    subgraph Persistence [Stateful Layer]
        Pod_v1 --- PVC[Persistent Volume Claim]
        Pod_v2 --- PVC
        PVC --- PV[Persistent Volume /mnt/data]
    end

    subgraph Governance [CI/CD Pipeline]
        GH[GitHub Repo] -->|Git Push| GHA[GitHub Actions]
        GHA -->|Validates IaC| K8s[Minikube Cluster]
    end
```

## 🛠️ Integrated Feature Set
1.  **Phase 1 (Foundations):** RBAC Control, Namespace Isolation (`lfs158`).
2.  **Phase 2 (Persistence):** PV/PVC Storage, Kubernetes Secrets, ConfigMaps.
3.  **Phase 3 (Elasticity):** HPA (CPU-based scaling), Nginx Ingress Routing.
4.  **Phase 4 (Hardening):** Cert-Manager (TLS), Prometheus & Grafana Monitoring.
5.  **Phase 5 (Traffic Engineering):** Istio Service Mesh, 90/10 Canary Shifting, GitHub Actions.
