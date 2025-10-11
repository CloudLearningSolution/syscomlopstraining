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

#### 🔍 VSCode | Pycharm | GitHub Search Navigation Ready:
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

#### 🔍 File Review Order for Labs 5.1

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

- Task: Describe each Step’s role  

Steps  
1. Search all files for:
```TODO: Lab 5.1.2 - Purpose Recognition```

2. Read the inline comments that explain each Step’s responsibility (data prep, model training, evaluation, conditional gating, registration, deployment).  
3. Hover or “Go to Definition” in VSCode on each Step class to confirm.  
4. Write a one-sentence purpose statement for every Step type.

### ✅ Lab 5.1.3 – Architecture Understanding

- **Task:** Understand how components fit in pipeline architecture  

- **Steps**  
1. Search **pipeline_dev.py** (and **pipeline_prod.py**) for  
```TODO: Lab 5.1.3 - Architecture Understanding```

2. Examine the `Pipeline(…)` constructor’s `steps=[ … ]` argument and note that SageMaker infers execution order from dependencies, not list order.  
3. Highlight or take note of data/property flows between Steps as described in code comments, observe and record how each Step passes data to the next.  
---
### ✅ Lab 5.1.4 – Conceptual Relationships

- Task: Trace data hand-offs between Steps  

- **Steps**
1. Search **pipeline_dev.py**, **pipeline_prod.py**, and **deploy_model.py** for:
```TODO: Lab 5.1.4 - Conceptual Relationships```

2. Follow each `stepA.properties…` reference into the consumer Step’s constructor.  
3. Use VSCode “Go to Definition” on property references to see producer and consumer.  
4. Summarize each producer→consumer link in your notes.

### ✅ Lab 5.1.5 – High-Level Comparison

- Compare SageMaker Pipelines to traditional ML workflows (e.g., Jupyter notebooks, Airflow DAGs)

- **Task:** Compare pipeline architecture vs traditional ML workflows  

- **Steps**  
1. Search all six files for  
```TODO: Lab 5.1.5 - High-level Comparison```

2. Read the inline comments in **pipeline_dev.py**, **pipeline_prod.py**, and **deploy_model.py** that contrast with traditional practices.  
3. Explore the code examples and embedded comments to identify concrete advantages of using SageMaker Pipelines—modularity, automatic dependency resolution, reusability, scalability, separation of concerns, and maintainability—over monolithic, manual workflows.  
4. In your lab notes cite specific lines or comments from the code to illustrate each point.   

---

## 4. Deliverables

- Annotated notebook with completed lab tasks  
- DAG notes showing flow of components  
- Written comparison of SageMaker Pipelines vs traditional ML workflows  

---

## 5. Reflection Questions

- What are the advantages of ML pipelines?  
- How do artifacts flow between steps in Pipelines?  
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

#### 🔍 File Review Order for Labs 5.2

To follow the end-to-end pipeline architecture and component tasks, review files in this sequence:

1. pipeline_dev.py  
2. preprocess.py  
3. train.py  
4. evaluate.py  
5. pipeline_prod.py  
6. deploy_model.py  

When a lab step asks you to search for `# TODO: Lab X.Y.Z`, use your prefered IDE like VSCode’s global search (Ctrl+Shift+F / ⌘+Shift+F) and scan these files in the order above.  

---

### ✅ Lab 5.2.1 – Step Configuration

- Task: Configure parameters and settings for each pipeline step

- Instructions:

- Search all six files for:
```# TODO: Lab 5.2.1 - Step Configuration```

- 🔍 Explore how each step is configured:

- In pipeline_dev.py and pipeline_prod.py, examine how SKLearnProcessor, SKLearn, and Model are initialized with instance types, roles, timeouts, and tags.

- In deploy_model.py, inspect how LambdaHelper and ModelMetrics are configured for deployment and registry.

- In train.py, review how hyperparameters like reg_rate are parsed and passed to the estimator.

### ✅ Lab 5.2.2 – Implementation Details

- Task: Implement inputs, outputs, arguments, and logic for each step

- Instructions:

- Search all six files for:
```# TODO: Lab 5.2.2 - Implementation Details```

- 🔍 Explore:

