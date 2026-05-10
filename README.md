# Hi there, I'm Juan Felipe Gómez 👋

<div align="left"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a> <a href="mailto:hello@felipegomez.me"> <img src="https://img.shields.io/badge/EMail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /> </a> </div>

**Staff Software Engineer | Platform Infrastructure & SRE**

*Expert in scaling cloud-native infrastructure, high-throughput API gateways, and resilient platform services.*

10+ years experience Platform & Infrastructure Software Engineer that architect and deliver reliable systems for global and high-throughput scale products — API gateways, service mesh connectivity, DNS architecture, Public Ingress/Egress and the observability tooling that makes reliability measurable across distributed systems. Over four years at Twilio I led the zero-to-production delivery of the Cloud-Native Domain (CND) gateway platform, validated at 3.39M aggregate RPS under stress testing, and drove TwilioKubernetesPlatform ↔ ClassicTwilioPlatform inter-service reliability from 96.33% to 99.99%, building the baseline for Twilio Customer Trust.

---

## 🔭 Current Focus
* **AI Integration:** Automating infrastructure processes and decision-making using AI in cloud environments. 
* **Service Communication:** Improving performance and reliability via Service Mesh and API Gateways (Kong, Istio). Focusing in the enbalement of DDD architecture in Twilio
* **Resiliency, Reliability and Scalability:** Maximizing availability (99.999%+) for mission-critical platform services.

---

## 🏗 Architecture Highlights

Here are some simplified representations of the high-scale infrastructure projects I have led, designed, implemented and operated.

### 1. Cloud Native API Gateway Infrastructure
A high-throughput, secure API Gateway solution proven to handle **3.39M RPS** during stress testing. It features automated provisioning via Terraform, custom plugin management, and full observability using OpenTelemetry sidecars, serving as the backbone for Twilio's critical platform services.

The architecture distributes traffic across multiple AWS services, fronted by a hardened Kong API Gateway. Traffic enters from Twilio's Edge Network (or Client VPCs) and is routed via AWS PrivateLink to a Network Load Balancer (NLB). This NLB handles layer-4 distribution to the ECS-based Gateway Cluster, where Kong containers manage routing, authentication, and metric collection (via OpenTelemetry sidecars) before proxying traffic to internal backend microservices.

### 2. Multi-Region Hierarchical DNS Strategy
A standardized, platform-agnostic DNS architecture enabling seamless service discovery across multiple Kubernetes clusters, regions, and environments. This architecture supported a **zero-incident migration** of critical DNS traffic and enables automatic bootstrapping of new domains in minutes, establishing a robust foundation for Cloud Native Domains.

The system implements a strict delegation hierarchy: `Root (domain.com) -> Environment (Prod/Dev) -> Region (us-east-1) -> Service`. This layered approach ensures that queries are efficiently routed from the global root down to specific regional service endpoints, allowing for isolated fault domains and clear ownership boundaries.

### 3. Automated Cross-Account Private Connectivity
A Terraform-driven architecture enabling zero-trust, private connectivity between distinct AWS accounts. It utilizes AWS RAM and SSM Parameters to automate the handshake between VPC Endpoint Services and Clients, eliminating manual coordination.

When a Terraform module provisions a new service in the Provider Account, it automatically updates AWS Resource Access Manager (RAM) to share the service ID and syncs metadata to the SSM Parameter Store. Consumer accounts then read this metadata to automatically provision the corresponding VPC Endpoints, establishing a secure PrivateLink tunnel without manual ticket exchanges.

### 4. Decentralized Gateway Configuration Pipeline
A robust GitOps workflow for managing API Gateway custom logic. This architecture decouples plugin development from infrastructure provisioning, allowing teams to build, push to ECR/S3, and deploy custom behavior dynamically at container startup.

The CI/CD pipeline is triggered by commits to the Plugin Monorepo. It builds and pushes JSON/YAML configurations to an S3 Config Bucket and Wasm/Lua binaries to an ECR Registry. At runtime, the Gateway Task initializes by fetching the latest configuration and plugins from these sources, ensuring that the running gateway always operates with the most current logic without requiring a full infrastructure redeploy.

---

## 💼 Professional Experience

### Staff Software Engineer (L4) @ Twilio
*June 2023 – Present*

**Key Achievements**
* **API Gateway:** Led the design of CND Domain Gateway Infrastructure using Kong, validated at 3.39M aggregate RPS under stress testing.
* **DNS Modernization:** Designed domain-scoped, platform-agnostic DNS hierarchy across EKS, ASG, and ECS runtimes with blast-radius isolation per domain.
* **Reliability:** Drove inter-service success rate from 96.33% → 99.90% at 1.74M avg RPS.

**Platform & Gateway Architecture**
* Led design, planning, and delivery of the CND Domain Gateway Infrastructure — a reusable Terraform module providing a production-grade Kong API gateway (ECS autoscaling, NLB, TLS/gRPC, S3 config, VPC PrivateLink, OTel observability).
* Designed and implemented cross-account VPC PrivateLink Terraform modules (EndpointService + RAM share + client-side SSM parameter discovery); reduced connectivity onboarding to a plug-in module.
* Authored ADRs and architecture documents for Terraform module delivery, Kong plugin lifecycle, and stress/load/performance testing.

