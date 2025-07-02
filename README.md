
#  Secure AWS VPC Setup with Bastion Host and Private EC2

##  Overview

This project implements a **secure Virtual Private Cloud (VPC)** on AWS with **network segmentation**, **least privilege SSH access**, and **infrastructure hardening** using native AWS resources. It simulates real-world cloud security design patterns to protect internal workloads while maintaining controlled access via a bastion host.

---

##  Architecture Diagram

> A secure AWS VPC design where a bastion host resides in a public subnet and accesses a private EC2 instance through internal networking only.

![VPC Architecture](./assets/vpc-architecture.png)

---

##  Project Goals

- Deploy a custom AWS VPC with **public** and **private** subnets  
- Implement a **bastion host** in the public subnet for SSH tunneling  
- Launch an **internal EC2 instance** in the private subnet  
- Restrict SSH access using **Security Groups** and **Network ACLs**
- Enforce **principle of least privilege** for secure cloud networking

---

##  Technologies Used

- AWS EC2, VPC, Subnets, IGW, Route Tables
- Security Groups & Network ACLs (NACLs)
- SSH (OpenSSH on Linux)
- Amazon Linux 2 AMI
- (Optional Enhancements: CloudTrail, Flow Logs)

---

##  Implementation Summary# 🔐 Secure AWS VPC Setup with Bastion Host and Private EC2

## 📘 Overview

This project implements a **secure Virtual Private Cloud (VPC)** on AWS with **network segmentation**, **least privilege SSH access**, and **infrastructure hardening** using native AWS resources. It simulates real-world cloud security design patterns to protect internal workloads while maintaining controlled access via a bastion host.

---

## 🧱 Architecture Diagram

> A secure AWS VPC design where a bastion host resides in a public subnet and accesses a private EC2 instance through internal networking only.

![VPC Architecture]()

---

## 🎯 Project Goals

- Deploy a custom AWS VPC with **public** and **private** subnets  
- Implement a **bastion host** in the public subnet for SSH tunneling  
- Launch an **internal EC2 instance** in the private subnet  
- Restrict SSH access using **Security Groups** and **Network ACLs**
- Enforce **principle of least privilege** for secure cloud networking

---

## 🛠️ Technologies Used

- AWS EC2, VPC, Subnets, IGW, Route Tables
- Security Groups & Network ACLs (NACLs)
- SSH (OpenSSH on Linux)
- Amazon Linux 2 AMI
- (Optional Enhancements: CloudTrail, Flow Logs)

---

## 🧪 Implementation Summary

### 1. VPC & Subnets
- Created VPC: `10.0.0.0/16`
- Public Subnet: `10.0.1.0/24` with IGW
- Private Subnet: `10.0.2.0/24` without IGW

### 2. Bastion Host (Public Subnet)
- EC2 instance with **public IP**
- Security Group allows **SSH (port 22)** only from my IP
- Used to tunnel into private subnet

### 3. Internal EC2 (Private Subnet)
- EC2 instance with **no public IP**
- Security Group allows **SSH only from bastion’s SG**
- Completely isolated from the internet

### 4. SSH Workflow

```bash
# Step 1: Connect to Bastion Host
ssh -i mykey.pem ec2-user@<bastion-public-ip>

# Step 2: From Bastion, SSH to Private EC2
ssh -i mykey.pem ec2-user@<private-ec2-private-ip>


### 1. VPC & Subnets
- Created VPC: `10.0.0.0/16`
- Public Subnet: `10.0.1.0/24` with IGW
- Private Subnet: `10.0.2.0/24` without IGW

### 2. Bastion Host (Public Subnet)
- EC2 instance with **public IP**
- Security Group allows **SSH (port 22)** only from my IP
- Used to tunnel into private subnet

### 3. Internal EC2 (Private Subnet)
- EC2 instance with **no public IP**
- Security Group allows **SSH only from bastion’s SG**
- Completely isolated from the internet

### 4. SSH Workflow

```bash
# Step 1: Connect to Bastion Host
ssh -i mykey.pem ec2-user@<bastion-public-ip>

# Step 2: From Bastion, SSH to Private EC2
ssh -i mykey.pem ec2-user@<private-ec2-private-ip>