- In preprocess.py, how ProcessingStep loads data, validates it, and splits it into train/test sets.

- In evaluate.py, how the model and test data are loaded, metrics are calculated, and outputs are saved.

- In deploy_model.py, how validation scripts, inference scripts, and Lambda functions are implemented for deployment and endpoint testing. 

### ✅ Lab 5.2.3 – Property References

- Task: Use step property references to wire dependencies

- Instructions:

- Search pipeline_dev.py, pipeline_prod.py, and deploy_model.py for:

```# TODO: Lab 5.2.3 - Property References```

- 🔍 Explore:

- How ProcessingStep outputs are referenced by TrainingStep and EvaluationStep using .properties.ProcessingOutputConfig.Outputs[...].

- How TrainingStep model artifacts are passed to EvaluationStep, ModelStep, and RegisterModelStep.

- How PropertyFile.JsonGet(...) is used to extract metrics for conditional logic.

### ✅ Lab 5.2.4 – Dependency Creation

- Task: Create step-to-step dependencies using property references

- Instructions:

- Search pipeline scripts for:

```# TODO: Lab 5.2.4 - Dependency Creation```

- 🔍 Explore:

- How property references are passed into step constructors to establish DAG relationships.

- How depends_on=[...] is used in ModelStep, CreateModelStep, and LambdaStep in deploy_model.py to enforce execution order.

- How the steps=[...] list in each pipeline assembles the full DAG.

### ✅ Lab 5.2.5 – TrainingStep Configuration

- Task: Configure estimator parameters and training inputs

- Instructions:

- Search train.py, pipeline_dev.py, and pipeline_prod.py for:

```# TODO: Lab 5.2.5 - TrainingStep Configuration```

- 🔍 Explore:

- How the SKLearn estimator is configured with entry_point, source_dir, hyperparameters, and instance types.

- How CLI arguments are parsed in train.py and passed to the estimator.

- How training data is referenced from the ProcessingStep.

### ✅ Lab 5.2.6 – TrainingStep Implementation

- Task: Implement training logic and produce model artifacts

- Instructions:

- Search train.py for:

```# TODO: Lab 5.2.6 - TrainingStep Implementation```

- 🔍 Explore:

- How the training script loads data, trains the model, and saves the .joblib artifact.

- How CLI arguments like --input_path and --model_output_path are used.

- How the output path aligns with what the pipeline expects.

### ✅ Lab 5.2.7 – Transform Step Usage

- Task: Implement batch transform jobs (optional extension)

- Instructions:

- Search pipeline_dev.py or pipeline_prod.py for:

```# TODO: Lab 5.2.7 - Transform Step Usage```

- 🔍 Explore:

- How to scaffold a TransformStep using the model artifact from TrainingStep.

- How to configure Transformer with instance type, batch input location, and output location.

- This step is not implemented in your current files but is a recommended extension.

### ✅ Lab 5.2.8 – Error Handling Implementation

- Task: Implement step-level error handling and validation

- Instructions:

- Search all six files for:

```# TODO: Lab 5.2.8 - Error Handling Implementation```

- 🔍 Explore:

- How try/except blocks are used in preprocess.py and evaluate.py to catch validation errors.

- How ConditionStep and FailStep are configured in pipeline_prod.py and deploy_model.py to enforce quality gates.

- How error messages are constructed using Join(...) and surfaced in logs.

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
- 
---

# 🧪 Lab 5.3: SageMaker Pipeline Orchestration and Workflow Management  
**Objective:** Understand how orchestration and workflow management are supported in SageMaker pipelines, and GitHub Actions can play a role in managing ML workflows—especially when transitioning to Google Cloud Vertex AI.

---

## 🔍 Overview  

Amazon SageMaker Pipelines offer built-in orchestration for machine learning workflows. Each pipeline is a directed acyclic graph (DAG) of steps such as data preprocessing, training, evaluation, and deployment. These steps are defined in Amazon Python SDK and executed in sequence based on their dependencies.

In conjuction with GitHub Actions can be used to orchestrate ML workflows outside of SageMaker—especially when moving toward cloud-agnostic or Vertex AI–based solutions. GitHub Actions provide a flexible, event-driven automation framework that can trigger pipeline runs, manage artifacts, and coordinate across environments.

