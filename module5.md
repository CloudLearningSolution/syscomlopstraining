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

## Next: Lab 5.6 preview

Lab 5.6 will cover orchestration and Kubeflow integration:
- Compiling pipeline (compiler.py) and submitting via `PipelineJob` (`run_pipeline.py`) from local CLI and CI/CD  
- Observability: monitoring runs, artifacts, and metrics in Vertex AI console  
- Advanced orchestration: retries, caching, parallelism, and conditional retries  
- CI/CD: example GitHub Actions workflow to compile → upload → submit

---

## 8. Snippets (copy into your repo README)

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

---
### 🧪 Lab 5.6: Vertex AI Pipeline Orchestration and Kubeflow Integration
Code-Only Exploration — Search for TODO Markers

Difficulty: Intermediate → Advanced  
Tools required: GitHub training repo, VS Code

---

### 🎯 Lab Objectives
- Explore orchestration patterns in Vertex AI pipelines using Kubeflow  
- Understand pipeline compilation, submission, and monitoring flows  
- Inspect caching, retries, resource limits, and observability strategies  
- Analyze CI/CD workflow automation using GitHub Actions  
- Compare orchestration differences between dev and prod pipelines  
- Learn debugging and failure-handling best practices

---

### 1. Prerequisites
- Completed Labs 5.4 and 5.5  
- Repository contains these files with # TODO: Lab 5.6.X markers:
  - compiler.py  
  - run_pipeline.py  
  - vertex_pipeline_dev.py  
  - vertex_pipeline_prod.py  
  - deploy_model.py  
  - vertex-ai-cicd.yml

---

### 2. VS Code Search Navigation
Use global search (Ctrl+Shift+F / Cmd+Shift+F) to locate each lab task token exactly:

- `# TODO: Lab 5.6.1` – Pipeline Compilation and Validation  
- `# TODO: Lab 5.6.2` – Pipeline Submission and PipelineJob parameters  
- `# TODO: Lab 5.6.3` – Caching and Retry Configuration  
- `# TODO: Lab 5.6.4` – Parallelism and Resource Limits  
- `# TODO: Lab 5.6.5` – Observability: logs, metrics, dashboard links  
- `# TODO: Lab 5.6.6` – CI/CD: GitHub Actions compile → submit  
- `# TODO: Lab 5.6.7` – Failure modes, debugging tips, and best practices

Search the exact token (including colon) and inspect 3–8 lines of context around each match.

---

### 3. Order of exploration (follow this sequence)
1. compiler.py — compilation selection, outputs, compiled function  
2. run_pipeline.py — PipelineJob construction, flags, JSON params, caching  
3. vertex_pipeline_dev.py — caching, resources, retry policy, parallelism (dev)  
4. vertex_pipeline_prod.py — production differences (thresholds, caching, resources)  
5. vertex-ai-cicd.yml — GitHub Actions compile → upload → submit → approval → deploy flow  
6. deploy_model.py — Model Registry lookup, endpoint reuse/creation, deployment, testing, observability  
7. Cross-file search: failure modes and best-practice TODOs

Follow the sequence — later files reference artifacts and patterns you’ll inspect earlier.

---

### 4. Lab Tasks — Code Exploration Only
Each task maps to a TODO marker. Open the specified file, find the marker, and inspect surrounding code/comments. No execution required.

#### ✅ Lab 5.6.1 — Pipeline Compilation and Validation  
File: compiler.py — Search: `# TODO: Lab 5.6.1`  
Explore and record:
- How the pipeline source file is selected (env var, CLI arg, or hard-coded path)  
- Which pipeline function is compiled (function name)  
- What YAML filename(s) are generated and where they are written  
- How parameters are passed to the compiler (CLI args, env vars)  
Deliverables:
- Exact compile command used in CI (copy full CLI line)  
- Output YAML path(s) to include in ci-cd-inspection.md

