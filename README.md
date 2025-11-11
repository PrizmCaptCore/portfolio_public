# MLOps & Cloud Infrastructure Portfolio

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)
![Code](https://img.shields.io/badge/Full_Code-Private_Repo-orange.svg)
![Commits](https://img.shields.io/badge/Commits-219+-brightgreen.svg)

**Production-grade MLOps infrastructure and healthcare data pipelines**

Showcasing expertise in AWS, Kubernetes, Terraform, Python, and healthcare IT systems.

> **📦 Note**: This is the **public overview portfolio**. **Full implementation code (40+ files, 5000+ lines) is maintained in a private repository** and is available upon request for hiring evaluation or collaboration discussions.

---

## 👨‍💻 About

Senior MLOps Engineer with hands-on experience building production ML infrastructure and healthcare data pipelines. This portfolio demonstrates:

- **Cloud Infrastructure**: Multi-VPC AWS architecture with security-first design
- **MLOps Pipelines**: ClearML, Airflow, MLflow with auto-scaling
- **Healthcare Systems**: FHIR R4, PACS/DICOM integration
- **Container Orchestration**: Production Kubernetes deployments
- **Python Development**: 16+ production ML packages

**Experience**: 219+ commits across 12+ production repositories

---

## 🏗️ Architecture Highlights

### Dual-VPC AWS Infrastructure

```
┌─────────────────────────────────────────────────────────────────┐
│                         AWS Account                              │
│                                                                  │
│  ┌────────────────────────┐    ┌─────────────────────────────┐ │
│  │   Isolated VPC         │    │     Service VPC             │ │
│  │   (Private Workloads)  │◄──►│  (Public Services)          │ │
│  │                        │    │                             │ │
│  │  ✓ SSH from trusted IP │    │  ✗ NO SSH                   │ │
│  │  ✓ ML Training         │    │  ✓ HTTP/HTTPS only          │ │
│  │  ✓ Data Processing     │    │  ✓ ALB + Route53            │ │
│  │                        │    │  ✓ Auto Scaling             │ │
│  └────────────────────────┘    └─────────────────────────────┘ │
│                                                                  │
│  Security: VPC isolation • Security Groups • IAM • Encryption   │
└─────────────────────────────────────────────────────────────────┘
```

**Key Features:**
- Network isolation with dual-VPC design
- Zero SSH policy for production servers
- Multi-AZ deployment for high availability
- Cost-optimized with Spot instances (60% savings)

### MLOps Pipeline Architecture

```
┌──────────┐    ┌──────────────┐    ┌───────────────┐    ┌──────────┐
│ Airflow  │───►│ ClearML Queue│───►│ Spot Instance │───►│ MLflow   │
│   DAG    │    │              │    │  Autoscaler   │    │ Tracking │
└──────────┘    └──────────────┘    └───────────────┘    └──────────┘
                                            │
                                            ▼
                                    ┌──────────────┐
                                    │ GPU Training │
                                    │   Agents     │
                                    └──────────────┘
```

**Technologies:** ClearML, Airflow, MLflow, AWS Boto3, Kubernetes

### Healthcare Data Integration

```
┌────────────┐    ┌────────────┐    ┌──────────────┐
│    PACS    │───►│   DICOM    │───►│  ML Pipeline │
│   Server   │    │ Processor  │    │  (PyTorch)   │
└────────────┘    └────────────┘    └──────────────┘
                                            │
                                            ▼
┌────────────┐    ┌────────────┐    ┌──────────────┐
│    EHR     │◄───│   FHIR R4  │◄───│ Diagnostic   │
│   System   │    │   Client   │    │   Report     │
└────────────┘    └────────────┘    └──────────────┘
```

**Standards:** FHIR R4, DICOM, HL7, HIPAA compliance

---

## 🔗 Repository Structure

This public repository contains:
- Architecture documentation and diagrams
- Technology stack descriptions
- Design patterns and principles

The full implementation code is maintained in a **private Git submodule**:
```
portfolio_public/               (this repo - PUBLIC)
├── README.md                   (this file)
├── LICENSE
├── .gitmodules                 (submodule configuration)
├── SUBMODULE_INFO.md          (submodule access guide)
└── private-implementations/    → https://github.com/PrizmCaptCore/portfolio.git (PRIVATE)
    ├── 1-aws-terraform-iac/    (40+ files, 5000+ lines of IaC)
    ├── 2-mlops-pipelines/
    ├── 3-healthcare-integration/
    ├── 4-kubernetes-gitops/
    ├── 5-hpc-cluster/
    └── 6-python-packages/
```

See [SUBMODULE_INFO.md](SUBMODULE_INFO.md) for details on accessing the private submodule.

---

## 📁 Portfolio Sections

### 1. AWS Terraform Infrastructure

Production-ready Infrastructure as Code with security-first design:

**Architecture:**
- Dual-VPC network isolation (Isolated VPC + Service VPC)
- Multi-AZ deployment across 3 availability zones
- Application Load Balancer with SSL/TLS termination
- Route53 DNS with ACM certificate automation
- VPC endpoints for cost optimization

**Security Implementation:**
- NO SSH access to production app servers
- Security groups with least-privilege access
- IAM roles (no hardcoded credentials)
- Encrypted EBS volumes
- Network segmentation

**Key Files:**
- `vpc.tf` - Dual-VPC architecture with peering
- `security_groups.tf` - Zero-trust security policies
- `alb.tf` - Load balancer with Route53 integration
- `main.tf` - EC2 compute instances

**Cost:** ~$250/month for basic setup, 60% savings with Spot instances

[📄 Detailed implementation available on request]

---

### 2. MLOps Pipelines

End-to-end ML pipeline orchestration with auto-scaling:

**Components:**
- **ClearML Pipeline**: 4-stage workflow (preprocess → train → evaluate → deploy)
- **Spot Autoscaler**: Dynamic EC2 provisioning based on queue length
- **Airflow DAG**: S3 data ingestion, ML training, model deployment

**Features:**
- Queue-based auto-scaling (0-5 instances)
- Cost optimization: 60% savings vs on-demand
- MLflow experiment tracking
- Automated deployment to production

**Technologies:**
- ClearML, Airflow, MLflow
- AWS Boto3, EC2 Spot instances
- Python asyncio, Pydantic

**Results:**
| Instance Type | On-Demand | Spot | Savings |
|--------------|-----------|------|---------|
| g4dn.xlarge  | $0.526/hr | $0.21/hr | 60% |
| p3.2xlarge   | $3.06/hr  | $1.22/hr | 60% |

[📄 Full pipeline code available on request]

---

### 3. Healthcare Integration

FHIR R4 and PACS/DICOM integration for medical imaging workflows:

**FHIR R4 Client:**
- Async patient demographics retrieval
- Imaging study queries with modality filtering
- DiagnosticReport creation with SNOMED CT coding
- GCP Healthcare API integration

**DICOM Processor:**
- Windowing and contrast adjustment
- Normalization and resizing
- Production-grade error handling
- Multi-format support

**PACS Client:**
- C-FIND, C-MOVE, C-STORE operations
- PyNetDICOM integration
- Automated study retrieval

**Standards:**
- FHIR R4 (HL7)
- DICOM/PACS
- HIPAA compliance considerations

[📄 Implementation details available on request]

---

### 4. Kubernetes GitOps

Production Kubernetes manifests for MLOps infrastructure:

**Deployments:**
- MLflow tracking server (2 replicas, PostgreSQL backend, S3 artifacts)
- Airflow (CeleryExecutor: webserver, scheduler, workers)
- PostgreSQL StatefulSet (100Gi, multi-database)
- Redis (Celery message broker)
- ClearML experiment tracking

**Infrastructure:**
- Namespace isolation with RBAC
- Network policies for pod-to-pod security
- Ingress with TLS (cert-manager)
- Persistent volumes (EBS, EFS)
- Resource limits and quotas

**Technologies:**
- Kubernetes 1.28+
- Kustomize for configuration management
- NGINX Ingress Controller
- Cert-Manager for TLS automation

[📄 Complete manifests available on request]

---

### 5. HPC SLURM Cluster

Dockerized SLURM cluster for distributed ML training:

**Architecture:**
- SLURM controller + compute nodes
- Multi-node GPU cluster (4 nodes)
- Munge authentication
- Docker integration for ML workloads

**Configuration:**
- Resource management with cgroups
- Partitions: GPU (priority 100), CPU (priority 50)
- Job scheduling with backfill
- Supervisord process management

**Use Cases:**
- Distributed PyTorch training
- Large-scale data processing
- HPC workload orchestration

[📄 Cluster configuration available on request]

---

### 6. Python ML Packages

Production-ready Python packages in monorepo structure:

**Packages (16+ total):**
- `ml_inference` - PyTorch inference engine with Pydantic configs
- `dicom_processor` - Medical image preprocessing
- `fhir_client` - Async FHIR R4 client

**Architecture:**
- Monorepo with namespace packages
- Pre-commit hooks (Black, isort, mypy, ruff)
- pytest with async support
- Type hints and dataclasses

**Technologies:**
- PyTorch, TorchVision, MONAI
- Pydicom, nibabel, SimpleITK
- Google Cloud Healthcare API
- asyncio, aiohttp

[📄 Package source code available on request]

---

## 💼 Technical Skills

### Cloud & Infrastructure
- **AWS**: VPC, EC2, ALB, Route53, IAM, S3, CloudWatch
- **Terraform**: Multi-VPC architecture, modules, state management
- **Kubernetes**: Deployments, StatefulSets, Ingress, GitOps

### MLOps & Data Engineering
- **Orchestration**: ClearML, Airflow, MLflow
- **Auto-scaling**: AWS Spot instances, queue-based scaling
- **Monitoring**: CloudWatch, Prometheus, Grafana

### Programming
- **Python**: asyncio, type hints, Pydantic, pytest
- **ML/DL**: PyTorch, TorchVision, MONAI, scikit-learn
- **Healthcare**: FHIR R4, DICOM, HL7 standards

### DevOps
- **CI/CD**: GitHub Actions, pre-commit hooks
- **Containerization**: Docker, multi-stage builds
- **IaC**: Terraform, Kustomize

---

## 📈 Impact & Results

- **Infrastructure**: Managed multi-VPC AWS environments serving production ML workloads
- **Cost Optimization**: 60% reduction in compute costs via Spot instance autoscaling
- **Pipelines**: Built end-to-end ML pipelines processing medical imaging data
- **Integration**: Enabled FHIR/DICOM data exchange for healthcare systems
- **Packages**: Developed 16+ reusable Python packages deployed across projects

---

## 🔒 Full Implementation Access

This public portfolio showcases architecture and design patterns. **Detailed implementations are maintained in a private repository** and are available upon request for serious inquiries.

### 📦 Private Repository Contents

The private repository includes full source code with complete Git history (219+ commits):

**Available Materials:**
- ✅ **AWS Terraform IaC** - Complete dual-VPC configurations
  - `vpc.tf` (400+ lines) - Multi-AZ VPC architecture
  - `security_groups.tf` (300+ lines) - Zero-trust security policies
  - `alb.tf` (350+ lines) - Load balancer with Route53/ACM integration
  - `main.tf`, `variables.tf`, `userdata.sh`

- ✅ **MLOps Pipelines** - Production pipeline implementations
  - `clearml_pipeline.py` (200+ lines) - 4-stage ML workflow
  - `spot_autoscaler.py` (250+ lines) - EC2 auto-scaling logic
  - `airflow_dag.py` (180+ lines) - End-to-end ML DAG

- ✅ **Healthcare Integration** - FHIR & DICOM clients
  - `fhir_integration.py` (300+ lines) - Async FHIR R4 client
  - `pacs_dicom_client.py` (350+ lines) - PyNetDICOM integration

- ✅ **Kubernetes GitOps** - Complete manifest suite
  - 9 YAML files (1100+ lines total)
  - MLflow, Airflow, PostgreSQL, Redis, ClearML deployments
  - Network policies, RBAC, Kustomize configs

- ✅ **HPC SLURM Cluster** - Dockerized cluster setup
  - Dockerfiles, SLURM configs, docker-compose orchestration

- ✅ **Python ML Packages** - 16+ production packages
  - Full source code for `ml_inference`, `dicom_processor`, `fhir_client`
  - Monorepo setup with pre-commit hooks

### 🔑 How to Request Access

Please contact via email or LinkedIn with:
1. Brief introduction of your organization
2. Specific materials you're interested in reviewing
3. Intended use case (hiring evaluation, collaboration, etc.)

**Access Process:**
- Private repository invitation will be sent to your GitHub account
- You can review full implementation code and Git commit history
- Access is granted on a case-by-case basis for verified opportunities

**Response Time:** Usually within 24-48 hours for legitimate inquiries

---

## 📫 Contact

- **LinkedIn**: [linkedin.com/in/jomin-kim-643870126](https://www.linkedin.com/in/jomin-kim-643870126)
- **GitHub**: [@PrizmCaptCore](https://github.com/PrizmCaptCore)
- **Email**: lumia82015@live.com

---

## 📝 License

MIT License - See [LICENSE](LICENSE) file for details.

**Note**: Code samples in this portfolio are anonymized versions of production implementations. Proprietary business logic and domain-specific details have been removed or generalized.

---

<p align="center">
  <i>Portfolio showcasing 219+ commits from production MLOps and healthcare infrastructure work</i><br>
  <i>Full implementation details available for hiring evaluation</i>
</p>