**DNS Infrastructure**
* Designed and implemented the domain-scoped DNS hierarchy platform-agnostic across Twilio's three runtime environments.
* Built the Route 53 hosted-zone Terraform module and DNS delegation chain; hardened records with prevent_destroy lifecycle rules.
* Implemented guardrails in production accounts to avoid manual manipulation of DNS infrastructure.
* Supported Service Catalog DNS sharding design; guided DNS delegation ownership model across platform teams.

**Reliability & Observability**
* Led NLB configuration hardening after production incidents; improved TwilioKubernetesPlatform → ClassicTwilioPlatform success rate 96.33% → 99.90%.
* Implemented Kong observability via OpenTelemetry sidecar exporting Prometheus metrics to Twilio's Springer/Grafana platform — first OTel integration for ECS-based Kong at Twilio.
* Built Grafana dashboard templates for Kong health and ECS metrics.
* Executed chaos/failure injection on Kong to validate gateway resilience and document recovery behavior.

**Testing & Developer Experience**
* Built the on-demand performance testing framework (k6 + Helm + Datadog); adopted by multiple engineering teams.
* Added ECS circuit breaker and rollback configuration to the API gateway Terraform module; enabled safe progressive delivery.
* Drove contributor documentation for the platform; wrote the CND DGW runbook and led the Domain Gateway Gameday.

**Mentoring & Cross-Team Influence**
* Provided technical guidance and pair programming for Twilio Classic Ingress Gateway sharding rollout, Service Catalog DNS sharding design, and Shuffle Sharding verification — mentoring multiple engineers across workstreams.
* Led knowledge transfer sessions on Domain Gateway architecture fundamentals for the broader team.
* Supported Data Platform team onboarding to the relay Kong gateway.

### Sr. Software Engineer, Kubernetes Platform (L3) @ Twilio
*November 2021 – June 2023*
Operated and scaled Twilio's Kubernetes-based API platform (OTK) across 50+ EKS clusters in multiple AWS regions. Implemented Datadog monitoring and alerting for cluster and workload health. Managed GitOps progressive delivery via Argo CD, enabling zero-downtime rollouts across production clusters. Authored Terraform modules for cluster lifecycle management and contributed to multi-region capacity planning and reliability improvements.

### Site Reliability Engineer / DevOps @ Adyton PBC
*June 2020 – November 2021*
Implemented infrastructure-as-code on AWS GovCloud for U.S. Department of Defense services using Terraform and SaltStack. Managed EKS clusters and ELK Stack monitoring. Built CI/CD systems with Bazel, GitLab Pipelines, Argo CD, and Jenkins.

### Software DevOps Engineer @ Addi
*March 2020 – June 2020*
Implemented SonarQube on Kubernetes clusters for automated integration test execution on new commits from product teams. Worked with development teams on the initial migration of workloads to Kubernetes.

### Professor @ Universidad Icesi
*August 2016 – December 2020*
Taught Operating Systems, Computer Networks II, and Infrastructure Automation. Developed Cloud Computing labs on AWS. Continued in parallel with industry roles through 2020.

### Cloud and DevOps Engineer @ IPINNOVATECH
*January 2020 – February 2020*
Implemented centralized AWS infrastructure management using SSM and CloudWatch.

### Research Assistant @ Universidad Icesi
*January 2018 – December 2019*
Published research on Quality of Service in Software-Defined Networks (SDN) on IEEEXplore.

### Network Engineer @ Global Networks Solutions
*December 2014 – December 2016*
Designed network infrastructure (127 Cisco devices) for government ministry facilities.

---

## 🛠️ Technical Skills

* **API Gateway & Service Mesh:** Kong API Gateway, Istio, Envoy, AWS ALB/NLB, cert-manager, external-dns
* **Cloud & Infrastructure:** AWS (ECS, EKS, Route 53, ACM, SSM, ECR, PrivateLink, RAM, IAM), Terraform, Helm, Argo CD, Kubernetes
* **Observability & Performance:** OpenTelemetry, Prometheus, Grafana, Datadog, k6, AWS EMF
* **Languages:** Go, Python, Bash, Lua (Kong plugins)
* **Practices:** Infrastructure-as-Code, GitOps, Chaos Engineering, ADR-driven Architecture, Progressive Delivery

---

## 🎓 Education

* **Master in Informatics and Telecommunications** | Universidad ICESI (2018 – 2020)
* **Professional in Telematics Engineering** | Universidad ICESI (2010 – 2016)

---

## 📜 Certifications & Publications

* **Certification:** LFS 265 — Software Defined Networking Fundamentals (Linux Foundation)
* **Publication:** "Performance of QoS policies in Software-Defined Networks" (IEEEXplore)