#### ✅ Lab 5.6.2 — Pipeline Submission and PipelineJob Parameters  
File: run_pipeline.py — Search: `# TODO: Lab 5.6.2`  
Explore and record:
- How PipelineJob is constructed (aiplatform PipelineJob or gcloud wrapper)  
- Arguments accepted and passed: `--pipeline-spec-uri`, `--pipeline-root`, `--service-account`, `--display-name`, `--parameter-values-json`, `--labels-json`  
- How `PARAMS_JSON` and `LABELS_JSON` are deserialized/consumed (json.loads → dict → PipelineJob param map)  
- How caching is toggled (flag or PipelineJob parameter)  
Deliverables:
- Exact submission command snippet from CI (copy/paste)  
- How numeric params are coerced (jq `tonumber` or Python cast)

#### ✅ Lab 5.6.3 — Caching and Retry Configuration  
Files: run_pipeline.py, vertex_pipeline_dev.py, vertex_pipeline_prod.py — Search: `# TODO: Lab 5.6.3`  
Explore and record:
- Where caching is enabled/disabled for pipeline components  
- Which components are marked safe to cache vs non-cacheable (e.g., registration ops)  
- Retry logic or comments about idempotency and retries per component  
- Differences between dev and prod retry strategies and caching usage  
Deliverables:
- List of components with caching/retry settings and dev/prod differences

#### ✅ Lab 5.6.4 — Parallelism and Resource Limits  
Files: vertex_pipeline_dev.py, vertex_pipeline_prod.py — Search: `# TODO: Lab 5.6.4`  
Explore and record:
- `.set_cpu_limit()` and `.set_memory_limit()` usage and values  
- Which components run in parallel (no `.after()` or direct dependencies)  
- Comments suggesting resource sizing or quotas to observe  
- Differences in resource configurations between dev and prod  
Deliverables:
- Table of components → CPU/memory limits and parallelism notes

#### ✅ Lab 5.6.5 — Observability: Logs, Metrics, Dashboard Links  
Files: run_pipeline.py, vertex_pipeline_dev.py, vertex_pipeline_prod.py, deploy_model.py — Search: `# TODO: Lab 5.6.5`  
Explore and record:
- `metrics.log_metric()` calls and metric names used in pipeline components  
- Logging patterns (`logging.info`, `logging.error`) and where dashboard URIs are printed or referenced  
- How `deploy_model.py` prints endpoint/resource identifiers and console URLs for CI capture  
Deliverables:
- Exact log/metric lines to capture, and list of console URLs printed by scripts

#### ✅ Lab 5.6.6 — CI/CD: GitHub Actions Compile → Submit  
File: vertex-ai-cicd.yml — Search: `# TODO: Lab 5.6.6`  
Explore and record:
- All workflow jobs and steps:
  - compile job (checkout, setup, install, auth, compile, upload-artifact)  
  - train-dev job (download-artifact, build jq `PARAMS_JSON`, `run_pipeline.py`)  
  - require-approval job (`environment: production`)  
  - train-prod job (find_parent_model, include `parent_model` in params)  
  - deploy-model job  
- Secrets referenced (exact secret names): `GCP_PROJECT_ID`, `GCP_PROJECT_NUMBER`, `GCP_WORKLOAD_IDENTITY_POOL_ID`, `GCP_WORKLOAD_IDENTITY_PROVIDER_ID`, `GHA_SERVICE_ACCOUNT_EMAIL`, `GCP_SHARED_MLOPS_BUCKET_NAME`, `VERTEX_PIPELINE_SA_EMAIL`, etc.  
- Artifact flow: compiled YAML local filenames, artifact upload name (e.g., `compiled-vertex-pipelines`), download path (e.g., `./compiled-pipelines/`), whether compiled YAMLs are archived to GCS (run_pipeline.py behavior vs explicit `gsutil`).  
- Parameter injection mechanism: exact `jq` snippets building `PARAMS_JSON` and `LABELS_JSON`, numeric coercion (`tonumber`), `PIPELINE_JOB_ID` generation, pipeline-root path template.  
- Approval mechanism: `environment: production` usage and job `needs` ordering  
Deliverables:
- Exact `upload-artifact` name and `download-artifact` path strings  
- Exact `jq` invocation and `run_pipeline.py` invocation lines to paste into ci-cd-inspection.md