---

## 🧠 Key Concepts to Explore  

### 5.3.1 – Workflow Triggers and Automation  
- Understand how SageMaker pipelines are triggered manually or via SDK/API  
- Explore how GitHub Actions can automate pipeline execution based on events:
  - Code commits or pull requests  
  - Scheduled runs (cron jobs)  

### 5.3.2 – Step Sequencing and Dependency Management  
- Learn how SageMaker uses step dependencies (`depends_on`) to enforce execution order  
- Explore how GitHub Actions uses `jobs` and `needs:` to define DAG-like workflows  
- Compare how both systems ensure reproducibility and traceability  

### 5.3.3 – Parameterization and Environment Control  
- Review how SageMaker pipelines use `ParameterString`, `ParameterFloat`, etc.  
- Explore how GitHub Actions uses `env:` and `inputs:` to pass configuration across jobs  
- Discuss how environment-specific variables (e.g., dev/test/prod) are managed in both systems  

---

## ✅ Outcomes  
By the end of this lab, learners will be able to:  
- Describe how SageMaker orchestrates ML workflows  
- Identify GitHub Actions features that support similar orchestration  


---

# 🧪 Vertex AI Targeted Training for MLOPS Capability
Audience: Learners transitioning from SageMaker to Vertex AI Tools: GitHub repo (Python files with TODOs), VS Code, Vertex AI SDK (no AWS required) Navigation Tip: Use VS Code global search (Ctrl+Shift+F / ⌘+Shift+F) to locate # TODO: Lab 5.X.Y markers in the code.

# 🧪 Lab 5.4: Vertex AI Pipeline Component Architecture Exploration

**Difficulty:** Beginner to Intermediate  
**Tools Required:** GitHub Training Repo, PyCharm or VS Code, Vertex AI SDK  

---

## 🎯 Lab Objectives

- Understand Vertex AI pipeline architecture as a Directed Acyclic Graph (DAG)  
- Identify and describe core Vertex AI pipeline components  
- Analyze pipeline execution, configuration, and orchestration patterns  
- Compare Vertex AI pipelines to SageMaker workflows  
- Prepare for hands-on implementation of custom and pre-built components in Lab 5.5  

---

## 1. Prerequisites

- Google Cloud project with Vertex AI enabled  
- IAM role with `Vertex AI Admin` and `Storage Admin` permissions  
- Python 3.9+ environment with `google-cloud-aiplatform` and `kfp` installed  
- Access to the GitHub Training Repo containing starter pipeline code  
- Pre-created GCS bucket for pipeline root and artifacts  

---

## 2. Theory Overview

Vertex AI Pipelines are built as **Directed Acyclic Graphs (DAGs)** using the Kubeflow Pipelines SDK. Each node represents a component, and edges represent data or control dependencies.

### 🔧 Core Component Types

| Component Type                        | Purpose                                                  |
|--------------------------------------|----------------------------------------------------------|
| `@component`                         | Wraps Python logic into a reusable pipeline step         |
| `CustomPythonPackageTrainingJobOp`   | Launches custom training jobs using containerized code   |
| `BigQueryQueryJobOp`                 | Executes SQL queries on BigQuery                         |
| `PipelineJob`                        | Submits compiled pipeline specs to Vertex AI             |
| `dsl.If`, `.after()`                 | Controls DAG flow and conditional execution              |

---

## 3. Sequential Lab Tasks

Each task below maps directly to commented sections in the Python code (`lab-5.4`) from the GitHub Training Repo.

### 🔍 VS Code Search Navigation

Use VS Code global search (`Ctrl+Shift+F` / `Cmd+Shift+F`) to locate lab tasks:

- `# TODO: Lab 5.4.1` – Component Identification  
- `# TODO: Lab 5.4.2` – Purpose Recognition  
- `# TODO: Lab 5.4.3` – Architecture Understanding  
- `# TODO: Lab 5.4.4` – Conceptual Relationships  (Exception: Included by presenter)
 

---

## ✅ Lab 5.4.1 – Component Identification

**Task:** Locate every pipeline component and orchestration construct  

### File Review Order

1. `run_pipeline.py`  
2. `compiler.py`  
3. `vertex_pipeline_dev.py`  
4. `vertex_pipeline_prod.py`  
5. `deploy_model.py`  

