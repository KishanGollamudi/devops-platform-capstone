# Phase 0 – Design Decisions & Standards

## Why Docker Compose Instead of Kubernetes
- The project scope focuses on CI/CD platform fundamentals rather than large-scale container orchestration.
- Docker Compose is simpler, faster to set up, and cost-effective for running platform services like SonarQube and Nexus.
- Compose provides clear service definitions, networking, and volume management without Kubernetes complexity.
- The goal is to demonstrate CI/CD principles, traceability, and automation—not Kubernetes administration.
- This choice keeps the platform maintainable and aligned with real-world small-to-medium DevOps setups.

## Why Infrastructure and Configuration Are Separated
- Infrastructure provisioning (Terraform) and configuration management (Ansible) solve different problems.
- Terraform is used only to create immutable resources such as VPCs, subnets, security groups, and virtual machines.
- Ansible is used to install and configure software after infrastructure exists.
- This separation improves clarity, reusability, and reduces blast radius during changes.
- It also allows infrastructure and configuration to evolve independently.

## What “No UI-Based Infrastructure” Means
- All infrastructure must be created, modified, and destroyed using code only.
- No manual creation or changes via cloud provider consoles are allowed.
- This ensures reproducibility, auditability, and version control of infrastructure.
- Any failure or misconfiguration must be fixed by updating code, not clicking in the UI.
- This approach reflects real DevOps and SRE best practices.