#### ✅ Lab 5.6.7 — Failure Modes, Debugging Tips, Best Practices  
Files: compiler.py, run_pipeline.py, vertex_pipeline_dev.py, vertex_pipeline_prod.py — Search: `# TODO: Lab 5.6.7`  
Explore and record:
- Exception handling and error messages; what exceptions are raised and where  
- Comments about common failure causes (IAM, missing artifacts, invalid URIs, quotas)  
- Debugging tips present in code comments (check logs, validate inputs, verify service enablement)  
- Best-practice suggestions (idempotency, small components, explicit resource limits, non-cacheable registration ops)  
Deliverables:
- Short troubleshooting checklist with remediation steps for common errors

---

### 5. Deliverables
Create a single `learner.md` that contains:

- Job list (5 jobs) with short purpose — copy from `vertex-ai-cicd.yml`  
- Secrets table with exact secret names and where used (job + step)  
- Artifact flow diagram: compile → upload-artifact → download → `run_pipeline.py` → optional GCS archival → Vertex AI  
- Parameter injection section: verbatim `jq` snippets and `run_pipeline.py` invocation lines copied from YAML  
- Dev vs Prod comparison table: `min_accuracy`, caching, `parent_model` usage, compiled YAML file, pipeline-root differences  
- Approval mechanism capture: YAML lines showing `environment: production` and `needs`  
- Failure modes & debugging checklist  
- Observability checklist: exact logging/metric lines to capture and console URLs printed by scripts

Use exact CLI/YAML snippets you copy from files in the repo when populating the document.

---

### 6. Quick tips for efficient exploration
- Search for exact tokens (include colon) to land on the student-facing TODO anchors.  
- When you find a shell step, copy the entire block (PIPELINE_JOB_ID, `jq`, `run_pipeline.py`).  
- For secrets, add one-line mapping: `SecretName — used in <job> : <step>` (e.g., `GCP_PROJECT_ID — setup-and-compile-gcp : Authenticate to Google Cloud`).  
- For artifact actions, capture action name and `path` verbatim.  
- For parameter JSON, copy the full `jq -n --arg ... '{...}'` block.  

---

Use `Ctrl+Shift+F` / `Cmd+Shift+F` to jump to each marker during targeted training.

---

# 🧪 Learner Guide — Labs 5.7, 5.8, and 5.9: Vertex AI Pipeline Conversion and Validation

**Session Type:** Explore-only (2 hours)  
**Tools Required:** PyCharm or VS Code, GitHub Training Repo with conversion file  
**File to Open:**  
- `train_to_vertex_ai_conversion.py`

---

## 🧠 Overview

This guided exploration focuses on understanding how a traditional ML training script (`train.py`) is converted into a Vertex AI pipeline using Kubeflow components. No execution or documentation is required — your goal is to read, reason, and locate the `# TODO: Lab X.Y.Z` markers embedded in the single consolidated conversion file.

---

## 🎯 Lab Objectives

### Lab 5.7 — General ML train.py → Vertex AI Pipeline Conversion Workshop  
**Focus:** High-level line-by-line exploration

- Understand how each import, parameter, and execution pattern in `train.py` maps to Vertex pipeline components  
- Compare script-style execution to DAG-based orchestration  
- Trace argparse usage and its replacement with pipeline parameters

### Lab 5.8 — Component Mapping and Functionality Translation  
**Focus:** Function-by-function deep dive

