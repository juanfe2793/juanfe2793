# Hi there, I'm Juan Felipe Gómez 👋

<div align="left"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a> <a href="mailto:juangomeztic27@gmail.com"> <img src="https://img.shields.io/badge/EMail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /> </a> </div>

**Staff Software Engineer | Cloud Infrastructure & SRE | Kubernetes | Service Mesh & API Gateways**

I am a Telematics Engineer with over 10 years of experience driving the lifecycle of Compute and Network infrastructure, from on-premise data centers to massive-scale cloud environments. Currently, I serve as a **Staff Software Engineer** in Twilio’s Platform Infrastructure Team, specializing in **AWS, Kubernetes, Service Communications, and Infrastructure as Code (Terraform)**.

I focus on designing resilient, high-traffic architectures, having led critical initiatives in **Cloud Native API Gateways (handling 3M+ RPS), Zero-Trust Connectivity, and Multi-Region DNS modernization**. My work emphasizes **reliability engineering**, **operational excellence**, and **strategic infrastructure leadership**.

---

### 🔭 Current Focus
* **AI Integration:** Automating infrastructure processes and decision-making using AI in cloud environments. 
* **Service Communication:** Improving performance and reliability via Service Mesh and API Gateways (Kong, Istio). 
* **Resiliency, Reliability and Scalability:** Maximizing availability (99.99%+) for mission-critical platform services.

---

### 🏗 Architecture Highlights

Here are some simplified representations of the high-scale infrastructure projects I have led, designed, implemented and operated.

#### 1. Cloud Native API Gateway Infrastructure
A high-throughput, secure API Gateway solution proven to handle **3.39M RPS** during stress testing. It features automated provisioning via Terraform, custom plugin management, and full observability using OpenTelemetry sidecars, serving as the backbone for Twilio's critical platform services.

The architecture distributes traffic across multiple AWS services, fronted by a hardened Kong API Gateway. Traffic enters from Twilio's Edge Network (or Client VPCs) and is routed via AWS PrivateLink to a Network Load Balancer (NLB). This NLB handles layer-4 distribution to the ECS-based Gateway Cluster, where Kong containers manage routing, authentication, and metric collection (via OpenTelemetry sidecars) before proxying traffic to internal backend microservices.

#### 2. Multi-Region Hierarchical DNS Strategy
A standardized, platform-agnostic DNS architecture enabling seamless service discovery across multiple Kubernetes clusters, regions, and environments. This architecture supported a **zero-incident migration** of critical DNS traffic and enables automatic bootstrapping of new domains in minutes, establishing a robust foundation for Cloud Native Domains.

The system implements a strict delegation hierarchy: `Root (domain.com) -> Environment (Prod/Dev) -> Region (us-east-1) -> Service`. This layered approach ensures that queries are efficiently routed from the global root down to specific regional service endpoints, allowing for isolated fault domains and clear ownership boundaries.

#### 3. Automated Cross-Account Private Connectivity
A Terraform-driven architecture enabling zero-trust, private connectivity between distinct AWS accounts. It utilizes AWS RAM and SSM Parameters to automate the handshake between VPC Endpoint Services and Clients, eliminating manual coordination.

When a Terraform module provisions a new service in the Provider Account, it automatically updates AWS Resource Access Manager (RAM) to share the service ID and syncs metadata to the SSM Parameter Store. Consumer accounts then read this metadata to automatically provision the corresponding VPC Endpoints, establishing a secure PrivateLink tunnel without manual ticket exchanges.

#### 4. Decentralized Gateway Configuration Pipeline
A robust GitOps workflow for managing API Gateway custom logic. This architecture decouples plugin development from infrastructure provisioning, allowing teams to build, push to ECR/S3, and deploy custom behavior dynamically at container startup.

The CI/CD pipeline is triggered by commits to the Plugin Monorepo. It builds and pushes JSON/YAML configurations to an S3 Config Bucket and Wasm/Lua binaries to an ECR Registry. At runtime, the Gateway Task initializes by fetching the latest configuration and plugins from these sources, ensuring that the running gateway always operates with the most current logic without requiring a full infrastructure redeploy.

#### 💼 Experience

#### Staff Software Engineer (L4) @ Twilio (2023 - Present)

**High-Scale API Gateway & Cloud Native Domains:** Led the end-to-end design and implementation of a Kong-based Domain Gateway, successfully validated to handle **3.39M aggregate RPS**. This infrastructure serves as the critical entry point for next-gen platform services.

**Reliability Engineering & Operational Excellence:** Hardened Ingress Gateways and led the migration to AWS Cloud WAN, improving service-to-service communication success rates from 96.3% to **99.9%+**. Drastically reduced incident volume to just **3 Sev3 incidents in 9 months**, achieving an **MTTA of <4 minutes** and **MTTR of ~1 hour**.

**DNS Infrastructure Modernization:** Designed and implemented a centralized, agnostic DNS boundary supporting multi-cluster/multi-region service discovery. Executed a **zero-incident migration** of DNS resolution traffic, ensuring seamless continuity for critical internal services.

**Security & Standardization:** Spearheaded the **Public Ingress Security** verification, establishing zero-trust patterns and strict compliance frameworks for exposing internal Kubernetes services to the public internet safely.

**Developer Experience & Tooling:** Developed an automated `k6` and `Helm` based performance testing suite adopted by multiple teams, reducing complex load test setups to just **two commands**.

#### Sr Software Engineer - Kubernetes Platform @ Twilio (2021 - 2023)

- Implemented Observability for initial Twilio Kubernetes Services using Datadog. Providing a monitoring and alerting system for critical services.

- Implemented and operated Argo CD for GitOps and automated rollouts for Kubernetes services. Ensured smooth and reliable updates to production environments.

- Deployed and operated more than 50 Kubernetes clusters in multiple regions and environments, developing and maintaining Terraform modules for consistent and repeatable infrastructure.

#### Site Reliability Engineer @ Adyton PBC (2020 - 2021)

- Built CI/CD systems from scratch using Bazel, GitLab Pipelines, and ArgoCD.

- Implemented robust infrastructure on AWS (Standard and GovCloud) for mission-critical services.


### 🛠️ Technologies & Tools

Cloud & Infra: AWS, Terraform, Kubernetes (EKS), Docker, Helm.

Connectivity: Kong API Gateway + plugins, Istio, Envoy, DNS (Route53).

Observability: Datadog, Prometheus, Grafana, OpenTelemetry.

CI/CD: ArgoCD, Jenkins, Buildkite.

Languages: Python, Go, HCL.

<div align="center"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://www.google.com/search?q=https://img.shields.io/badge/LinkedIn-0077B5%3Fstyle%3Dfor-the-badge%26logo%3Dlinkedin%26logoColor%3Dwhite" alt="LinkedIn" /> </a>