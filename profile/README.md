# CyberRangeCZ

**CyberRangeCZ** is an open-source platform for building, delivering, and managing advanced cybersecurity training environments.  
It enables organizations to create interactive, scenario-based cyber exercises with features like:

- Dynamic sandbox provisioning
- Adaptive training paths
- Real-time feedback
- Centralized user management

Designed for scalability and automation, the platform supports both individual and group-based training across diverse environments, making it suitable for educational, governmental, and enterprise use cases.

## Mission & Scope

CyberRangeCZ is built to support realistic, automated training simulations designed to:

- Help teams build real skills with hands-on, cloud-based training environments.
- Make it easy to reuse and tweak scenarios with clear, modular setup configurations.
- Manage large-scale training for trainees with minimal manual overhead.

## About the Platform

The CyberRangeCZ Platform is a container-based, microservices architecture optimized for creating and running cyber-range exercises:

- Supports **OpenStack** and **AWS** cloud back-ends.
- Offers both **linear** (fixed-level) and **adaptive** (knowledge-based branching) training models.
- Configured with an **infrastructure-as-code** model.


## Architecture

CyberRangeCZ is built atop a modern microservice ecosystem:

- **Sandbox Service** – Manages lifecycle of emulated environments.
- **Training Services** – Includes Linear and Adaptive Training services, integrated with Smart Assistant for real‐time decision logic.
- **Supporting Services** – Answers Storage, Training Feedback, Elasticsearch, MITRE Technique, User & Group, OIDC provider, etc.

Workload infrastructure on Kubernetes and OpenStack/AWS enables flexible deployment and sandbox provisioning.

## Repositories & Key Components

### `devops-helm`
- Serves as the primary tool for deploying the entire CyberRangeCZ platform onto Kubernetes clusters using Helm.
- Includes:
  - Helm configuration files (`helm/`)
  - Sandbox training definitions (`training-definitions/`)
  - Complete automated deployment workflows, including a Vagrant-based proof-of-concept setup
- Acts as the hub for configuring platform services, training definitions, proxy jump access, networking, and demo environments.

### Other important repositories:
- **`tf-module-helm`** – Terraform modules integrating with Helm deployment pipelines.
- **`devops-tf-deployment`** – Manages provisioning of cloud infrastructure on OpenStack and AWS using Terraform (via OpenTofu), feeding into the Helm deployment process for full platform installation.
- **`backend-sandbox-service`** – Provides APIs for sandbox orchestration and lifecycle management.
- **`backend-training`**, **`backend-adaptive-training`**, **`backend-adaptive-smart-assistant`**, **`backend-training-feedback`**, **`backend-answers-storage`** – Java-based microservices powering training logic, adaptive branching, assistance, and feedback capture.
- **`frontend-training-portal`** – The Angular-based web interface for launching training exercises and reviewing progress.


## Documentation

Comprehensive documentation is hosted at:  
[docs.platform.cyberrange.cz](https://docs.platform.cyberrange.cz)


## Target Audience

CyberRangeCZ is designed for anyone who needs scalable, hands-on cyber training environments:

- Educators teaching cybersecurity through real-world scenarios.
- Security teams running internal simulations, red/blue team exercises, or SOC training.
- Government & public sector institutions building cyber resilience.
- Training providers delivering live or self-paced courses at scale.
- Companies looking to upskill staff and test cyber readiness.
- Researchers & developers experimenting with sandboxed infrastructure for cyber testing.

Whether you're running a university course or building a national cyber drill, CyberRangeCZ helps you do it efficiently and repeatably.


## License & Credits

All code repositories are licensed under the **MIT License**, promoting community reuse and collaboration.  

CyberRangeCZ builds on the innovation started by **KYPO CRP at Masaryk University** since 2013, now stewarded by **CyberSecurity Hub, z.s.** with continued institutional support and community contributions.


## Contact & Support

- Browse the repositories’ issues or join GitHub Discussions at: [CyberRangeCZ Issues](https://github.com/cyberrangecz/issues)  
- For commercial support, large-scale deployment assistance, or custom integration, visit: [CyberRangeCZ Contact Page](https://www.cyberrange.cz/contact/)