- Map each function in `train.py` to its corresponding Vertex component  
- Explore how CSV-based logic is replaced by BigQuery artifacts  
- Verify algorithm consistency and artifact persistence

### Lab 5.9 — Pipeline Testing and Validation Framework  
**Focus:** Quality gates and testing patterns

- Understand how conditional logic replaces always-register behavior  
- Explore metrics-driven approval and rejection paths  
- Review transformation patterns that support enterprise-grade monitoring

---

## 📚 Theory Summary

Vertex AI pipelines use declarative DAGs with typed artifacts, structured Metrics, and conditional branching. Migration replaces file-based I/O with cloud-native services (BigQuery), wraps logic in components, and introduces observability and quality gates while keeping core algorithm code largely unchanged.

---

## 📂 File to Open

- `train_to_vertex_ai_conversion.py` — the single canonical conversion file for Labs 5.7–5.9.

Use global search (Ctrl+Shift+F / Cmd+Shift+F) inside that file to jump to each `# TODO: Lab X.Y.Z` marker listed below.

---

## ✅ Lab 5.7 — High-Level Conversion Exploration

- TODO: `Lab 5.7.1` — Line-by-Line Import Exploration  
  - Search for the comment line: `# TODO: Lab 5.7.1 - Line-by-Line Import Exploration: Find each train.py import and its pipeline equivalent`  
  - Inspect the original train.py import block (commented) and the Vertex AI imports (kfp, kfp.dsl, artifact_types). Confirm mapping and note why some imports disappear or are replaced by cloud services.

- TODO: `Lab 5.7.2` — High-Level Architecture  
  - Search for: `# TODO: Lab 5.7.2 - High-Level Architecture Exploration: How script metadata becomes pipeline configuration`  
  - Inspect PIPELINE_NAME, PIPELINE_DESCRIPTION, BASE_IMAGE, REQUIREMENTS_PATH and compare to original script execution guard.

- TODO: `Lab 5.7.3` — Parameter Handling Evolution  
  - Search for: `# TODO: Lab 5.7.3 - Data Flow Exploration: train.py sequential calls → pipeline DAG`  
  - Confirm pipeline parameters in the `diabetes_training_pipeline` signature and how argparse in the __main__ block maps to pipeline parameters.

- Additional Lab 5.7 anchors: `TODO: Lab 5.7.4` (task creation) and `TODO: Lab 5.7.5` (dependency management / URI parsing notes).

Note: canonical parameter name used in file and README is `min_accuracy` (pipeline parameter). When reading components, some component examples use `min_accuracy_threshold` — the student should note these naming variants and record them in notes (assignments require reading only).

---

## ✅ Lab 5.8 — Component Mapping and Functionality Translation

- TODO: `Lab 5.8.1` — Function Mapping  
  - Search: `# TODO: Lab 5.8.1 - Function Mapping Exploration: How get_csvs_df() becomes BigQuery component`  
  - Inspect the commented original `get_csvs_df` function and the loaded pre-built component `bigquery_query_job_op` (look for the components.load_component_from_url call). Note the function→component mapping and the versioned component URL.

- TODO: `Lab 5.8.2` — Data Flow Translation  
  - Search: `# TODO: Lab 5.8.2 - Data Source Translation: DataFrame input → BigQuery table parsing` and related `# TODO: Lab 5.8.2 - Data Splitting Translation` comments.  
  - Inspect train_model_op and evaluate_model_op components for URI parsing regex and BigQuery client `.query(...).to_dataframe()` calls.

- TODO: `Lab 5.8.3` — Parameter Evolution  
  - Search: `# TODO: Lab 5.8.3 - Data Loading Evolution: pandas.read_csv() → BigQuery client` and `# TODO: Lab 5.8.3 - Model Loading Translation: Direct object → artifact loading`  
  - Confirm how function args become component inputs/outputs and how joblib is used to persist/load artifacts (`joblib.dump` / `joblib.load`).

