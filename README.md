# Automating Infrastructure Deployment Using Terraform

This repository demonstrates how to use Terraform to automate the deployment of Google Cloud infrastructure. The project deploys an auto mode network with a firewall rule and two VM instances.

## Project Overview

This project creates:
- One auto mode VPC network
- A firewall rule to allow HTTP, SSH, RDP, and ICMP traffic
- Two VM instances in different zones connected to the network

## Video 

https://youtu.be/FdxTlCYXBDs

## Prerequisites

- [Google Cloud Platform](https://cloud.google.com/) account
- [Terraform](https://www.terraform.io/downloads.html) (v1.5.7 or later)
- [Google Cloud SDK](https://cloud.google.com/sdk/docs/install)

## Project Structure

```
.
├── README.md
├── provider.tf          # Google Cloud provider configuration
├── mynetwork.tf         # Network and VM instance configurations
└── instance/            # VM instance module
    ├── main.tf          # VM instance resource definition
    └── variables.tf     # Input variables for the module
```

## How to Use This Repository

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/terraform-gcp-infrastructure.git
cd terraform-gcp-infrastructure
```

### 2. Initialize Terraform

```bash
terraform init
```

### 3. Create an Execution Plan

```bash
terraform plan
```

### 4. Apply the Configuration

```bash
terraform apply
```
Confirm by typing `yes` when prompted.

### 5. Verify Deployment

1. In the Google Cloud console, navigate to VPC Network > VPC Networks to verify network creation
2. Navigate to VPC Network > Firewall to verify firewall rule creation
3. Navigate to Compute Engine > VM Instances to verify VM instances creation
4. Test connectivity between instances using SSH and ping commands

### 6. Clean Up Resources (Optional)

To destroy all resources created by Terraform:

```bash
terraform destroy
```
Confirm by typing `yes` when prompted.

## Implementation Details

### Network Configuration

The configuration creates an auto mode VPC network, which automatically creates a subnet in each region. The firewall rule allows HTTP (port 80), SSH (port 22), RDP (port 3389), and ICMP traffic.

### VM Instance Module

The instance module is used to create VM instances with consistent configuration. The module takes the following input variables:
- `instance_name`: Name of the VM instance
- `instance_zone`: Zone where the VM instance is created
- `instance_type`: Machine type (defaults to e2-micro)
- `instance_network`: Network to which the VM instance is connected

## Key Concepts

- **Infrastructure as Code**: Define infrastructure using code for improved consistency and reusability
- **Modules**: Reusable Terraform configurations for creating similar resources
- **Resource Dependencies**: Using references like `self_link` to create resources in the proper order

## License

This project is licensed under the MIT License - see the LICENSE file for details.
