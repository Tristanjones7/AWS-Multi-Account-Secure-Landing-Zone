# AWS Multi-Account Secure Landing Zone (Mini)

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Terraform](https://img.shields.io/badge/IaC-Terraform-623CE4)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-blue)
![Security](https://img.shields.io/badge/Security-Best_Practices-green)

---

## PROJECT OVERVIEW

This project builds a simplified AWS Landing Zone using Terraform.

It simulates a real enterprise cloud environment with:
- Multi-account AWS setup
- Centralized logging
- Security guardrails
- CI/CD automation
- Isolated environments (dev, staging, production)

Goal: demonstrate real-world cloud engineering and SRE-level architecture skills.

---

## ARCHITECTURE

Below is the system design:
                AWS MANAGEMENT ACCOUNT
               (AWS ORGANIZATIONS ROOT)
                          |
  -------------------------------------------------
  |                      |                        |
DEV ACCOUNT     STAGING ACCOUNT               PROD ACCOUNT
VPC - VPC - VPC
App workloads - Testing env - Production app
| | |
                       |
            CENTRAL LOGGING ACCOUNT
            - S3 log storage
            - CloudTrail aggregation

---

## TECH STACK

- AWS Organizations
- IAM (least privilege access)
- VPC networking
- CloudTrail
- S3 (central logs)
- Terraform (Infrastructure as Code)
- GitHub Actions (CI/CD)
- Docker (sample app deployment)

---

## SECURITY DESIGN

This project follows cloud security best practices:

- Multi-account isolation (dev / staging / prod)
- IAM roles with least privilege
- Centralized logging for auditing
- CloudTrail enabled across all accounts
- Secure Terraform state handling (recommended S3 backend + DynamoDB lock)

Optional upgrades:
- SCP (Service Control Policies)
- AWS Config rules
- MFA enforcement for root users

---

## CI/CD PIPELINE

GitHub Actions automates deployment:

FLOW:

Git Push → GitHub Actions → Terraform Plan → Manual Approval → Terraform Apply

Pipeline stages:
1. Terraform fmt
2. Terraform validate
3. Terraform plan
4. Approval step (optional)
5. Terraform apply

---

## PROJECT STRUCTURE

aws-landing-zone/
│
├── terraform/
│   ├── organizations/
│   ├── networking/
│   ├── iam/
│   ├── logging/
│
├── app/
│   ├── simple-web-app/
│
├── github-actions/
│   ├── deploy.yml
│
├── diagrams/
│   ├── architecture.png
│
└── README.md

---

## DEPLOYMENT STEPS

1. Clone repo
git clone https://github.com/yourusername/aws-landing-zone-mini.git
cd aws-landing-zone-mini

2. Configure AWS credentials
aws configure

3. Initialize Terraform
cd terraform
terraform init

4. Plan infrastructure
terraform plan

5. Apply infrastructure
terraform apply

---

## WHAT THIS PROJECT DEMONSTRATES

- Real AWS multi-account architecture
- Cloud security design principles
- Infrastructure as Code (Terraform)
- CI/CD automation with GitHub Actions
- Production-grade system thinking

---

## FUTURE IMPROVEMENTS

- AWS Control Tower integration
- IAM Identity Center (SSO)
- WAF + ALB for application layer security
- AWS Budgets cost monitoring
- Observability stack (Prometheus + Grafana)
- Blue/green deployment pipeline

---

## AUTHOR

Tristan Jones  
Aspiring Cloud Engineer  
AWS Certified Solutions Architect Associate          
