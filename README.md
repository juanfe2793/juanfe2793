# Hi there, I'm Juan Felipe Gómez 👋

**Staff Software Engineer | Cloud Infrastructure & SRE | Kubernetes | Service Mesh & API Gateways**

I am a Telematics Engineer with over 10 years of experience in the lifecycle of Compute and Network infrastructure, ranging from on-premise data centers to large-scale cloud environments. Currently, I work as a **Staff Software Engineer** in the Twilio Platform Infrastructure area, specializing in **AWS, Kubernetes, Service Communications and Infrastructure as Code (Terraform)**.

I focus on designing resilient, high-traffic architectures, having led critical initiatives in **DNS infrastructure redesign, Service Mesh optimization, and Cloud Native API Gateways**.

---

### 🔭 Current Focus
* **AI Integration:** Automating infrastructure processes and decision-making using AI in cloud environments. 
* **Service Communication:** Improving performance and reliability via Service Mesh and API Gateways (Kong, Istio). 
* **Resiliency, Reliability and Scalability:** Maximizing availability (99.99%+) for mission-critical platform services.

---

### 🏗 Architecture Highlights

Here are some simplified representations of the high-scale infrastructure projects I have led, designed, implemented and operated.

#### 1. Cloud Native API Gateway Infrastructure
A scalable, secure API Gateway solution designed to handle millions of transactions per day. It features automated provisioning via Terraform, custom plugin management, and full observability using OpenTelemetry sidecars.

```mermaid
graph LR
    subgraph Client_Account [Client / Edge Account]
        App[Client Application] -->|Private Request| VPCE[VPC Endpoint]
    end

    subgraph Platform_Account [Platform Account]
        VPCS[VPC Endpoint Service]
        NLB[Network Load Balancer]
        
        subgraph ECS_Cluster [Gateway Cluster]
            Kong[API Gateway Container]
            Otel[Otel Sidecar]
        end
        
        S3[(Config Bucket)]
        ECR[(Plugin Registry)]
        
        VPCE -.->|AWS PrivateLink| VPCS
        VPCS --> NLB
        NLB --> Kong
        Kong -->|Metrics| Otel
        Kong -.->|Fetch Config| S3
        Kong -.->|Pull Plugins| ECR
    end

    subgraph Backend_Services [Internal Network]
        Svc1[Microservice A]
        Svc2[Microservice B]
    end

    Kong --> Svc1
    Kong --> Svc2
```

#### 2. Multi-Region Hierarchical DNS Strategy
A standardized, platform-agnostic DNS architecture enabling seamless service discovery across multiple Kubernetes clusters, regions and environments (e.g., service.region.env.domain.com) enabling the use of Cloud Native Domains. Thanks to this architecture new domains and services could be bootstrapped automatically, and could be discovered by any Twilio internal service in minutes.

```mermaid
graph TD
    Root[Root Zone <br/> internal.com]
    
    subgraph Region_Layer [Regional Layer]
        USEast[us-east-1]
        USWest[us-west-2]
    end
    
    subgraph Env_Layer [Environment Layer]
        Prod[prod.us-east-1]
        Dev[dev.us-east-1]
    end
    
    subgraph Domain_Layer [Domain Ownership]
        Domain1[payments.prod...]
        Domain2[messaging.prod...]
        Domain3[auth.prod...]
    end

    Root -->|Delegation| USEast
    Root -->|Delegation| USWest
    
    USEast -->|Delegation| Prod
    USEast -->|Delegation| Dev
    
    Prod -->|Delegation| Domain1
    Prod -->|Delegation| Domain2
    Prod -->|Delegation| Domain3
    
    style Root fill:#f9f,stroke:#333,stroke-width:2px
    style Domain_Layer fill:#e1f5fe,stroke:#01579b
```

#### 3. Automated Cross-Account Private Connectivity
A Terraform-driven architecture enabling zero-trust, private connectivity between distinct AWS accounts. It utilizes AWS RAM and SSM Parameters to automate the handshake between VPC Endpoint Services and Clients, eliminating manual coordination.

```mermaid
graph LR
    subgraph Consumer_Account [Consumer Account]
        ClientApp[Client Application]
        VPCE[VPC Endpoint]
        SSM_Get[SSM Parameter Store]
    end

    subgraph Shared_Infrastructure [AWS Backbone]
        PL[AWS PrivateLink]
        RAM[Resource Access Manager]
    end

    subgraph Provider_Account [Provider Account]
        VPCS[VPC Endpoint Service]
        NLB[Network Load Balancer]
        App[Backend Service]
        TF_Mod[Terraform Module]
    end

    App --> NLB
    NLB --> VPCS
    VPCS -.->|Share Service ID| RAM
    RAM -.->|Sync Metadata| SSM_Get
    
    TF_Mod -->|Provisions| VPCS
    TF_Mod -->|Updates| RAM
    
    SSM_Get -->|Fetch Service Name| VPCE
    ClientApp -->|Private Traffic| VPCE
    VPCE ==>|Secure Tunnel| PL
    PL ==>|Traffic| VPCS
```

#### 4. Decentralized Gateway Configuration Pipeline
A robust GitOps workflow for managing API Gateway custom logic. This architecture decouples plugin development from infrastructure provisioning, allowing teams to build, push to ECR/S3, and deploy custom behavior dynamically at container startup.

```mermaid
graph TD
    subgraph CI_CD_Pipeline [Build Pipeline]
        Repo[Plugin Monorepo]
        Build[Build & Test]
        PushConfig[Push Config]
        PushImage[Push Plugin]
    end

    subgraph Artifact_Store [Storage Layer]
        S3[(S3 Config Bucket)]
        ECR[(Container Registry)]
    end

    subgraph Runtime_Environment [ECS Cluster]
        Task[Gateway Task Startup]
        Run[Running Gateway]
    end

    Repo -->|Commit| Build
    Build -->|JSON/YAML| PushConfig
    Build -->|Wasm/Lua| PushImage
    
    PushConfig --> S3
    PushImage --> ECR
    
    Task -.->|1. Fetch Config| S3
    Task -.->|2. Pull Plugin| ECR
    Task -->|3. Initialize| Run
```



#### 💼 Experience

#### Staff Software Engineer (L4) @ Twilio (2023 - Present)

**API Gateway & Cloud Native Domains:** Led the design and implementation of a Kong-based Domain Gateway, achieving ~ 3.39M aggregate RPS in stress tests.

**Observability:** Implemented OpenTelemetry sidecars for real-time metrics and created automated performance testing tools using k6.

**DNS Modernization:** Designed and implemented a centralized, agnostic DNS boundary to support multi-cluster and multi-region service discovery.

**Reliability and Resiliency:** Hardened Ingress Gateways and support the migration of network infrastructure to AWS Cloud WAN, improving success rates to 99.9%+.

**Public Ingress Capability:** Led the design and implementation of a public ingress capability to allow safely expose Kubernetes services to the public internet, following Twilio's security and compliance frameworks, integrated with Twilio's API.

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

<div align="center"> <a href="https://www.linkedin.com/in/juangomez27/" target="_blank"> <img src="https://www.google.com/search?q=https://img.shields.io/badge/LinkedIn-0077B5%3Fstyle%3Dfor-the-badge%26logo%3Dlinkedin%26logoColor%3Dwhite" alt="LinkedIn" /> </a> <a href="mailto:juangomeztic27@gmail.com"> <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /> </a> </div>