# Week 3: Identity and Access Management – Platform Enablement (Provisioning) Hands-On Workshop

# **Presenter Demonstration**
# 🧪 Lab 3.1: AWS Management Console IAM Configuration for SageMaker

**Objective:** Explore the IAM roles, trust relationships, and managed policies that enable Amazon SageMaker—without creating or modifying any IAM resources.
---

## 1. Prerequisites

- AWS Management Console access with IAM “ReadOnly” and SageMaker permissions  

- Familiarity with AWS IAM concepts (roles, policies, trust relationships)  

- No new IAM role or policy creation allowed  

---

## 2. Theory Overview

- SageMaker uses an execution role to call other AWS services on your behalf (S3, ECR, CloudWatch, etc.)  

- Execution roles require a trust policy allowing the SageMaker service principal (`sagemaker.amazonaws.com`) to assume the role  

- Common managed policies include `AmazonSageMakerFullAccess` and `AmazonS3ReadOnlyAccess`  

- The `iam:PassRole` permission is required to pass execution roles into SageMaker jobs  

---

## 3. Hands-On Exploration Steps (Do Not Finalize Resources)

- Open the AWS Console

- Search for IAM, and then select **Roles**  

- Search for **AmazonSageMaker** in the Roles list  

## 4. Review an Existing SageMaker Execution Role

- Click a role named like `AmazonSageMaker-ExecutionRole-*`  

- Select the **Trust relationships** tab  

- Confirm `Service: sagemaker.amazonaws.com` under **Trusted entities**  

## 5. Inspect Attached Policies

- Select the **Permissions** tab  

- Note managed policies such as `AmazonSageMakerFullAccess`

- Click **Policy name** → **JSON** to view actions and resources  
---

## 4. Deliverables

- List of SageMaker execution roles and their trust principals  

- Summary of key managed policies and granted actions  
---

## 5. Supplemental Materials

- IAM Roles for SageMaker Overview  
  https://docs.aws.amazon.com/sagemaker/latest/dg/security_iam_service-with-iam.html  

- SageMaker Execution Role Best Practices  
  https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-access.html  

---

## 6. Notes and Warnings

- Do not create, modify, or delete any IAM roles or policies  

- Viewing trust relationships and policies is read-only  

- Passing real roles without proper review can break production workflows  

---

## 7. Verification Source

- Verified against AWS SageMaker IAM documentation  
  https://docs.aws.amazon.com/sagemaker/latest/dg/security_iam_service-with-iam.html  

---

# **Presenter Demonstration**

# 🧪 Lab 3.2: AWS CLI and SDK Authentication Setup for SageMaker

**Objective:** Validate AWS CLI/SDK authentication for SageMaker by inspecting credential configurations and making read-only calls—without launching any SageMaker jobs.

---

## 1. Prerequisites

- AWS CLI v2 installed (or use AWS CloudShell)
- **SageMaker execution role** with appropriate permissions

---

## 2. Theory Overview

- **SageMaker requires specific IAM roles** for training jobs, endpoints, and notebook instances

---

## 3. SageMaker-Specific Authentication Requirements

### Key SageMaker Policies:
- `AmazonSageMakerFullAccess` - Full SageMaker permissions
- `AmazonSageMakerReadOnly` - Read-only access for monitoring
- `AmazonS3FullAccess` - Required for data access and model storage
- Custom execution roles for training jobs and endpoints

## Hands-On Exploration Steps

## 4. Check available SageMaker execution roles
- Run: `aws iam list-roles --query 'Roles[?contains(RoleName, `SageMaker`)].{RoleName:RoleName,Arn:Arn}' --output table`

## 5. Verify SageMaker service permissions
- Run: `aws sagemaker describe-domain --domain-id $(aws sagemaker list-domains --query 'Domains[0].DomainId' --output text) 2>/dev/null || echo "No SageMaker Studio domain found"`

## 6. Validate SageMaker Execution Role

- Get SageMaker execution role ARN

- Run: `ROLE_ARN=$(aws iam list-roles --query 'Roles[?contains(RoleName, `SageMaker`)].Arn | [0]' --output text)`

## 7. Verify role exists and has trust policy
- Run: `aws iam get-role --role-name $(basename $ROLE_ARN) --query 'Role.AssumeRolePolicyDocument'`

## 8. Check attached policies
- Run: `aws iam list-attached-role-policies --role-name $(basename $ROLE_ARN)`

## Notes and Warnings
- Do not create or launch any SageMaker jobs

- Avoid committing real credentials in shared scripts

- Use read-only calls to confirm permissions

## Verification Source

- Verified against AWS CLI and Boto3 documentation https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html

---

## 🧪 Lab 3.4: Google Cloud Console IAM Configuration for Vertex AI

**Duration:** TBD minutes  
**Objective:** Explore predefined and custom IAM roles for Vertex AI in the Google Cloud Console
---
