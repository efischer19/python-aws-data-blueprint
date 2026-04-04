# Infrastructure

This directory contains [Terraform](https://www.terraform.io/) configuration
for provisioning AWS infrastructure. See
[ADR-016](../meta/adr/ADR-016-terraform_iac.md) for the decision to use
Terraform and [ADR-015](../meta/adr/ADR-015-aws_cloud_provider.md) for the
choice of AWS as cloud provider.

## Directory Structure

```text
infrastructure/
├── main.tf          # Primary resource definitions
├── variables.tf     # Input variables
├── outputs.tf       # Output values
├── providers.tf     # AWS provider configuration
├── backend.tf       # Remote state backend (S3 + DynamoDB)
└── modules/         # Reusable Terraform modules
    └── README.md
```

## Getting Started

1. **Install Terraform:** Follow the
   [official installation guide](https://developer.hashicorp.com/terraform/install).
2. **Replace placeholders:** Search for `{{...}}` values and replace them with
   your real AWS configuration.
3. **Initialize:** `terraform init`
4. **Preview changes:** `terraform plan`
5. **Apply changes:** `terraform apply`

## Placeholder Values

| Placeholder | Description | Example |
| :--- | :--- | :--- |
| `{{AWS_ACCOUNT_ID}}` | Your AWS account ID | `123456789012` |
| `{{AWS_REGION}}` | Target AWS region | `us-east-1` |
| `{{TF_STATE_BUCKET}}` | S3 bucket for Terraform state | `my-project-tf-state` |
| `{{TF_LOCK_TABLE}}` | DynamoDB table for state locking | `my-project-tf-lock` |
| `{{PROJECT_NAME}}` | Your project name | `my-data-project` |

> **Note:** Never commit real AWS account IDs, ARNs, or credentials to version
> control.
