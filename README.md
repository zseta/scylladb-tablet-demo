# ScyllaDB Tablets demo
This ScyllaDB demo shows you how ScyllaDB handles 1M ops/sec workload while scaling out from 3 nodes to 6 nodes and back with tablets.

## Infrastructure elements
* Amazon Web Services (AWS) EC2 instances

## Prerequisites
* AWS account and CLI credentials (more information on acquiring the credentials [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) and [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html), for OKTA you can use [gimme-aws-creds](https://github.com/Nike-Inc/gimme-aws-creds))
* Terraform installed on your machine (installation instructions [here](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli))

### AWS permissions
Make sure that you have sufficient AWS permissions to create the following items:
* VPC
* Subnets
* Security groups
* EC2 instances


## Get started
Clone the repository:
```
git clone <repo>
cd repo/
```

First, set the required items in `variables.tf`:
```terraform
#
# Set the following variables (mandatory)
#

# ScyllaDB Cloud API token
variable "scylla_cloud_token" {
  description = "ScyllaDB Cloud API token"
  type        = string
  default     = "ADD-YOUR-API-TOKEN-HERE"
}

# ScyllaDB Cloud region
variable "scylla_cloud_region" {
  description = "ScyllaDB Cloud region of the cluster"
  type        = string
  default     = "eu-north-1"
}

# SSH private key for EC2 instance access
variable "ssh_private_key" {
  description = "SSH private key location for EC2 instance access"
  type        = string
  default     = "/home/user/Documents/your-private-key.pem"
}

variable "aws_key_pair" {
  description = "Key pair name in AWS"
  type        = string
  default     = "my-key-pair"
}

# AWS credentials file
variable "aws_creds" {
  description = "AWS credentials location"
  type        = string
  default     = "/home/user/.aws/credentials"
}
```

Start setting up infrastructure with Terraform:
```bash
terraform init
terraform plan
terraform apply

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

[...]

Apply complete! Resources: 23 added, 0 changed, 0 destroyed.
```

Setting up the infrastructure takes YX minutes. Once Terraform is finished do X Y Z


After finishing the demo, destroy the infrastructure:
```
terraform destroy
```




