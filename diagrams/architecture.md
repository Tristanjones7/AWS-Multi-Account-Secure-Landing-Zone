# AWS Multi-Account Secure Landing Zone — Architecture Diagram

```mermaid
flowchart TB
    M[Management Account\nAWS Organizations]

    M --> D[Development Account\nVPC + Workloads]
    M --> S[Staging Account\nVPC + Test Workloads]
    M --> P[Production Account\nVPC + Production Workloads]

    D --> L[Central Logging Account]
    S --> L
    P --> L

    L --> CT[CloudTrail\nAPI Activity]
    CT --> B[S3\nCentralized Log Storage]

    G[GitHub Actions] --> T[Terraform\nPlan / Approval / Apply]
    T --> M

    classDef mgmt fill:#eef4ff,stroke:#3b82f6,stroke-width:2px;
    classDef env fill:#f8fafc,stroke:#64748b,stroke-width:1.5px;
    classDef log fill:#f0fdf4,stroke:#22c55e,stroke-width:2px;
    classDef cicd fill:#faf5ff,stroke:#8b5cf6,stroke-width:2px;

    class M mgmt;
    class D,S,P env;
    class L,CT,B log;
    class G,T cicd;
```

## Design intent

- **Management account:** organizational control and account governance.
- **Separate environment accounts:** stronger isolation and reduced blast radius.
- **Central logging:** aggregate CloudTrail activity for auditing and investigation.
- **Terraform:** define infrastructure consistently and review changes before deployment.
- **GitHub Actions:** automate validation, planning, approval, and application of infrastructure changes.
