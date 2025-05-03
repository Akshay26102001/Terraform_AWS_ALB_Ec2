<<<<<<< HEAD
# 🌐 Highly Available Web Server Deployment Using Terraform on AWS

This project automates the deployment of a **highly available**, **scalable**, and **fault-tolerant** web server infrastructure using **Terraform** on **Amazon Web Services (AWS)**.

It provisions essential networking components, security configurations, EC2 instances, and an Application Load Balancer (ALB) to distribute traffic across multiple Availability Zones.

---

## 🏗️ Architecture Diagram (Conceptual)

Internet
│
▼
[ Application Load Balancer ]
│
┌───┴────────────┐
▼ ▼
[ EC2 Instance ] [ (More EC2 in future) ]
│
▼
Public Subnets (AZ-a & AZ-b)
│
▼
VPC


---

## 🧩 Key Components & Purpose

### 1. **Networking**
- `aws_vpc.india_vpc` – Custom Virtual Private Cloud.
- `aws_subnet.public_subnet_a/b` – Public subnets in different Availability Zones.
- `aws_internet_gateway.igw` – Enables internet access.
- `aws_route_table` – Routes public traffic via IGW.

### 2. **Security Groups**
- `alb_sg` – Allows HTTP (port 80) traffic from the internet.
- `ec2_sg` – Restricts access to EC2 only via ALB.

### 3. **Compute**
- `aws_instance.web` – EC2 instance with Apache serving a static HTML page (`Hello from EC2`).

### 4. **Load Balancer**
- `aws_lb.alb` – ALB distributes HTTP traffic.
- `aws_lb_target_group.tg` – Group of EC2 targets.
- `aws_lb_listener.http_listener` – Listens on port 80 and forwards to the target group.

### 5. **High Availability**
- Deployed in two AZs with health checks to ensure resilience.

---

## ✅ Use Cases / Benefits

- ✅ **Highly Available Website** — Runs across two AZs.
- ✅ **Scalable** — Easily add more EC2 instances.
- ✅ **Secure** — Traffic only allowed via ALB.
- ✅ **Infrastructure as Code** — Easy to version, replicate, and maintain.
- ✅ **No Manual Setup** — Complete automation with `terraform apply`.

---

## 📦 Prerequisites

- [x] AWS account
- [x] IAM user with programmatic access
- [x] AWS CLI configured (`aws configure`)
- [x] Terraform installed (>= 1.0)
- [x] SSH Key Pair (already uploaded to AWS)

---

## 🚀 How to Deploy
When Using Git in your Project
### 1. **Clone the repository**
```bash
git clone https://github.com/yourusername/terraform-aws-alb.git
cd terraform-aws-alb
### 1. **When you are using local machine or laptop**

📁 Folder Structure

terraform-aws-alb/
├── main.tf(your terraform code paste here)
       
This Is Mandatory
**Initialize Terraform**
--terraform init

**Preview the changes**
--terraform plan

**Apply and deploy**
--terraform apply
----->Type **yes** when prompted.



🌐 Access the Web Server
After successful deployment, Terraform will output the ALB DNS name.
Visit it in your browser to see:

**Hello from EC2**



🧹 How to Destroy the Infrastructure
To tear down all AWS resources created by this Terraform project:
----terraform destroy

=======
🚀 AWS ALB + EC2 with WAF (India Only) - Terraform Setup

This project deploys a complete AWS environment using Terraform:

A VPC with public subnets

EC2 instance with Apache Web Server

Application Load Balancer (ALB)

AWS WAF to allow only India-based traffic

Security groups and routing

Auto installation of Apache on EC2



📦 Prerequisites
Before you begin, make sure you have:

✅ Terraform installed

✅ AWS CLI configured with credentials (aws configure)

✅ A valid EC2 key pair in ap-south-1 region (used in key_name = "personal")


🏗️ Setup Steps

1. Clone the Repository
git clone <your-repo-url>
cd <your-repo-directory>

2. Initialize Terraform
terraform init

3. Preview the Infrastructure
terraform plan

4. Apply the Configuration
terraform apply

When prompted, type "yes" to approve the deployment.

💡 Note: This may take a few minutes to complete.


🌐 Access Your Web Application
Once the deployment is done, Terraform will output resources.

🔍 Find the ALB DNS Name
To get the ALB DNS:

aws elbv2 describe-load-balancers \
  --names india-alb \
  --region ap-south-1 \
  --query "LoadBalancers[0].DNSName"


Or go to the AWS Console > EC2 > Load Balancers and copy the DNS name of india-alb.

🔗 Visit in Browser
Open the following in your browser:

http://<alb-dns-name>/index.html

If you're accessing from outside India, you will be blocked by WAF. You can test using a VPN set to an Indian IP.


🔒 WAF Protection (India Only)
This project includes a WAFv2 ACL that only allows HTTP traffic originating from India ("IN" country code).

🧹 Cleanup
To destroy all AWS resources:

terraform destroy


📁 File Structure
.
├── main.tf            # Full Terraform configuration
├── README.md          # This guide

✍️ Author
Akshay Pratap Upadhyay
Cloud Engineer | Web Developer
>>>>>>> e300e8d (Initial commit - Terraform Web Server with WAF Access Prevent)
