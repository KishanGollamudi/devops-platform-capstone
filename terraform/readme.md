# Terraform – DevOps Platform Infrastructure (Phase 1)

This repository contains the **Terraform-based infrastructure setup** for a modular DevOps platform.  
The goal of Phase 1 is to provision **clean, reproducible AWS infrastructure** following best DevOps practices.

---

## 📌 Phase 1 Objective

Provision AWS infrastructure using **Terraform only**, with:
- No manual AWS Console configuration
- No software installation
- Clear separation of concerns
- Fully reproducible environment

Configuration and application setup are intentionally deferred to **Phase 2 (Ansible)**.

---

## 🧱 Architecture Overview

The following infrastructure components are created:

### 🌐 Networking
- Custom VPC
- Public Subnet
- Internet Gateway
- Route Table with internet access
- Proper tagging for visibility

### 🔐 Security
- Dedicated Security Groups per component
- SSH access enabled (port 22)
- Principle of isolation between services

### 🖥️ Compute (EC2 Instances)

| Component | Purpose |
|---------|--------|
| Jenkins | CI/CD orchestration |
| SonarQube | Code quality analysis |
| Nexus | Artifact repository |
| Docker Host | Image build & runtime |
| Ansible Control Node | Configuration management controller |

All instances:
- Run **Ubuntu Server**
- Are provisioned only (no software installed)
- Use encrypted EBS volumes
- Are tagged for environment and ownership

---

## 📁 Project Structure

```text
terraform/
├── main.tf
├── provider.tf
├── versions.tf
├── variables.tf
├── data.tf
├── outputs.tf
└── modules/
    ├── network/
    ├── security/
    ├── compute-jenkins/
    ├── compute-sonarqube/
    ├── compute-nexus/
    ├── compute-docker/
    └── compute-ansible/