- TODOs for algorithm, persistence, logging:
  - `Lab 5.8.4` — algorithm/feature columns (search `# TODO: Lab 5.8.4`)  
  - `Lab 5.8.5` — line-by-line training mapping (search `# TODO: Lab 5.8.5`)  
  - `Lab 5.8.6` — model persistence (`# TODO: Lab 5.8.6` and sublabels like `5.8.6.2a` → look for `joblib.dump` & `shutil.copy`)  
  - `Lab 5.8.7` — logging evolution (`# TODO: Lab 5.8.7` and metrics.log_metric calls)

---

## ✅ Lab 5.9 — Pipeline Testing and Validation Framework

- TODO: `Lab 5.9.1` — Pipeline Enhancement (automated approval)  
  - Search: `# TODO: Lab 5.9.1 - Pipeline Enhancement: Automated approval logic addition`  
  - Inspect the `dsl.If` blocks that use `eval_task.outputs["Output"]` compared to `min_accuracy`. Confirm the conditional branch that triggers `model_approved_op` and `register_model_op`.

- TODO: `Lab 5.9.2` — Quality Gates  
  - Search: `# TODO: Lab 5.9.2 - Quality Gates: Structured approval vs always-register` and `# TODO: Lab 5.9.1 - Quality Gate Enhancement`  
  - Inspect `model_rejected_op`, `model_approved_op`, and the register_model_op component upload_args to see enriched metadata.

- Additional Lab 5.9.X markers: search for `# TODO: Lab 5.9.X` lines distributed in registration, compile/run, and __main__ compile/submit sections.

---

## ⏱️ Timebox & Suggested Walkthrough (2 hours)

- 0–10 min: open `train_to_vertex_ai_conversion.py` and search/count `# TODO: Lab 5.7`, `# TODO: Lab 5.8`, `# TODO: Lab 5.9` markers. Note any naming variants: `min_accuracy` vs `min_accuracy_threshold` and `output_model` vs `trained_model` occurrences.  
- 10–35 min: Lab 5.7 — imports (5.7.1.*), pipeline metadata and execution (5.7.2.*), parameters (5.7.3).  
- 35–80 min: Lab 5.8 — data loading (5.8.1.*), train_model_op (5.8.1.2*), data parsing (5.8.2.*), model serialization (5.8.6.*), metrics (5.8.7.*).  
- 80–105 min: Lab 5.8 continued — evaluate_model_op and evaluation metrics.  
- 105–120 min: Lab 5.9 — conditional registration, approved/rejected behavior, register_model_op and compile/submit logic.

---

## 📝 Student note expectations (read-only)

- Use exact in-file identifiers: `min_accuracy` (pipeline parameter), `eval_task.outputs["Output"]` (pipeline output used in dsl.If), `train_task.outputs["output_model"]` (artifact name used in register path), `bq_train_task.outputs["destination_table"]`, `joblib.dump` / `shutil.copy`, and metrics keys like `"training_accuracy"`, `"accuracy"`, `"passes_threshold"`.  
- The student does not edit files — they map WHERE (search for the TODO comment), WHAT (what changed or was replaced), WHY (reason given in the comment).

---

## Student Checklist mapping each README TODO to the in-file TODO comment and purpose

Below is a checklist students can use directly. For each TODO entry, search for the exact comment text shown in quotes (use Ctrl/Cmd+F), open the code immediately above and below that comment, and record the mapping in your notes. Each checklist line includes: TODO label → exact in-file TODO comment text to search → purpose.

- Lab 5.7.1  
  - Search for: "# TODO: Lab 5.7.1 - Line-by-Line Import Exploration: Find each train.py import and its pipeline equivalent"  
  - Purpose: Examine original train.py imports (commented block) and the Vertex AI imports block to map each import and note replacements.

