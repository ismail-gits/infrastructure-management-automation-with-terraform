# Infrastructure Managment Automation With Terraform

## Overview
This project aims to automate the deployment of infrastructure components on Amazon Web Services (AWS) using Terraform. It streamlines the provisioning of EC2 instances, management of Virtual Private Cloud (VPC) resources, and establishment of an Amazon Elastic Kubernetes Service (EKS) cluster. Additionally, it configures Kubernetes resources to deploy a basic NGINX server. This README provides an in-depth understanding of the project structure, configurations, and usage.

## Directory Structure

```plaintext
infrastructure-management-automation-with-terraform/
│
├── aws-ec2-automation/
│   ├── entry-script.sh
│   ├── main.tf
│   ├── terraform.tfvars
│   └── README.md
│
├── aws-ec2-module-automation/
│   ├── modules/
│   │   ├── subnet/
│   │   │   ├── main.tf
│   │   │   ├── outputs.tf
│   │   │   └── variables.tf
│   │   └── webserver/
│   │       ├── main.tf
│   │       ├── outputs.tf
│   │       └── variables.tf
│   ├── outputs.tf
│   ├── variables.tf
│   └── README.md
│
└── aws-eks-automation/
    ├── main.tf
    ├── nginx-kubernetes-config.yaml
    ├── terraform.tfvars
    ├── vpc.tf
    └── README.md
```

### `aws-ec2-automation`
This directory focuses on Terraform configurations for provisioning EC2 instances.

- **`entry-script.sh`**: A Bash script executed on EC2 instances to initialize them with necessary software and configurations.
- **`main.tf`**: The primary Terraform configuration file defining AWS resources such as VPC, subnet, security group, key pair, and EC2 instance.
- **`terraform.tfvars`**: A variables file containing specific configurations like VPC CIDR block, subnet CIDR block, instance type, etc.

### `aws-ec2-module-automation`
This directory contains modularized Terraform configurations for EC2 instance provisioning, promoting reusability and maintainability.

- **`modules`**: A directory containing reusable modules for subnet and webserver configurations.
    - **`subnet`**: A module for subnet provisioning.
    - **`webserver`**: A module for EC2 instance provisioning.
- **`outputs.tf`**: Defines outputs for the modules, facilitating easy access to essential information.
- **`variables.tf`**: Defines variables used in the modules, ensuring consistency and flexibility in configurations.

### `aws-eks-automation`
This directory encompasses Terraform configurations for setting up an Amazon EKS cluster, a managed Kubernetes service.

- **`main.tf`**: The Terraform configuration file for EKS cluster setup, including configurations for cluster name, version, node groups, and tags.
- **`nginx-kubernetes-config.yaml`**: A Kubernetes configuration file specifying the deployment and service definitions for the NGINX server.
- **`terraform.tfvars`**: A variables file containing configurations for AWS region, VPC CIDR block, and subnet CIDR blocks.
- **`vpc.tf`**: A Terraform configuration file for VPC setup, ensuring the required networking infrastructure for the EKS cluster.

## Usage
1. Install Terraform on your local machine.
2. Clone this repository to your local environment.
3. Navigate to the directory of the component you want to deploy (`aws-ec2-automation` or `aws-eks-automation`).
4. Initialize Terraform with `terraform init`.
5. Review and update variables in `terraform.tfvars` to match your environment requirements.
6. Apply the Terraform configuration with `terraform apply`.
7. Monitor the Terraform execution and verify the resources created in your AWS console.

## Dependencies
- **Terraform**: The infrastructure as code tool used for defining and provisioning AWS resources.
- **AWS CLI**: Required for authentication and configuration of AWS credentials.