### Instructions

1. Search each file for:  ```TODO: Lab 5.4.1 - Component Identification ```
2. Identify:
- `@component` decorators  
- Pre-built components (e.g., `CustomPythonPackageTrainingJobOp`)  
- Orchestration constructs (`PipelineJob`, `dsl.pipeline`, `.after()`, `dsl.If`)  
3. Record each component’s name, type (custom or pre-built), and role in the pipeline.

---

## ✅ Lab 5.4.2 – Purpose Recognition

**Task:** Describe each component’s role and why it exists  

### Instructions

1. Search all files for:  ```TODO: Lab 5.4.2 - Purpose Recognition ```
2. Read inline comments and docstrings explaining:
- What each component does (e.g., preprocessing, training, evaluation, deployment)  
- Why specific parameters, images, or resource specs are used  
- How the pipeline is configured for dev vs prod  
3. Write a one-sentence purpose statement for each component and orchestration block.

---

## ✅ Lab 5.4.3 – Architecture Understanding

**Task:** Analyze how the pipeline is structured and executed  

### Instructions

1. Search all files for: ```TODO: Lab 5.4.3 - Architecture Understanding ```
2. Observe:
- How pipeline DAGs are constructed using `@dsl.pipeline`  
- How components are sequenced using `.after()` and conditional logic  
- How resource limits and environment variables are configured  
- How compiled specs are submitted via `PipelineJob(...)`  
3. Sketch the pipeline architecture showing:
- Component flow  
- Data dependencies  
- Conditional branches  
- Execution triggers

---

## ✅ Lab 5.4.4 – Conceptual Relationships

- **Task:** Explore with the presenter how data and configuration flow between components  
---
# 🧪 Lab 5.5: Vertex AI Custom Components, Pre-built Components, and Accelerator Templates

**Difficulty:** Intermediate → Advanced  
**Tools Required:** GitHub Training Repo, PyCharm or VS Code, Vertex AI SDK, Kubeflow Pipelines SDK, (optional) Terraform CLI

---

## 🎯 Lab Objectives

- Distinguish custom vs pre-built Vertex AI pipeline components in the repo  
- Map component design decisions in code to the 3-layer accelerator template  
- Understand BigQuery and Feature Group integration as a pre-built data access pattern  
- Verify pipeline parameter and artifact changes introduced by BigQuery migration  
- Prepare for orchestration and Kubeflow integration in Lab 5.6

---

## 1. Prerequisites

- Completed Lab 5.4 (component architecture exploration)  
- Google Cloud project with Vertex AI, BigQuery, and Feature Registry API enabled  
- IAM roles: Vertex AI and appropriate BigQuery permissions  
- Python 3.9+ with `google-cloud-aiplatform`, `kfp`, `google-cloud-pipeline-components`, and `google-cloud-bigquery` installed  
- Repo files available and up-to-date:
  - vertex_pipeline_dev.py  
  - vertex_pipeline_prod.py  
  - compiler.py  
  - run_pipeline.py  
  - deploy_model.py  
  - vertex_ai_infrastructure.tf  
  - vertex-ai-cicd.yml

---

## 2. Theory Overview

Enterprise pipelines balance two forces:

- Template: Custom components for business-specific logic, rapid iteration, and fine-grained control  
- Template: Pre-built Google Cloud Pipeline Components for managed, standardized, scalable operations

Accelerator Template (3-layer) pattern:
- Infrastructure layer (Terraform): provisions Vertex AI resources, BigQuery, Feature Groups, IAM  
- Pipeline layer (KFP): custom + pre-built components and orchestration logic  
- Enterprise layer: Sysco governance, audit, compliance, and reusable Sysco solution well architected frameworks

BigQuery integration pattern used here:
- Use pre-built BigQuery Query Job components for serverless SQL-based preprocessing and deterministic AI ML train/test splits for descriminitive and generative models
- Use Feature Groups for feature governance, data drift, and data lineage from preprocessing, training, testing, evaluating, model registering, to online realtime inferencing, serving, and generative API endpoints.
- Consume shared views of BigQuery table artifacts in custom training/eval components eliminating data duplication persistant storage or temporary in-memory storage.

