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
````

Each module is self-contained with:

* `main.tf`
* `variables.tf`
* `outputs.tf`

---

## 🔧 Key Design Decisions

### Why Terraform?

* Infrastructure as Code (IaC)
* Version-controlled infrastructure
* Safe, repeatable deployments
* Clear dependency management

### Why Separate Modules?

* Reusability
* Maintainability
* Clean abstraction boundaries
* Easy scaling

### Why No Software Installation in Phase 1?

* Terraform handles **infrastructure only**
* Configuration is delegated to Ansible (Phase 2)
* Prevents tight coupling between infra and config

---

## 🚀 How to Use

### Initialize Terraform

```bash
terraform init
```

### Validate Configuration

```bash
terraform validate
```

### Review Execution Plan

```bash
terraform plan
```

### Apply Infrastructure

```bash
terraform apply
```

### Destroy Infrastructure (Cost Safety)

```bash
terraform destroy
```

---

## 📤 Outputs

Terraform outputs provide public IPs for all servers:

* Jenkins
* SonarQube
* Nexus
* Docker Host
* Ansible Control Node

These outputs are later used for:

* Ansible inventory
* Documentation
* Validation

---

## 🔒 Security & Git Hygiene

* Terraform state files are **not committed**
* SSH keys (`*.pem`) are ignored
* `.terraform/` directory is ignored
* Clean `.gitignore` enforced

---

## 🧭 Next Phase

**Phase 2 – Configuration Management (Ansible)**:

* Ansible will run from the Ansible EC2 control node
* Install and configure Jenkins, Docker, SonarQube, and Nexus
* No manual SSH configuration
* Fully automated provisioning

---

## ✅ Status

✔ Phase 1 complete
✔ Infrastructure verified in AWS Console
✔ Code committed to GitHub
✔ Ready for Phase 2

---

## 👤 Author

**Kishan Gollamudi**
DevOps | Cloud | Infrastructure as Code

````
