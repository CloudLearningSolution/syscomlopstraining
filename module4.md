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
