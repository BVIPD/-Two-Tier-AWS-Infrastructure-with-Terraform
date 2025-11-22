# -Two-Tier-AWS-Infrastructure-with-Terraform

## 📌 Project Overview

This project demonstrates the automated deployment of a secure, scalable, and modular two-tier architecture on AWS using Terraform. All Terraform commands, modules, and infrastructure provisioning were executed completely inside **Google Colab**, making the project portable, cloud-based, and easy to reproduce.

The architecture consists of:

* **Frontend Tier:** EC2 instance hosted in a **public subnet**
* **Backend Tier:** MySQL RDS instance hosted in a **private subnet**
* **Networking Layer:** VPC, subnets, routing, and Internet Gateway
* **IaC Automation:** Fully modular Terraform configuration

---

## 🏗️ Architecture Diagram (Conceptual)

```
             ┌──────────────────────────────┐
             │          Google Colab         │
             │   (Terraform Execution Env)   │
             └───────────────┬──────────────┘
                             │
                             ▼
                    Terraform (IaC)
                             │
                             ▼
   ┌─────────────────────────────────────────────────────┐
   │                         AWS                         │
   │                                                     │
   │     ┌──────────────┐        ┌────────────────┐      │
   │     │  Public Subnet│        │ Private Subnet │      │
   │     │   EC2 Server  │◀──────▶│   RDS MySQL   │      │
   │     └──────────────┘        └────────────────┘      │
   │                                                     │
   │                 VPC + Routing + IGW                 │
   └─────────────────────────────────────────────────────┘
```

---

## 🎯 Key Features

* **Infrastructure as Code (IaC)** using Terraform
* **Google Colab execution** for all Terraform operations
* Modular design with separate modules for:

  * VPC
  * EC2
  * RDS
* Secure **two-tier architecture** (frontend + backend separation)
* Automated provisioning of:

  * VPC with public/private subnets
  * EC2 instance
  * RDS MySQL database
* Output values: VPC ID, EC2 Public IP, RDS Endpoint
* Easy to reuse, modify, or scale



## 📁 Project Structure

```
aws_two_tier/
│
├── main.tf
├── variables.tf
├── outputs.tf
│
├── modules/
│   ├── vpc/
│   │   ├── main.tf
│   │   └── variables.tf
│   │
│   ├── ec2/
│   │   ├── main.tf
│   │   └── variables.tf
│   │
│   └── rds/
│       ├── main.tf
│       └── variables.tf
│
└── README.md
```



## 🧠 How to Run in Google Colab

### 1️⃣ Install Terraform

```bash
!apt-get install unzip -y
!wget https://releases.hashicorp.com/terraform/1.7.5/terraform_1.7.5_linux_amd64.zip
!unzip terraform_1.7.5_linux_amd64.zip
!mv terraform /usr/local/bin/
!terraform -version
```

### 2️⃣ Create Project Folders

```bash
!mkdir -p aws_two_tier/modules/{vpc,ec2,rds}
%cd aws_two_tier
```

### 3️⃣ Add Terraform Files

Paste the provided **main.tf**, **modules**, and variables exactly as in your project.

### 4️⃣ Initialize Terraform

```bash
!terraform init
```

### 5️⃣ Validate Configuration

```bash
!terraform validate
```

### 6️⃣ Optional: View Execution Plan

```bash
!terraform plan -no-color
```

### 7️⃣ Optional: Apply the Infrastructure

Requires AWS credentials:

```bash
!terraform apply -auto-approve
```


## 📊 Outputs After Deployment

Terraform automatically prints:

* **VPC ID**
* **EC2 Public IP**
* **RDS Endpoint**
These values can be used for testing or connecting applications.



## 📚 Technologies Used

* **Terraform** (IaC tool)
* **AWS Services**: VPC, EC2, RDS
* **Google Colab** for execution
* **Linux shell environment** via Colab



## 🧪 Results

* Terraform successfully initialized and validated in Google Colab
* Modules executed correctly
* Plan generated accurate AWS resource creation
* Optional: Full infrastructure deployed on AWS
* Outputs verified (EC2 Public IP, RDS Endpoint)



## 🔮 Future Enhancements

* Add **Security Groups**
* Integrate **Application Load Balancer**
* Add **Auto Scaling Group**
* Store secrets in **AWS Secrets Manager**
* Implement **CI/CD** with GitHub Actions or Terraform Cloud
* Convert architecture to **3-tier** or migrate to **ECS/EKS**


## 📄 References

* Terraform Docs: [https://developer.hashicorp.com/terraform/docs](https://developer.hashicorp.com/terraform/docs)
* AWS Docs: [https://docs.aws.amazon.com/](https://docs.aws.amazon.com/)
* Terraform AWS Provider: [https://registry.terraform.io/providers/hashicorp/aws/latest](https://registry.terraform.io/providers/hashicorp/aws/latest)
* Google Colab: [https://research.google.com/colaboratory/](https://research.google.com/colaboratory/)
