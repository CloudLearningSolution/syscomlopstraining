# Machine Learning Operations Playbook Adoption Workshop – Week 4: Network Configuration and VPC Setup - Hands-On Workshop

## Objectives

## Overview

This week focuses on network configuration and VPC setup for ML platforms. AWS labs provide high-level exploration, while Google Cloud labs deliver deep technical implementation.

## Prerequisites
### AWS Requirements

- AWS hands on demonstrated by presenter. Attendees do not require access.

### Google Cloud Requirements

- Google Cloud Console access with Network Admin role
- gcloud CLI installed and configured
- Vertex AI API enabled
- Billing account configured

# 🧪 Lab 4.1: AWS VPC Design and Implementation for SageMaker

**Objective:** Understand how Amazon SageMaker integrates with Amazon VPCs to isolate ML workloads and enable secure communication with AWS services.

---

## 1. Prerequisites

- AWS Console access with SageMaker and VPC permissions  
- No resource creation required (exploration-only)  
- Familiarity with basic VPC concepts: subnets, route tables, security groups  

---

## 2. Theory Overview

- SageMaker domains can be configured to run in **VPC-only mode** for full network isolation  
- You must specify subnets, security groups, and optionally VPC endpoints for services like S3 and CloudWatch  
- VPC-only mode disables public internet access and routes all traffic through your defined VPC  

---

## 3. Hands-On Exploration Steps

### 10. Navigate to SageMaker Domain Setup

- Go to [Amazon SageMaker Console](https://console.aws.amazon.com/sagemaker/)  
- Click **Domains** → **Create Domain** → Choose **Set up for organizations**

### 11. Review Network Configuration Options

- Under **Network**, select **VPC only**  
- Observe required fields:  
  - VPC ID  
  - Subnet IDs (must be private)  
  - Security Group IDs  

### 12. Explore VPC Console

- Open [Amazon VPC Console](https://console.aws.amazon.com/vpc/)  
- Review existing VPCs and subnets  
- Confirm subnet types (public vs private)  

---

## 4. Deliverables

- Notes of SageMaker domain network configuration  
- List of required VPC components for VPC-only mode  

---

## 5. Supplemental Materials

- [Choosing an Amazon VPC for SageMaker](https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-vpc.html)
 
# 🧪 Lab 4.2: Security Groups and Network ACLs for ML Workloads

**Objective:** Explore how security groups and network ACLs control traffic to ML workloads in Amazon VPCs.

---

## 1. Prerequisites

- AWS Console access with EC2 and VPC permissions  
- No instance launch required  

---

## 2. Theory Overview

- **Security Groups**: Stateful, instance-level firewalls  
- **Network ACLs**: Stateless, subnet-level firewalls  
- Security groups allow inbound/outbound rules per protocol and port  
- Network ACLs allow and deny rules based on CIDR, protocol, and port  

---

## 3. Hands-On Exploration Steps

### 4. Open EC2 Security Groups

- Go to [EC2 Console](https://console.aws.amazon.com/ec2/)  
- Click **Security Groups** → Select any group  

### 5. Review Inbound and Outbound Rules

- Note rules for ports like 22 (SSH), 443 (HTTPS), 8888 (Jupyter)  
- Observe CIDR ranges and protocol types  

### 6. Open VPC Network ACLs

- Go to [VPC Console](https://console.aws.amazon.com/vpc/)  
- Click **Network ACLs** → Select any ACL  

### 7. Compare ACL Rules

- Note allow/deny rules  
- Observe stateless behavior (return traffic must be explicitly allowed)  

---

## Deliverables

- Table comparing security group vs network ACL rules  
- Notes on rule behavior and ML workload implications  

---

## Supplemental Materials

- [Security Groups and Network ACLs Best Practices](https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/security-groups-and-network-acls-bp5.html)


# 🧪 Lab 4.3: VPC Endpoints and Private Connectivity Configuration

**Objective:** Explore how VPC interface endpoints enable private connectivity to SageMaker APIs and runtimes using AWS PrivateLink.

---

## 1. Prerequisites

- AWS Console access with VPC and SageMaker permissions  
- No endpoint creation required  

---

## 2. Theory Overview

- VPC endpoints allow private access to AWS services without internet exposure  
- SageMaker supports **interface endpoints** via AWS PrivateLink  
- Private DNS can be enabled to resolve SageMaker endpoints internally  

---

## 3. Hands-On Exploration Steps

### 10. Open VPC Console → Endpoints

- Go to [VPC Console](https://console.aws.amazon.com/vpc/)

- Click **Endpoints** → **Create Endpoint**  

### 11. Explore SageMaker Services

- Search for services:  
  - `com.amazonaws.region.sagemaker.api` 

# 🧪 Lab 4.4: Google Cloud VPC Design and Implementation for Vertex AI
 
**Objective:** Design and configure a secure VPC environment that enables Vertex AI pipeline components to access Google Cloud Storage and BigQuery using Private Google Access—without relying on external IPs or public internet routing.

---

## 1. Prerequisites

- Google Cloud Console access with Compute Network Admin and Vertex AI Admin roles  
- Vertex AI API enabled  
- Cloud Shell or gcloud CLI installed and authenticated  
- Existing Vertex AI pipeline deployed or simulated  
- Familiarity with pipeline components and their data dependencies  

---

## 2. Theory Overview

- **Private Google Access** allows VMs in private subnets to access Google APIs (e.g., GCS, BigQuery) without external IPs  
- **Vertex AI pipeline components** often run on managed infrastructure that uses internal IPs only  
- Enabling Private Google Access ensures secure, compliant access to datasets, models, and metadata stored in GCS and BigQuery  
- This configuration is critical for components like `preprocess_data_op`, `train_model_op`, `evaluate_model_op`, `model_approved_op`, and `register_model_op`  
- The only component that does not require GCS access is `model_rejected_op`  

---

## 3. Hands-On Implementation Steps

### 10. Create a Custom VPC Network
