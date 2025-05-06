# Infrastructure as Code

IaC tools, best practices, and resources

## IaC Platforms

### Multi-Cloud Solutions

- [Terraform](https://www.terraform.io/) - HashiCorp's infrastructure as code tool
- [Pulumi](https://www.pulumi.com/) - Modern infrastructure as code using programming languages
- [CloudFormation](https://aws.amazon.com/cloudformation/) - AWS native IaC service
- [CDK](https://aws.amazon.com/cdk/) - AWS Cloud Development Kit
- [Cloud Deployment Manager](https://cloud.google.com/deployment-manager) - Google Cloud's IaC service
- [Crossplane](https://crossplane.io/) - Manage infrastructure directly from Kubernetes
- [AIAC](https://github.com/gofireflyio/aiac) - AI-powered infrastructure as code generator

## Terraform Ecosystem

### Core Tools

- [Terraform Cloud](https://cloud.hashicorp.com/products/terraform) - managed Terraform service
- [Terragrunt](https://terragrunt.gruntwork.io/) - DRY code
- [Atlantis](https://www.runatlantis.io/) - Terraform PRs automation
- [Spacelift](https://spacelift.io/) - Terraform automation and collaboration
- [Infracost](https://www.infracost.io/) - Cloud cost estimates
- [Checkov](https://www.checkov.io/) - Static code analysis tool
- [TFLint](https://github.com/terraform-linters/tflint) - Terraform linter
- [Terraform-docs](https://terraform-docs.io/) - Documentation generator modules

### Infrastructure Import Tools

- [Terraformer](https://github.com/GoogleCloudPlatform/terraformer)
- [Terracognita](https://github.com/cycloidio/terracognita)
- [Terraforming](https://github.com/dtan4/terraforming)
- [CF2TF](https://github.com/DontShaveTheYak/cf2tf) - Convert CloudFormation to Terraform

### Testing and Validation

- [Terratest](https://terratest.gruntwork.io/) - Testing framework
- [Kitchen-Terraform](https://github.com/newcontext-oss/kitchen-terraform) - Test Terraform configurations
- [Terraform Validator](https://github.com/GoogleCloudPlatform/terraform-validator) - Policy validation tool
- [Conftest](https://www.conftest.dev/) - Write tests against structured configuration data

## Security and Compliance

- [OPA (Open Policy Agent)](https://www.openpolicyagent.org/) - Policy-based control for cloud infrastructure
- [KICS](https://kics.io/) - Find security vulnerabilities in IaC
- [TFSec](https://github.com/aquasecurity/tfsec) - Security scanner code
- [Terrascan](https://github.com/accurics/terrascan) - Static code analyzer for IaC
- [Regula](https://regula.dev/) - Check infrastructure as code for compliance

## State Management

- [Terraform Backend Configuration](https://www.terraform.io/language/settings/backends) - State storage options
- [S3 Backend](https://www.terraform.io/language/settings/backends/s3) - Store state in AWS S3
- [GCS Backend](https://www.terraform.io/language/settings/backends/gcs) - Store state in Google Cloud Storage
- [Azure Backend](https://www.terraform.io/language/settings/backends/azurerm) - Store state in Azure Storage
- [Remote Backend](https://www.terraform.io/language/settings/backends/remote) - Store state in Terraform Cloud

## Module Registries

- [Terraform Registry](https://registry.terraform.io/) - HashiCorp's public module registry
- [AWS Quick Start](https://github.com/aws-quickstart) - AWS reference deployments
- [Google Cloud Foundation Toolkit](https://github.com/GoogleCloudPlatform/cloud-foundation-toolkit) - GCP modules
- [Azure Terraform Modules](https://github.com/Azure/terraform-azurerm-modules) - Microsoft's Azure modules
- [CloudPosse](https://github.com/cloudposse) - Extensive collection of Terraform modules

## Secret Management

- [Vault](https://www.vaultproject.io/)
- [SOPS](https://github.com/mozilla/sops) - Secrets OPerationS
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/) - AWS native secrets
- [GCP Secret Manager](https://cloud.google.com/secret-manager) - GCP native secrets
- [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/) - Azure secrets

## Best Practices

### Code Organization

- Use consistent naming conventions
- Modularize infrastructure code
- Separate environments with workspaces or directories
- Store state remotely with locking enabled
- Use version control for all IaC code

### Security

- Enforce least privilege principle
- Scan IaC code for security issues
- Encrypt sensitive data in state files
- Implement compliance as code
- Use private module registries for sensitive modules

### Operations

- Implement CI/CD pipelines for infrastructure
- Use plan output review before applying changes
- Implement change management processes
- Set up monitoring for infrastructure drift
- Use cost estimation before deployment

## Learning Resources

- [Terraform Best Practices](https://www.terraform-best-practices.com/) - Community-maintained guide
- [HashiCorp Learn](https://learn.hashicorp.com/terraform) - Official Terraform tutorials
- [AWS Architecture Center](https://aws.amazon.com/architecture/) - Reference architectures
- [GCP Cloud Architecture Center](https://cloud.google.com/architecture) - GCP best practices
- [Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/) - Azure guidance 