- Lab 5.7.1.1 (original imports)  
  - Search for: "# TODO: Lab 5.7.1.1 - ANSWER: Original train.py imports (WHAT: These are the standalone script imports)"  
  - Purpose: Locate commented original imports (argparse, glob, os, pandas, sklearn, mlflow) and note where each was used in train.py.

- Lab 5.7.1.2 (pipeline imports)  
  - Search for: "# TODO: Lab 5.7.1.2 - ANSWER: Vertex AI Kubeflow Pipeline imports (WHAT: These are the cloud-native equivalents)"  
  - Purpose: Inspect kfp, kfp.dsl imports and artifact_types to see cloud equivalents and understand import transformations.

- Lab 5.7.2  
  - Search for: "# TODO: Lab 5.7.2 - High-Level Architecture Exploration: How script metadata becomes pipeline configuration"  
  - Purpose: Read PIPELINE_NAME and PIPELINE_DESCRIPTION mapping and the explanation.

- Lab 5.7.2.1 (pipeline metadata)  
  - Search for: "# TODO: Lab 5.7.2.1 - ANSWER: Pipeline Metadata (WHAT: Pipeline identification and description)"  
  - Purpose: Confirm pipeline naming & description replaced script filename.

- Lab 5.7.2.2 (execution environment)  
  - Search for: "# TODO: Lab 5.7.2.2 - ANSWER: Execution Environment (WHAT: Container-based execution vs local Python)"  
  - Purpose: Confirm BASE_IMAGE and REQUIREMENTS_PATH represent containerized reproducible environment.

- Lab 5.7.3  
  - Search for: "# TODO: Lab 5.7.3 - Data Flow Exploration: train.py sequential calls → pipeline DAG"  
  - Purpose: Inspect pipeline signature (note `min_accuracy` is the pipeline parameter) and how sequential main() steps map to DAG tasks.

- Lab 5.7.4  
  - Search for: "# TODO: Lab 5.7.4 - Task Creation Exploration: Function calls → component instantiation"  
  - Purpose: Compare get_csvs_df(...) -> bigquery_query_job_op task creation (bq_train_task / bq_test_task).

- Lab 5.7.5  
  - Search for: "# TODO: Lab 5.7.5 - Dependency Management: Sequential execution → explicit dependencies"  
  - Purpose: Inspect train_task.after(bq_train_task) and eval_task.after(train_task) demonstrating explicit dependencies.

- Lab 5.8.1  
  - Search for: "# TODO: Lab 5.8.1 - Function Mapping Exploration: How get_csvs_df() becomes BigQuery component"  
  - Purpose: Find the commented original get_csvs_df and the `bigquery_query_job_op = components.load_component_from_url(...)`.

- Lab 5.8.1.1  
  - Search for: "# TODO: Lab 5.8.1.1 - ANSWER: Original train.py data loading function (WHAT: Local CSV file handling)"  
  - Purpose: Inspect the original CSV-loading logic (glob, pandas concat) in comments.

- Lab 5.8.1.2  
  - Search for: "# TODO: Lab 5.8.1.2 - ANSWER: Vertex AI BigQuery Component (WHAT: Cloud-native data access)"  
  - Purpose: Inspect the pre-built BigQuery component and its registry URL.

- Lab 5.8.1.3  
  - Search for: "# TODO: Lab 5.8.1.3 - COMPARISON SUMMARY: Function vs Component transformation"  
  - Purpose: Read the summary of what changed (get_csvs_df → bigquery_query_job_op).

- Lab 5.8.1 (train_model mapping)  
  - Search for: "# TODO: Lab 5.8.1 - Function Mapping Deep Dive: How train_model() becomes train_model_op component"  
  - Purpose: Inspect the annotated original train_model function (comment) and the `@component` train_model_op definition.

- Lab 5.8.1.1 (original train_model)  
  - Search for: "# TODO: Lab 5.8.1.1 - ANSWER: Original train.py train_model function (WHAT: Core ML training logic)"  
  - Purpose: Read commented original train_model and identify model initialization, fit, return.

