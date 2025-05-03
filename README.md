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

