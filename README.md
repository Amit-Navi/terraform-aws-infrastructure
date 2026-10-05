

# Terraform AWS Infrastructure Provisioning

Infrastructure as Code (IaC) project that provisions a repeatable AWS infrastructure environment using **Terraform**. The project demonstrates how cloud infrastructure can be defined, version-controlled, planned, and provisioned through declarative configuration instead of manual AWS Console setup.

## Project Overview

This project provisions a basic AWS infrastructure environment consisting of:

- Amazon VPC
- Public Subnet
- Internet Gateway
- Route Table
- Route Table Association
- Security Group
- EC2 Instance
- Linux web server with Nginx

The infrastructure is defined using Terraform configuration files so that the environment can be recreated consistently and maintained through version control.

## Architecture

```text
                    Internet
                       |
                       |
              Internet Gateway
                       |
                       |
                Public Subnet
                       |
                  EC2 Instance
                       |
                    Nginx
                       |
                 Web Server
                       
        ┌─────────────────────────┐
        │       AWS VPC           │
        │                         │
        │   Public Subnet         │
        │        │                │
        │        └── EC2          │
        │             │           │
        │           Nginx          │
        │                         │
        │   Route Table           │
        │        │                │
        │   Internet Gateway      │
        └─────────────────────────┘
```

## Technologies Used

| Technology | Purpose |
|---|---|
| Terraform | Infrastructure as Code and infrastructure provisioning |
| AWS | Cloud infrastructure platform |
| VPC | Network isolation |
| Subnet | Network segmentation |
| Internet Gateway | Internet connectivity |
| Route Table | Network traffic routing |
| Security Group | Instance-level network access control |
| EC2 | Compute infrastructure |
| Linux | Server operating system |
| Nginx | Web server |
| Git | Version control |

## Key Terraform Concepts Demonstrated

This project focuses on practical Terraform and IaC concepts, including:

- Terraform providers
- Resource definitions
- Input variables
- Outputs
- Variable validation
- Resource dependencies
- Terraform plan and apply workflow
- Infrastructure lifecycle management
- Reusable configuration
- Version-controlled infrastructure
- Declarative infrastructure provisioning

## Infrastructure Components

### 1. VPC

Creates an isolated AWS network environment for the infrastructure.

### 2. Public Subnet

Creates a subnet within the VPC where the EC2 instance is deployed.

### 3. Internet Gateway

Provides a path between the VPC and the public internet.

### 4. Route Table

Defines routing rules for traffic from the public subnet.

### 5. Security Group

Controls inbound and outbound network traffic for the EC2 instance.

The configuration follows the principle of allowing only the traffic required by the application.

### 6. EC2 Instance

Creates the compute environment inside the configured AWS network.

### 7. Nginx

Configures an Nginx web server on the Linux EC2 instance to demonstrate application-level provisioning on top of infrastructure provisioning.

## Project Structure

```text
terraform-aws-infrastructure/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── provider.tf
├── terraform.tfvars.example
├── .gitignore
└── README.md
```

### File Responsibilities

**`provider.tf`**

Defines the AWS provider and Terraform configuration.

**`main.tf`**

Contains the primary AWS infrastructure resources such as:

- VPC
- Subnet
- Internet Gateway
- Route Table
- Security Group
- EC2

**`variables.tf`**

Defines configurable input variables used by the infrastructure.

**`outputs.tf`**

Defines useful infrastructure outputs such as resource identifiers and server information.

**`terraform.tfvars.example`**

Provides an example of configurable values without exposing personal or sensitive information.

**`.gitignore`**

Prevents Terraform state files, local configuration, credentials, and other sensitive files from being committed to Git.

## How It Works

The project follows a standard Infrastructure as Code workflow:

```text
Terraform Configuration
          ↓
   terraform init
          ↓
   terraform validate
          ↓
     terraform plan
          ↓
     terraform apply
          ↓
   AWS Infrastructure
          ↓
     EC2 + Nginx
```

### Step 1 — Initialize Terraform

```bash
terraform init
```

Initializes Terraform and downloads the required provider plugins.

### Step 2 — Validate Configuration

```bash
terraform validate
```

Checks whether the Terraform configuration is syntactically valid and internally consistent.

### Step 3 — Review Infrastructure Changes

```bash
terraform plan
```

Creates an execution plan showing the infrastructure Terraform intends to create or modify.

### Step 4 — Provision Infrastructure

```bash
terraform apply
```

Applies the Terraform configuration and provisions the required AWS resources.

### Step 5 — View Outputs

```bash
terraform output
```

Displays the configured Terraform outputs.

### Step 6 — Destroy Resources

When the environment is no longer required:

```bash
terraform destroy
```

Removes the infrastructure managed by Terraform.

## Security Considerations

This repository is designed so that sensitive credentials are not stored in source control.

The following should **never** be committed:

```text
*.tfstate
*.tfstate.*
.terraform/
*.tfvars
credentials
AWS access keys
private keys
```

AWS credentials should be provided through an appropriate local AWS authentication mechanism rather than hard-coded inside Terraform configuration.

## What I Learned

This project helped me understand the practical relationship between cloud infrastructure and Infrastructure as Code.

Key areas explored include:

- Designing basic AWS network infrastructure
- Provisioning AWS resources through Terraform
- Managing dependencies between infrastructure resources
- Using variables and outputs for reusable configuration
- Reviewing changes through `terraform plan`
- Applying infrastructure changes through `terraform apply`
- Configuring Linux infrastructure after provisioning
- Managing infrastructure configuration through Git
- Understanding the difference between manual cloud configuration and declarative infrastructure

## Future Improvements

Possible extensions to this project include:

- Private subnet architecture
- NAT Gateway
- Application Load Balancer
- Auto Scaling Group
- IAM roles with least-privilege permissions
- Remote Terraform state management
- State locking
- Multiple environments such as development and production
- Terraform modules
- CI/CD pipeline for Terraform validation and deployment
- Infrastructure monitoring and logging

## Disclaimer

This project is intended for learning and demonstration purposes. AWS resources may incur charges depending on the configuration and usage. Review and destroy resources when they are no longer required.

## Author

**Amit Navi**

- LinkedIn: https://linkedin.com/in/amit-navi-49843723b
- GitHub: https://github.com/Amit-Navi