- Lab 5.8.1.2 (component transform)  
  - Search for: "# TODO: Lab 5.8.1.2 - ANSWER: Component Transformation (WHAT: Function becomes distributed component)" and the `@component(... ) def train_model_op(...):` block  
  - Purpose: Inspect component signature (train_data: Input[artifact_types.BQTable], output_model: Output[Model], metrics: Output[Metrics], reg_rate, project_id, bq_location) and return type float.

- Lab 5.8.2 (data source translation)  
  - Search for: "# TODO: Lab 5.8.2 - Data Source Translation: DataFrame input → BigQuery table parsing"  
  - Purpose: Inspect `uri = train_data.uri` and the regex parsing `re.search(r'projects/([^/]+)/datasets/([^/]+)/tables/([^/]+)', uri)` and BigQuery query.

- Lab 5.8.3 (data loading evolution / model loading)  
  - Search for: "# TODO: Lab 5.8.3 - Data Loading Evolution: pandas.read_csv() → BigQuery client" and "# TODO: Lab 5.8.3 - Model Loading Translation: Direct object → artifact loading" in evaluate component  
  - Purpose: Inspect bq_client.query(...).to_dataframe() and joblib.load(model.path) usages.

- Lab 5.8.4 (feature consistency)  
  - Search for: "# TODO: Lab 5.8.4 - Algorithm Consistency Exploration: Same sklearn code in both versions" and "# TODO: Lab 5.8.4.1" sublabels  
  - Purpose: Confirm FEATURE_COLUMNS list is same as in train.py and used in train & eval.

- Lab 5.8.5 (line-by-line mapping)  
  - Search for: "# TODO: Lab 5.8.5 - Line-by-Line Algorithm Mapping: Identical sklearn training code" and sublabels 5.8.5.1 / 5.8.5.2  
  - Purpose: Identify exact model initialization and model.fit lines and model.score usage.

- Lab 5.8.6 (model persistence)  
  - Search for: "# TODO: Lab 5.8.6 - Model Persistence Translation: return model → artifact serialization" and sublabels 5.8.6.2a / 5.8.6.2b / 5.8.6.2c (look for `joblib.dump` and `shutil.copy`)  
  - Purpose: Trace how the model is written to model.joblib and copied to output_model.path.

- Lab 5.8.7 (logging evolution)  
  - Search for: "# TODO: Lab 5.8.7 - Logging Evolution: print() statements → structured metrics" and sublabels 5.8.7.2* (look for `metrics.log_metric(...)`)  
  - Purpose: Identify metrics keys and how print statements were replaced.

- Lab 5.8.* evaluation extraction entries  
  - Search for: "# TODO: Lab 5.8.1 - Function Extraction Exploration: Evaluation logic separated from training" and evaluate_model_op function block  
  - Purpose: Read evaluation extraction, enhanced metrics (precision/recall), and return accuracy.

- Lab 5.9.1 (approval logic)  
  - Search for: "# TODO: Lab 5.9.1 - Pipeline Enhancement: Automated approval logic addition" and the `with dsl.If(eval_task.outputs["Output"] >= min_accuracy, ...)` block  
  - Purpose: Inspect approval path (model_approved_op → register_model_op).

- Lab 5.9.2 (quality gates)  
  - Search for: "# TODO: Lab 5.9.2 - Quality Gates: Structured approval vs always-register" and `model_rejected_op` component and the `with dsl.If(eval_task.outputs["Output"] < min_accuracy, ...)` block  
  - Purpose: Inspect rejection path and error logging.

- Lab 5.9.X (compile/run and advanced topics)  
  - Search for: "# TODO: Lab 5.9.X" (multiple occurrences around pipeline compilation, register_model_component notes, and advanced topics)  
  - Purpose: Inspect pipeline compile/submit logic in `if __name__ == "__main__":` block and CLI→pipeline parameter mapping.

---

