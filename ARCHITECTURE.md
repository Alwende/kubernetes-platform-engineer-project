# 🏗️ Technical Architecture: Verified Enterprise GKE Platform

## 🗺️ System Flow Diagram (Phases 1-6)
```mermaid
graph TD
    User([External User]) -->|HTTP Port 80| Ing[NGINX Ingress Controller]
    
    subgraph GKE_Cloud_Infrastructure [Google Kubernetes Engine - Siaya Cluster]
        direction TB
        Ing -->|Routes| Svc[Frontend Service]
        
        subgraph LFS158_Namespace [Namespace: lfs158 - Protected]
            direction LR
            Svc --> HPA[Horizontal Pod Autoscaler]
            HPA --> Pod[Frontend Pod: Nginx + Sidecar]
            Pod --- PVC[Persistent Volume Claim]
            
            subgraph Governance [Resource Guardrails]
                RQ[ResourceQuota: 2CPU/2Gi]
                LR[LimitRange: 500m Default]
            end
        end

        subgraph Monitoring_Layer [Namespace: monitoring]
            Prom[Prometheus] ---|Scrapes| Pod
            Graf[Grafana] ---|Visualizes| Prom
        end
        
        subgraph GitOps_Control [Namespace: argocd]
            Argo[ArgoCD Server] -->|Syncs Manifests| LFS158_Namespace
        end
    end

    subgraph Storage_Layer [GCP Infrastructure]
        PVC --- PD[GCP Persistent Disk - RWO]
    end

    subgraph CI_CD_Pipeline [GitHub Ecosystem]
        Repo[(GitHub Repo)] -->|Push| GHA[GitHub Actions]
        GHA -->|Security Scan| Trivy[Trivy Vulnerability Scanner]
        Trivy -->|Success| Repo
        Repo ---|Source of Truth| Argo
    end
```

## 🛠️ Integrated Feature Set
1.  **Phase 1 (Foundations):** Namespace Isolation (`lfs158`), RBAC `pod-reader` role.
2.  **Phase 2 (Persistence):** GKE Persistent Disks (RWO) via PVCs for data durability.
3.  **Phase 3 (Elasticity):** HPA-driven scaling (CPU 50%) aligned with storage limits.
4.  **Phase 4 (Hardening):** Automated security with **Trivy** vulnerability scanning.
5.  **Phase 5 (Traffic Engineering):** **NGINX Ingress Controller** (IP: 35.194.3.0) for edge routing.
6.  **Phase 6 (Cloud-Native & Observability):** **ArgoCD** GitOps, **ResourceQuotas**, and **Prometheus/Grafana** metrics.

---
*Authorized by: Head of PMO*
