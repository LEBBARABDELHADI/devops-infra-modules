
```markdown
# 🏗️ devops-infra-modules

> Production-grade, tested Terraform modules for AWS infrastructure.

[![Terraform](https://img.shields.io/badge/Terraform-1.6+-purple)]()
[![tfsec](https://img.shields.io/badge/tfsec-passing-green)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🎯 Vision

A curated library of opinionated, tested Terraform modules for AWS.
Each module follows the Terraform module conventions, includes validation,
examples, and auto-generated documentation.

Developed locally with **LocalStack**, tested with **Terratest**.

## 📦 Modules

| Module | Status | Purpose |
|--------|--------|---------|
| `vpc` | 🔜 W5 | Multi-AZ VPC with public/private subnets, NAT, endpoints, flow logs |
| `iam-cross-account` | 🔜 W6 | Cross-account roles with MFA, ExternalId, permission boundary |
| `lambda-app` | 🔜 W7 | Lambda with triggers (API GW, EventBridge, SQS), monitoring, VPC |
| `disaster-recovery` | 🔜 W9 | AWS Backup plans, cross-region replication |
| `ecs-fargate` | 🔜 W13 | ECS Fargate with capacity providers, auto-scaling, circuit breaker |
| `eks` | 🔜 W17 | EKS cluster with managed node groups, IRSA, addons |

## 🧪 Quality Standards

Every module includes:
- ✅ Typed variables with `validation {}` blocks
- ✅ Comprehensive outputs
- ✅ 2-3 working examples in `examples/`
- ✅ Auto-generated docs via [terraform-docs](https://terraform-docs.io/)
- ✅ CI: tflint + tfsec + checkov (zero warnings)
- ✅ Integration tests via Terratest
- ✅ Semantic versioning with git tags

## 📂 Structure

```
├── modules/
│   ├── vpc/
│   │   ├── README.md          # Auto-generated
│   │   ├── main.tf
│   │   ├── variables.tf       # With validations
│   │   ├── outputs.tf
│   │   └── examples/
│   │       ├── simple/
│   │       └── production-3az/
│   ├── iam-cross-account/
│   ├── lambda-app/
│   └── ...
├── tests/                     # Terratest (Go)
├── .github/workflows/
│   ├── terraform-validate.yml
│   └── terratest.yml
└── CONTRIBUTING.md
```

## 🚀 Usage

```hcl
module "vpc" {
  source = "github.com/YOURNAME/devops-infra-modules//modules/vpc?ref=v1.0.0"

  cidr_block         = "10.0.0.0/16"
  availability_zones = ["eu-west-3a", "eu-west-3b", "eu-west-3c"]
  enable_nat_gateway = true
  enable_flow_logs   = true
}
```

## 🔧 Local Development (LocalStack)

```bash
docker start localstack
cd modules/vpc/examples/simple
terraform init && terraform plan
```

## 📜 License 
