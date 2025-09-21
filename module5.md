# Machine Learning Operations Playbook Adoption Workshop – Week 5: ML Pipeline Components and Architecture Exploration - Hands-On Workshop

## 🚀 Migration Machine Learning Operations Pipeline Architecture Comparison
### Module Learning Objectives

- Analyze and compare SageMaker Pipeline components with Vertex AI Pipeline architecture
- Understand SageMaker Pipeline orchestration workflows
- Explore Vertex AI custom and pre-built components (Accelerators: Templates) using Vertex AI Kubeflow
- Design migration strategies for Vertex AI pipelines
- Implement pipeline validation frameworks
- Create component mapping documentation for functionality translation between platforms

### Prerequisites

- AWS Management Console access with SageMaker permissions
- Google Cloud Console access with Vertex AI and AI Platform permissions
- Basic knowledge of Amazon Web Services ML pipeline concepts and containerization
- Participants are recommended to use browser capabilities such as Incognito or In private Browser Sessions due to single-sign-on and cached credential challenges
- Docker or Docker Desktop installed for container component development

# 🧪 Lab 5.1: SageMaker Pipeline Component Architecture Overview

**Difficulty:** Intermediate  
**Tools Required:** GitHub Training Repo 

---

## 🎯 Lab Objectives

- Understand SageMaker Pipeline architecture as a Directed Acyclic Graph (DAG)  
- Identify and describe core SageMaker Pipeline step types  
- Analyze pipeline data dependencies and conceptual relationships  
- Compare SageMaker Pipelines to traditional ML workflows  
- Prepare for hands-on implementation of processing, training, and transform steps in Lab 5.2  

---

## 1. Prerequisites

- AWS account with SageMaker Studio or Notebook access  
- IAM role with `AmazonSageMakerFullAccess` and `AmazonS3FullAccess`  
- Python 3.8+ environment with `sagemaker` SDK installed  
- Access to the GitHub Training Repo containing starter pipeline code  
- Pre-created S3 bucket for input/output artifacts  

---

## 2. Theory Overview

SageMaker Pipelines are built as **Directed Acyclic Graphs (DAGs)**, where each node represents a step and edges represent data dependencies.  

### 🔧 Core Step Types

| Step Type        | Purpose                                      |
|------------------|----------------------------------------------|
| `ProcessingStep` | Preprocess or analyze data                   |
| `TrainingStep`   | Train a model using an estimator             |
| `TransformStep`  | Batch inference on new data                  |
| `ModelStep`      | Register trained model for deployment        |
| `ConditionStep`  | Branch logic based on metrics or thresholds  |
| `CallbackStep`   | Custom logic or external integrations        |

---

## 3. Sequential Lab Tasks

Each task below maps directly to commented sections in the Python notebook (`lab-5.1-pipeline-component.ipynb`) from the GitHub Training Repo.

### ✅ Lab 5.1.1 – Component Identification

- Review the SageMaker SDK documentation  
- List all available pipeline step classes  
- Match each class to its functional role in ML workflows  

### ✅ Lab 5.1.2 – Purpose Recognition

- For each step type, describe its purpose  
- Identify which steps produce artifacts and which consume them  

### ✅ Lab 5.1.3 – Architecture Understanding

- Sketch a DAG showing how steps might be arranged  
- Label inputs, outputs, and dependencies  

### ✅ Lab 5.1.4 – Conceptual Relationships

- Describe how `ProcessingStep` output feeds into `TrainingStep`  
- Explain how `TrainingStep` output feeds into `TransformStep` or `ModelStep`  

### ✅ Lab 5.1.5 – High-Level Comparison

- Compare SageMaker Pipelines to traditional ML workflows (e.g., Jupyter notebooks, Airflow DAGs)  
- Discuss benefits: reproducibility, modularity, auditability  

---

## 4. Deliverables

- Annotated notebook with completed lab tasks  
- Screenshot of pipeline registration in SageMaker Studio  
- DAG sketch showing conceptual flow of components  
- Written comparison of SageMaker Pipelines vs traditional ML workflows  

---

## 5. Reflection Questions

- What are the advantages of using a DAG structure for ML pipelines?  
- How do artifacts flow between steps in SageMaker Pipelines?  
- Which step types would you use for data validation or model evaluation?

---

## 6. Supplemental Materials

- [SageMaker Pipelines SDK Reference](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines-sdk.html)  
- [Understanding DAGs in ML Workflows](https://aws.amazon.com/blogs/machine-learning/building-ml-pipelines-with-amazon-sagemaker-pipelines/)  
- [SageMaker Execution Roles](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html)  

---

Next up: **Lab 5.2 – SageMaker Processing, Training, and Transform Steps**, where we’ll implement real functionality and connect steps into a working DAG.
