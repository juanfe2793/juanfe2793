# Hi there, I'm Juan Felipe Gómez 👋

<div align="left"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a> <a href="https://juanfe2793.github.io/Portfolio/" target="_blank"> <img src="https://img.shields.io/badge/Portfolio-16161A?style=for-the-badge&logo=githubpages&logoColor=white" alt="Portfolio" /> </a> <a href="mailto:juangomeztic27@gmail.com"> <img src="https://img.shields.io/badge/EMail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /> </a> </div>

**Staff Software Engineer | Cloud Infrastructure & SRE | Kubernetes | Service Mesh & API Gateways**

I am a Telematics Engineer with over 10 years of experience driving the lifecycle of Compute and Network infrastructure, from on-premise data centers to massive-scale cloud environments. Currently, I serve as a **Staff Software Engineer** in Twilio's Platform Infrastructure Team, specializing in **AWS, Kubernetes, Service Communications, and Infrastructure as Code (Terraform)**.

I focus on designing resilient, high-traffic architectures, having led critical initiatives in **Cloud Native API Gateways (multi-million RPS), Zero-Trust Connectivity, and Multi-Region DNS modernization**. My work emphasizes **reliability engineering**, **operational excellence**, and **strategic infrastructure leadership**.

---

### 🔭 Current Focus
* **AI Integration:** Automating infrastructure processes and decision-making using AI in cloud environments.
* **Service Communication:** Improving performance and reliability via Service Mesh and API Gateways (Kong, Istio).
* **Resiliency, Reliability and Scalability:** Maximizing availability for mission-critical platform services, with a five-nines target.

---

### 🏗 Architecture Highlights

Simplified, vendor-neutral views of the kinds of high-scale infrastructure I have led, designed, implemented and operated. The full write-ups live in my [portfolio](https://juanfe2793.github.io/Portfolio/docs/case-studies).

#### 1. Cloud Native API Gateway Infrastructure
A high-throughput, secure API gateway platform validated at **multi-million requests per second** under stress testing. It features automated provisioning via Terraform, governed plugin management, and full observability using OpenTelemetry sidecars, serving as a foundation for critical platform services.

Traffic reaches a hardened Kong gateway over AWS PrivateLink, through a Network Load Balancer that handles layer-4 distribution to a containerized gateway tier. There, Kong manages routing, authentication and metric collection before proxying traffic to backend microservices.

#### 2. Multi-Region Hierarchical DNS Strategy
A standardized, platform-agnostic DNS architecture enabling seamless service discovery across multiple Kubernetes clusters, regions, and environments. It supported a **zero-incident migration** of critical DNS traffic and lets new domains bootstrap in minutes, giving Cloud Native Domains a robust foundation.

The system implements a strict delegation hierarchy: `Root -> Environment -> Region -> Service`. This layered approach routes queries from the global root down to regional service endpoints, allowing isolated fault domains and clear ownership boundaries.

#### 3. Automated Cross-Account Private Connectivity
A Terraform-driven architecture enabling zero-trust, private connectivity between distinct AWS accounts. It combines AWS resource sharing with parameter-store discovery to automate the handshake between endpoint services and their clients, eliminating manual coordination.

When a Terraform module provisions a new service in the provider account, the service is shared automatically and its metadata is published for consumers. Consumer accounts read that metadata to provision the matching endpoints, establishing a secure PrivateLink connection without manual ticket exchanges.

#### 4. Decentralized Gateway Configuration Pipeline
A GitOps workflow for managing API gateway custom logic. It decouples plugin development from infrastructure provisioning, so teams can build, publish, and deploy custom behavior dynamically at container startup.

A CI/CD pipeline triggered by commits to a plugin monorepo publishes declarative configuration to object storage and plugin artifacts to a container registry. At runtime, each gateway task fetches the latest configuration and plugins, so the running gateway always operates with current logic without a full infrastructure redeploy.

---

### 💼 Experience

#### Staff Software Engineer @ Twilio (2023 - Present)

**High-Scale API Gateway & Cloud Native Domains:** Led the end-to-end design and implementation of a Kong-based domain gateway, validated at **multi-million RPS**. This infrastructure serves as a critical entry point for next-generation platform services.

**Reliability Engineering & Operational Excellence:** Hardened ingress gateways and led network path improvements that raised service-to-service success rates to a **five-nines target**. Drove a sustained reduction in incident volume and faster detection and recovery times.

**DNS Infrastructure Modernization:** Designed and implemented a centralized, agnostic DNS boundary supporting multi-cluster and multi-region service discovery. Executed a **zero-incident migration** of DNS resolution traffic, ensuring seamless continuity for critical internal services.

**Security & Standardization:** Led the public ingress security verification, establishing zero-trust patterns and compliance practices for safely exposing internal Kubernetes services.

**Developer Experience & Tooling:** Built an automated `k6` and `Helm` based performance testing suite adopted by multiple teams, reducing complex load test setups to **two commands**.

#### Senior Software Engineer, Kubernetes Platform @ Twilio (2021 - 2023)

- Implemented observability for the company's early Kubernetes services with Datadog, providing monitoring and alerting for critical workloads.

- Implemented and operated Argo CD for GitOps and automated rollouts, ensuring smooth and reliable production updates.

- Deployed and operated dozens of Kubernetes clusters across regions and environments, building and maintaining Terraform modules for consistent, repeatable infrastructure.

#### Site Reliability Engineer @ Adyton PBC (2020 - 2021)

- Built CI/CD systems from scratch using Bazel, GitLab Pipelines, and ArgoCD.

- Implemented robust infrastructure on AWS (Standard and GovCloud) for mission-critical services.

---

### 🛠️ Technologies & Tools

Cloud & Infra: AWS, Terraform, Kubernetes (EKS), Docker, Helm.

Connectivity: Kong API Gateway + plugins, Istio, Envoy, DNS (Route53).

Observability: Datadog, Prometheus, Grafana, OpenTelemetry.

CI/CD: ArgoCD, Jenkins, Buildkite.

Languages: Python, Go, HCL.

<div align="center"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a> </div>
