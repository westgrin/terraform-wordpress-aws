# Terraform Capstone Project - Automated WordPress Deployment on AWS (Local Setup)

## Project Overview
This project automates a scalable, secure WordPress deployment on AWS using Terraform modules for VPC, RDS, EFS, ALB, and Auto Scaling. It includes a live WordPress site and auto-scaling demonstration. Builds on previous Terraform projects (Jul 8-12, 2025).

## Setup
- Initiated on Jul 13, 2025, 7:32 AM WAT.
- Used WSL Ubuntu, VS Code, and Git Bash in `C:\Users\Abraham\Documents\Workspace\terraform-wordpress-aws`.
- System: 2 CPUs, 2GB free memory, 20GB free disk space.

## Security Measures
- **VPC**: Isolated resources in a custom VPC with public/private subnets.
- **RDS**: Private subnet placement, security group restricts access to EC2.
- **EFS**: Encrypted file system, restricted to EC2 security group.
- **ALB**: Public access restricted to port 80, integrated with Auto Scaling.
- **EC2/Auto Scaling**: SSH restricted, auto-scaling policies for CPU usage.
- **Sensitive Data**: DB password stored as Terraform variable and GitHub Secret.

## Execution Steps
1. **Confirm Prerequisites**:
   - Verified AWS CLI, Terraform, and SSH key.
   - [Screenshot: `aws_prerequisites_output_local.png` - Shows AWS CLI verification.]
   - [Screenshot: `ssh_key_output_local.png` - Shows SSH key verification.]
2. **Create Terraform Modules**:
   - VPC: Defined VPC, subnets, NAT Gateway.
   - RDS: MySQL instance in private subnets.
   - EFS: Shared file system for WordPress files.
   - EC2/Auto Scaling: EC2 instances with WordPress and auto-scaling.
   - ALB: Load balancer for high availability.
3. **Deploy with Terraform**:
   - Ran `terraform init`, `validate`, `plan`, and `apply`.
   - [Screenshot: `terraform_init_output_local.png` - Shows initialization.]
   - [Screenshot: `terraform_validate_output_local.png` - Shows validation.]
   - [Screenshot: `terraform_plan_output_local.png` - Shows plan output.]
   - [Screenshot: `terraform_apply_output_local.png` - Shows apply output.]
4. **Access WordPress**:
   - Configured WordPress at `http://<alb-dns-name>`.
   - [Screenshot: `wordpress_site_output_local.png` - Shows WordPress site.]
   - [Screenshot: `aws_resources_output_local.png` - Shows AWS resources.]
5. **Demonstrate Auto-Scaling**:
   - Simulated CPU load with `stress` to trigger scale-up.
   - [Screenshot: `autoscaling_output_local.png` - Shows scaled instances.]
   - Stopped load to trigger scale-down.
   - [Screenshot: `autoscaling_down_output_local.png` - Shows scaled-down instances.]
6. **Clean Up**:
   - Ran `terraform destroy` to remove resources.
   - [Screenshot: `terraform_destroy_output_local.png` - Shows destroy output.]
7. **Side Hustle Task**:
   - Automated deployment with GitHub Actions.
   - Pushed to `https://github.com/westgrin/terraform-wordpress-aws`.
   - [Screenshot: `github_actions_terraform_run_local.png` - Shows workflow run.]

## Learning Summary
This project advanced my skills in Terraform, AWS, and WordPress deployment, building on my previous Terraform and Kubernetes projects (Jul 8-12, 2025). It reinforced modular infrastructure, auto-scaling, and security practices, aligning with my DevOps goals (June 16, 2025).

## Tools Used
- **WSL Ubuntu Terminal**: For AWS CLI and Terraform commands.
- **VS Code**: For editing Terraform files and `README.md`.
- **Git Bash**: For GitHub operations.
- **GitHub Actions**: For deployment automation.
- **Terraform**: For infrastructure as code.
- **AWS CLI**: For AWS authentication.

## Project Deliverables
- **Documentation**: This `README.md` with steps, security measures, and learning summary.
- **Screenshots**:
  - `aws_prerequisites_output_local.png`
  - `ssh_key_output_local.png`
  - `terraform_init_output_local.png`
  - `terraform_validate_output_local.png`
  - `terraform_plan_output_local.png`
  - `terraform_apply_output_local.png`
  - `wordpress_site_output_local.png`
  - `aws_resources_output_local.png`
  - `autoscaling_output_local.png`
  - `autoscaling_down_output_local.png`
  - `terraform_destroy_output_local.png`
  - `github_actions_terraform_run_local.png`
- **Script Link**: [GitHub Repository](https://github.com/westgrin/terraform-wordpress-aws)

## Local Development Instructions
1. Clone repository: `git clone https://github.com/westgrin/terraform-wordpress-aws.git`
2. Configure AWS CLI: `aws configure`
3. Initialize Terraform: `terraform init`
4. Validate script: `terraform validate`
5. Plan execution: `terraform plan -var="db_password=YourSecurePassword123"`
6. Apply configuration: `terraform apply -var="db_password=YourSecurePassword123"`
7. Access WordPress: `http://<alb-dns-name>`
8. Demonstrate auto-scaling with `stress`
9. Destroy resources: `terraform destroy -var="db_password=YourSecurePassword123"`

## Troubleshooting
- Ensured valid AMI ID for `us-east-1` using AWS CLI or Console.
- Fixed AWS CLI authentication with `aws configure`.
- Set DNS to `8.8.8.8` for network issues.
- Verified system resources with `lscpu`, `free -h`, `df -h`.
- Checked RDS connectivity with `mysql -h <rds-endpoint> -u admin -p`.

## Conclusion
This project successfully deployed a scalable, secure WordPress site on AWS with Terraform, demonstrated auto-scaling, and implemented automation, enhancing my skills in cloud infrastructure and DevOps.