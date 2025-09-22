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
- Python 3.9+ environment with `sagemaker` SDK installed  
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

- Each task below maps directly to commented sections in the Python code (`lab-5.1`) from the GitHub Training Repo.

#### # 🔍 VSCode | Pycharm | GitHub Search Navigation Ready:
Participants can now easily navigate through the lab using VSCode search:

- #### Example, Find/Replace: # TODO: Lab 5.1.1 - Find all Component Identification tasks
- #### Example, Find/Replace: # TODO: Lab 5.1.2 - Find all Purpose Recognition tasks

- Lab 5.1 Navigation:

#### # TODO: Lab 5.1.1 - Component Identification tasks
#### # TODO: Lab 5.1.2 - Purpose Recognition tasks
#### # TODO: Lab 5.1.3 - Architecture Understanding tasks
#### # TODO: Lab 5.1.4 - Conceptual Relationships tasks
#### # TODO: Lab 5.1.5 - High-level Comparison tasks

### ✅ Lab 5.1.1 – Component Identification

# 🔍 File Review Order for Labs 5.1

To follow the end-to-end pipeline architecture and component tasks, review files in this sequence:

1. pipeline_dev.py  
2. preprocess.py  
3. train.py  
4. evaluate.py  
5. pipeline_prod.py  
6. deploy_model.py  

When a lab step asks you to search for `# TODO: Lab X.Y.Z`, use your prefered IDE like VSCode’s global search (Ctrl+Shift+F / ⌘+Shift+F) and scan these files in the order above.  

---

## Component Architecture Overview

Tools: GitHub Training Repo, VSCode, Notebook  

### Lab 5.1.1 – Component Identification  
Task: Locate every core Step class  

Steps  
1. Search all six files for:
```TODO: Lab 5.1.1 - Component Identification```

2. In each file—starting with **pipeline_dev.py**, then **preprocess.py**, **train.py**, **evaluate.py**, **pipeline_prod.py**, **deploy_model.py**—note which Step classes appear or are imported.  
3. Consolidate a unique list of Step types (ProcessingStep, TrainingStep, EvaluationStep, ConditionStep, ModelStep, RegisterModelStep, etc.) in your lab notes.


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

- Next up: **Lab 5.2 – SageMaker Processing, Training, and Transform Steps**

# 🧪 Lab 5.2: SageMaker Processing, Training, and Transform Steps

**Difficulty:** Intermediate  
**Tools Required:** GitHub Training Repo

---

## 🎯 Lab Objectives

- Configure and implement `ProcessingStep`, `TrainingStep`, and `TransformStep` in a SageMaker Pipeline  
- Use step property references to enforce execution order and pass outputs between steps  
- Understand how artifacts flow through the pipeline DAG  
- Implement error handling and validation logic for robust pipeline execution  

---

## 1. Prerequisites

- Completion of Lab 5.1 (Pipeline architecture and component overview)  
- AWS account with SageMaker Studio or Notebook access  
- IAM role with `AmazonSageMakerFullAccess` and `AmazonS3FullAccess`  
- Python 3.8+ environment with `sagemaker` SDK installed  
- Access to the GitHub Training Repo containing starter pipeline code  
- Pre-created S3 bucket for input/output artifacts
- Pre-created Redshift Database Table

---

## 2. Theory Overview

SageMaker Pipelines support modular ML workflows using built-in step types:

- `ProcessingStep`: for data cleaning, feature engineering, or validation  
- `TrainingStep`: for model training using built-in or custom estimators  
- `TransformStep`: for batch inference using trained models  
- Steps are connected using **property references**, which pass outputs from one step as inputs to another  
- Error handling can be implemented at the script level or using conditional logic in the pipeline  

---

## 3. Sequential Lab Tasks

- Each task below maps directly to commented sections in the Python code (`lab-5.2`) from the GitHub Training Repo.

#### # 🔍 VSCode | Pycharm | GitHub Search Navigation Ready:
Participants can now easily navigate through the lab using VSCode search:

- #### Find/Replace: # TODO: Lab 5.2.3 - Find all Property References tasks
- #### Find/Replace: # TODO: Lab 5.2.8 - Find all Error Handling tasks

- Lab 5.2 Navigation:

#### # TODO: Lab 5.2.1 - Step Configuration tasks
#### # TODO: Lab 5.2.2 - Implementation Details tasks
#### # TODO: Lab 5.2.3 - Property References tasks
#### # TODO: Lab 5.2.4 - Dependency Creation tasks
#### # TODO: Lab 5.2.5 - TrainingStep Configuration tasks
#### # TODO: Lab 5.2.6 - TrainingStep Implementation tasks
#### # TODO: Lab 5.2.7 - Transform Step Usage tasks
#### # TODO: Lab 5.2.8 - Error Handling Implementation tasks

### ✅ Lab 5.2.1 – Step Configuration

- Define a `SKLearnProcessor` or `ScriptProcessor`  
- Configure instance type, count, and container image  
- Set up the `ProcessingStep` with basic parameters and script location  

### ✅ Lab 5.2.2 – Implementation Details

- Specify `ProcessingInput` and `ProcessingOutput` objects  
- Define input/output S3 paths and mount locations  
- Confirm that the script reads from and writes to expected locations  

### ✅ Lab 5.2.3 – Property References

- Access output paths from the `ProcessingStep` using `.properties.outputs`  
- Use these references as inputs to the `TrainingStep`  

train_input = processing_step.properties.ProcessingOutputConfig.Outputs["train_data"].S3Output.S3Uri

### ✅ Lab 5.2.4 – Dependency Creation
- Pass train_input to the estimator in TrainingStep

- Ensure the pipeline DAG reflects correct execution order

- Confirm that TrainingStep waits for ProcessingStep to complete

### ✅ Lab 5.2.5 – TrainingStep Configuration
- Define a SKLearn or XGBoost estimator

- Set hyperparameters, instance type, and output path

- Configure the TrainingStep with estimator and input references

### ✅ Lab 5.2.6 – TrainingStep Implementation
- Implement the training script and upload to S3

- Confirm that the model artifact is saved to the correct output location

- Use .properties.ModelArtifacts.S3ModelArtifacts for downstream steps

### ✅ Lab 5.2.7 – Transform Step Usage
- Define a Transformer using the trained model

- Configure batch transform input and output locations

- Add a TransformStep to the pipeline using .properties.ModelArtifacts

### ✅ Lab 5.2.8 – Error Handling Implementation
- Add try/except blocks in processing and training scripts

- Use ConditionStep to check for metric thresholds or missing outputs

- Log errors and raise exceptions for failed steps

- Optionally route to a CallbackStep or notification handler

### 4. Deliverables

- ✅ train.py - Complete with numbered lab tasks
- ✅ preprocess.py - Complete with numbered lab tasks
- ✅ evaluate.py - Complete with numbered lab tasks
- ✅ pipeline_dev.py - Complete with numbered lab tasks
- ✅ pipeline_prod.py - Complete with numbered lab tasks
- ✅ deploy_model.py - Complete with numbered lab tasks

### 5. Reflection Questions
- What are some of the core pipeline components?

- Are pipelines and pipeline components used as accelarator templates?

- How would you modify the pipeline to include model evaluation logic?

#### A notebook is like a whiteboard: great for brainstorming, testing, and learning.

#### A pipeline is like a factory line: optimized for repeatable, scalable, and secure production.

### 6. Supplemental Materials

## 📊 SageMaker Pipeline Advantages

| Feature            | SageMaker Pipeline                              | SageMaker Notebook                          |
|--------------------|--------------------------------------------------|---------------------------------------------|
| **Automation**     | Fully automated workflow execution              | Manual cell-by-cell execution               |
| **Reproducibility**| Versioned, parameterized, and trackable         | Prone to human error and inconsistent runs  |
| **Modularity**     | Steps are reusable and composable               | Code often tangled and linear               |
| **Auditability**   | Execution history, metadata, and lineage        | Limited tracking unless manually added      |
| **Scalability**    | Designed for production-grade ML workflows      | Best for experimentation and prototyping    |
| **Error Handling** | Built-in step-level failure handling            | Requires custom logic or manual debugging   |
| **CI/CD Integration** | Easily integrates with GitHub Actions, CodePipeline, etc. | Requires manual setup             |


- SageMaker ProcessingStep Documentation: https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html

- SageMaker TrainingStep Documentation: https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html

- SageMaker TransformStep Documentation: https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html

- Pipeline Property References: https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-steps.html