---

## 3. File review order

Open files in this sequence to follow end-to-end architecture and CI/infra flow:

1. vertex_pipeline_dev.py 
2. vertex_pipeline_prod.py
3. compiler.py  
4. run_pipeline.py  
5. deploy_model.py  
6. vertex-ai-cicd.yml  
7. vertex_ai_infrastructure.tf

---

## 4. How to navigate the code (Repo files)

Use global search (Ctrl+Shift+F / Cmd+Shift+F) and search for the exact TODO tokens below to jump to training TODO in-line comments:

- `# TODO: Lab 5.5.1`  
- `# TODO: Lab 5.5.2`  
- `# TODO: Lab 5.5.3`  
- `# TODO: Lab 5.5.4`  
- `# TODO: Lab 5.5.5`

You’ll also see `# TODO: Lab 5.4.X` markers for architecture-level references from the prior lab. For these lab tasks disregard Lab 5.4.

---

## 5. Lab Tasks

---

## ✅ Lab 5.5.1 — Custom vs Pre-built Component Identification

Task: Inventory components and label CUSTOM or PRE-BUILT.

Files to open: vertex_pipeline_dev.py, vertex_pipeline_prod.py

Steps:
1. Search for `# TODO: Lab 5.5.1`.  
2. For each TODO, inspect surrounding lines and note:
   - Component name (function or loaded op)  
   - Type: CUSTOM or PRE-BUILT  
   - One-sentence rationale from inline comments

Deliverable: A 3-column table (CSV/Markdown) in your feature branch:
| Component | Type | One-line Rationale |

Example rows you should produce:
- bigquery_query_job_op | PRE-BUILT | Serverless SQL-based data access and deterministic splitting  
- train_model_op | CUSTOM | scikit-learn training, custom joblib serialization

---

## ✅ Lab 5.5.2 — Pre-built Alternatives Exploration

Task: Review commented pre-built examples and capture trade-offs.

Files to open: vertex_pipeline_dev.py, vertex_pipeline_prod.py

Steps:
1. Search for `# TODO: Lab 5.5.2`.  
2. Locate commented pre-built examples (BigQuery Query Job, CustomTrainingJobOp, ModelUploadOp).  
3. For each custom component, write:
   - Pre-built alternative name  
   - 2 benefits of the pre-built approach  
   - 2 reasons the repo keeps/customizes the component

Deliverable: Short pros/cons list for each component pair (one paragraph each).

---

## ✅ Lab 5.5.3 — Accelerator Template Mapping

Task: Map pipeline files and infra to the 3-layer Accelerator Template.

Files to open: vertex_pipeline_dev.py, vertex_pipeline_prod.py, vertex_ai_infrastructure.tf, .github/workflows/vertex-ai-cicd.yml

Steps:
1. Search for `# TODO: Lab 5.5.3`.  
2. Identify concrete repo artifacts for each layer:
   - Infrastructure layer → terraform file(s) and outputs (vertex_ai_infrastructure.tf)  
   - Pipeline layer → vertex_pipeline_*.py and compiler.py  
   - Enterprise layer → comments in prod pipeline, ModelUploadOp labels, recommended governance checks
3. Write a one-paragraph mapping for each layer listing filenames and the responsibilities they cover.

Deliverable: Three short paragraphs (one per layer) in feature branch.

---

## ✅ Lab 5.5.4 — BigQuery Integration, Artifact Typing, and Parameter Plumbing

Task: Trace how BigQuery outputs are produced, typed, and consumed by custom components.

Files to open: vertex_pipeline_dev.py, vertex_pipeline_prod.py, compiler.py, run_pipeline.py

Steps:
1. Search for `# TODO: Lab 5.5.4`.  
2. Confirm:
   - `bigquery_query_job_op` is loaded (components.load_component_from_url) and called for train/test queries.  
   - SQL uses `FARM_FINGERPRINT` for deterministic 80/20 splitting.  
   - BigQuery op outputs a BQ table artifact; code uses `Input[artifact_types.BQTable]`.  
   - Custom components parse `train_data.uri` (or metadata) to build `project.dataset.table` and read via `bigquery.Client`.  
   - Pipeline signature parameters (`bq_dataset`, `bq_view`, `project_id`, `region`) are passed through compiler/run scripts.
