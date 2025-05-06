# AWS Tools and Resources

Tools, services, and resources for working with Amazon Web Services

## General Resources

- [AWS IP Ranges](https://ip-ranges.amazonaws.com/ip-ranges.json) - Official AWS IP address ranges in JSON format
- [AWS Status Dashboard Alternative](https://stop.lying.cloud/) - Third-party AWS status monitoring
- [AWS Quick Start Examples](https://github.com/aws-quickstart) - Reference deployments for AWS
- [EC2 Instance Comparison](https://www.ec2instances.info/) - Compare EC2 instance types and pricing
- [Compute Cost Comparison](https://compute-cost.com/) - Find the best price for AWS compute
- [AWS Security Best Practices](https://asecure.cloud/) - Repository of AWS security configurations and best practices

## IAM & Security

### IAM Tools

- [AWS IAM Actions Reference](https://www.awsiamactions.io/) - Complete list of IAM actions
- [IAM Policy Generator](https://github.com/iann0036/iamlive) - Generate IAM policies from AWS calls
- [IAM Policy Simulator](https://policysim.aws.amazon.com/home/index.jsp) - Test IAM policies
- [IAM Policy JSON to Terraform](https://github.com/flosell/iam-policy-json-to-terraform) - Convert IAM policies to Terraform

### Authentication & Role Management

- [AWS Vault](https://github.com/99designs/aws-vault) - Securely store and access AWS credentials
- [Leapp](https://github.com/Noovolari/leapp) - Cross-platform AWS temporary credentials manager
- [Granted](https://docs.commonfate.io/granted/getting-started) - SSO + Role assume + Multi-account support
- [AWS Extend Switch Roles](https://github.com/tilfinltd/aws-extend-switch-roles) - Browser extension for switching roles
- [Console Me](https://github.com/Netflix/consoleme) - Netflix's tool to simplify IAM access
- [AWS-ADFS](https://github.com/venth/aws-adfs/) - Authentication for Active Directory or DUO
- [Gimme AWS Creds](https://github.com/Nike-Inc/gimme-aws-creds) - Okta-based AWS credential retrieval
- [SAML2AWS](https://github.com/Versent/saml2aws) - CLI tool for SAML authentication

## S3 Tools

- [Rclone](https://rclone.org/) - Command line program to manage files on cloud storage
  - Delete versioned bucket: `rclone purge --verbose s3:my-versioned-bucket`
- [S3Gof3r](https://github.com/y0zg/s3gof3r) - Fast, parallelized streaming access to S3
- [S5cmd](https://github.com/peak/s5cmd) - Parallel S3 command line tool

## Infrastructure Management

- [LocalStack](https://github.com/localstack/localstack) - Local AWS cloud stack for development and testing
- [AWS CLI Console Plugin](https://github.com/b-b3rn4rd/awscli-console-plugin) - Generate console URLs from CLI credentials
- [AWS-Gate](https://github.com/xen0l/aws-gate) - Better AWS Session Manager CLI
- [Let Me In](https://github.com/rlister/let-me-in) - Add your IP to AWS security groups
- [Finala](https://github.com/similarweb/finala) - Cost optimization tool

## EKS

- [EKS Best Practices](https://github.com/aws/aws-eks-best-practices) - Official AWS EKS best practices
- [Kubernetes Best Practices](https://github.com/y0zg/kubernetes-best-practices) - General K8s best practices
- [K8s Instance Calculator](https://learnk8s.io/kubernetes-instance-calculator) - Calculate instance types for K8s workloads
- [EKS IAM Auth Controller](https://github.com/rustrial/aws-eks-iam-auth-controller) - Controller for managing aws-auth ConfigMap
- [EKS Auth Sync](https://gitlab.com/y0zg/eks-auth-sync) - Synchronize IAM roles with Kubernetes RBAC

## ECS

- [E1S](https://github.com/keidarcy/e1s) - Terminal UI for ECS (similar to K9s for Kubernetes)
- [Bottlerocket](https://github.com/bottlerocket-os/bottlerocket) - AWS purpose-built container OS
- [ECS Deploy](https://github.com/silinternational/ecs-deploy) - Deployment tool for ECS
- [UFO Ships](https://ufoships.com/) - ECS deployment tool

## Security & Analysis

- [Cloud Custodian](https://cloudcustodian.io/docs/index.html) - Rules engine for cloud security
- [CloudTrail CloudWatch Alarms](https://github.com/cloudposse/terraform-aws-cloudtrail-cloudwatch-alarms) - Security monitoring
- [Stratus Red Team](https://github.com/DataDog/stratus-red-team) - AWS attack simulation
- [CloudMapper](https://github.com/duo-labs/cloudmapper) - Analyze AWS infrastructure
- [AWS Perspective](https://github.com/awslabs/aws-perspective) - Visualize your AWS infrastructure
- [AWS Security Viz](https://github.com/anaynayak/aws-security-viz) - Visualize security groups
- [Enumerate IAM](https://github.com/andresriancho/enumerate-iam) - Brute force permission discovery

## Remote Access & Bastions

- [Cloudflared](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/do-more-with-tunnels/trycloudflare/) - Secure tunneling
- [Bastion](https://github.com/cloudposse/bastion) - Secure bastion with MFA
- [Socat Tunneller](https://github.com/y0zg/stable-charts/tree/master/stable/socat-tunneller) - TCP tunneling
- [Port7777](https://port7777.com/) - Fargate-based remote database access

## Cost Management

- [Vantage.sh](https://vantage.sh/) - Cloud cost management platform
- [CloudHealth](https://www.cloudhealthtech.com/) - Cloud management platform
- [CloudZero](https://www.cloudzero.com/) - Cloud cost intelligence
- [Cloudability](https://www.apptio.com/products/cloudability/) - FinOps solutions

## Feeds & Monitoring

- [AWS Status RSS](http://status.aws.amazon.com/rss/all.rss) - AWS service status
- [AWS News Feed](https://aws.amazon.com/new/feed/) - AWS news and updates
- [AWS Security Bulletins](https://aws.amazon.com/security/security-bulletins/feed) - Security bulletins

## AWS Resource Cleanup

- [AWS Nuke](https://github.com/rebuy-de/aws-nuke) - Account cleanup tool

## Secrets Management

- [External Secrets](https://github.com/godaddy/kubernetes-external-secrets) - K8s integration with external secret management
- [SOPS](https://github.com/mozilla/sops) - Secrets encryption with multi-provider support
- [Kubernetes Secrets Init](https://github.com/doitintl/kube-secrets-init) - Secrets initialization

## Benchmarking & Testing

- [FIO Tool](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/benchmark_procedures.html) - Storage benchmarking
- [EC2 Benchmarks](https://browser.geekbench.com/v6/cpu/compare/4016859?baseline=4353636) - Instance performance 