3. Compile the pipeline locally (example):
```bash
python compiler.py --py vertex_pipeline_dev.py --output pipelines/dev_diabetes_pipeline.yaml
```
4. Inspect the compiled YAML to confirm the BigQuery component output key name (`destination_table` or `destinationTable`) and note it.

Deliverable:
- Short dataflow bullets:
  BigQuery view → bigquery_query_job_op (train/test) → BQTable artifact → train_model_op / evaluate_model_op (reads via BigQuery client) → model artifacts
- Note: exact BigQuery output key from the compiled YAML and any mismatch to code usage.

---

## ✅ Lab 5.5.5 — Feature Groups and Governance

Task: Explain how Feature Groups fit into the pipeline and propose governance checks to add.

Files to open: vertex_pipeline_dev.py, vertex_pipeline_prod.py, vertex_ai_infrastructure.tf

Steps:
1. Search for `# TODO: Lab 5.5.5`.  
2. Identify where pipeline queries a BigQuery view backed by Feature Groups and where Feature Registry is referenced in comments.  
3. Draft three practical governance actions to add in future labs (schema validation, data quality checks, drift monitoring) and where to place them in the pipeline (as components or monitoring jobs).

Deliverable: One-paragraph summary and a 3-item TODO checklist for governance tasks.

---

## 6. Practical checklist (quick wins)

- Confirm `bigquery_query_job_op` URL resolves from your environment (network/registry access).  
- Confirm the BigQuery component’s output key (`destination_table`) matches usage in pipeline code.  
- Ensure `train_model_op` and `evaluate_model_op` accept `project_id` and `bq_location` parameters and use them with the BigQuery client.  
- Update `compiler.py` compile examples and README run examples to include `bq_dataset` and `bq_view`.  
- Add README note for learners to search for `# TODO: Lab 5.5.X` markers to follow hands-on steps.

---

## 7. Next: Lab 5.6 preview

Lab 5.6 will cover orchestration and Kubeflow integration:
- Compiling pipeline (compiler.py) and submitting via `PipelineJob` (`run_pipeline.py`) from local CLI and CI/CD  
- Observability: monitoring runs, artifacts, and metrics in Vertex AI console  
- Advanced orchestration: retries, caching, parallelism, and conditional retries  
- CI/CD: example GitHub Actions workflow to compile → upload → submit

---

## 8. Helpful snippets (copy into your repo README or instructor notes)

- Compile dev pipeline locally:
```bash
python compiler.py --py vertex_pipeline_dev.py --output pipelines/dev_diabetes_pipeline.yaml
```

- Submit compiled pipeline:
```bash
python run_pipeline.py \
  --project-id YOUR_PROJECT_ID \
  --region YOUR_REGION \
  --pipeline-spec-uri gs://YOUR_BUCKET/pipelines/dev_diabetes_pipeline.yaml \
  --service-account pipeline-runner@YOUR_PROJECT_ID.iam.gserviceaccount.com \
  --pipeline-root gs://YOUR_BUCKET/pipeline-root/dev/ \
  --display-name dev-diabetes-run \
  --parameter-values-json '{"project_id":"YOUR_PROJECT_ID","region":"YOUR_REGION","model_display_name":"dev-diabetes","bq_dataset":"shared_bronze","bq_view":"diabetes_features_view"}' \
  --labels-json '{"env":"dev","team":"ml"}'
```

- Quick VS Code searches:
  - `# TODO: Lab 5.5.1`
  - `# TODO: Lab 5.5.2`
  - `# TODO: Lab 5.5.4`
  - `# TODO: Lab 5.5.5`

---

## 9. Instructor notes

- Emphasize why certain components were migrated to pre-built BigQuery components (scalability, serverless, governance) and why others remain custom (business logic, control).  
- Encourage learners to inspect compiled YAML to see how KFP serializes pre-built vs custom components and artifact types.  
- Advise learners to validate artifact output keys in compiled YAML before wiring downstream components.

---

If you want, I can now generate:
- A ready-to-commit `README.md` file for the repo, or  
- Example `# TODO: Lab 5.5.X` comment blocks you can paste into `vertex_pipeline_dev.py` to guide learners through the code.

---
# 🧪 Lab 5.6: Vertex AI Pipeline Orchestration and Kubeflow Integration

**Difficulty:** Intermediate to Advanced  
**Tools Required:** GitHub Training Repo, VS Code, Vertex AI SDK, Kubeflow Pipelines SDK, GitHub Actions (or other CI/CD), Terraform (optional)

---

## 🎯 Lab Objectives

- Compile and submit KFP v2 pipelines to Vertex AI programmatically and via CI/CD  
- Understand how Vertex AI executes Kubeflow pipeline specs (PipelineJob → Kubeflow runtime)  
- Implement and reason about orchestration primitives: caching, retries, parallelism, resource limits, and conditional branches  
- Add observability: logs, metrics, dashboard links, and artifact tracking for troubleshooting  
- Create an example GitHub Actions workflow to compile and submit pipelines automatically

---

## 1. Prerequisites

- Completion of Labs 5.4 and 5.5 (pipeline architecture, pipeline template component options and BigQuery integration)  
- Google Cloud project with Vertex AI, BigQuery, Artifact Registry access, and appropriate IAM roles  
- Python 3.9+ with `google-cloud-aiplatform`, `kfp`, `google-cloud-bigquery` installed  
- Access to the repo files:
  - `vertex_pipeline_dev.py` (pipeline)
  - `vertex_pipeline_prod.py` (pipeline)
  - `compiler.py` (compilation)
  - `run_pipeline.py` (submission)
  - `deploy_model.py` (serving)
  - Optional: `vertex_ai_infrastructure.tf` and `.github/workflows/` (CI)
- GitHub repository with Actions enabled and secrets configured (PROJECT_ID, REGION, SERVICE_ACCOUNT, PIPELINE_ROOT, etc.)

---

## 2. Theory Overview

Vertex AI pipelines are Kubeflow Pipeline specs executed by a managed Kubeflow runtime. Key orchestration concerns:

- Compilation: Python pipeline function → KFP v2 YAML (compiler.Compiler().compile)  
- Submission: PipelineJob in Vertex AI uses the compiled YAML + parameter_values to create a runtime job  
- Caching: Component-level caching enables reuse of prior outputs to save time/cost  
- Retries & Failure Handling: KFP/Vertex support retry policies on components and job-level monitoring  
- Parallelism: Independent tasks run concurrently when no data/control dependency exists  
- Observability: Logs, metrics (component Metrics outputs), and Vertex Pipeline dashboard URLs are essential for debugging and auditing  
- CI/CD: Automate compile + submit via GitHub Actions; pipeline parameterization allows environment-specific runs (dev/prod)

---

## 3. File review order (what to open first)

1. `compiler.py` — how the Python pipeline is selected and compiled to YAML  
2. `run_pipeline.py` — how PipelineJob is constructed and submitted, parameter handling, caching flag  
3. `vertex_pipeline_dev.py` — pipeline DAG (resource limits, dsl.If branches, BigQuery integration)  
4. `vertex_pipeline_prod.py` — prod differences (thresholds, versioning)  
5. `.github/workflows/ci-pipeline.yml` (example to create) — CI job to compile & submit  
6. `deploy_model.py` — how pipeline outputs are consumed and deployed to endpoints

---

## 4. How to navigate the code (VS Code)

Search the repo for these new markers and add them to files as exploration tasks:

- `# TODO: Lab 5.6.1` — Pipeline Compilation and Validation  
- `# TODO: Lab 5.6.2` — Pipeline Submission and PipelineJob parameters  
- `# TODO: Lab 5.6.3` — Caching and Retry Configuration in components and PipelineJob  
- `# TODO: Lab 5.6.4` — Parallelism and Resource Limits (set_cpu_limit, set_memory_limit)  
- `# TODO: Lab 5.6.5` — Observability: logs, metrics, dashboard links, pipeline artifacts  
- `# TODO: Lab 5.6.6` — CI/CD: GitHub Actions example for compile → submit  
- `# TODO: Lab 5.6.7` — Failure modes, debugging tips, and best practices

Use `Ctrl+Shift+F` / `Cmd+Shift+F` to jump to each marker during targeted training.

---
