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

## 🔧 Lab 5.1: SageMaker Pipeline Component Architecture Overview

- Tools Required: GitHub Training Repo
- Difficulty: Intermediate

#### Lab Objectives

- Understand SageMaker Pipeline architecture as a Directed Acyclic Graph (DAG)
- Understand the core SageMaker Pipeline step types and their purposes as components
- Analyze pipeline data dependencies and step relationships
- Prepare foundation knowledge for detailed implementation in Lab 5.2

### Step 1: Pipeline Concept Introduction and DAG Structure

- Understand SageMaker Pipelines as interconnected steps in a Directed Acyclic Graph (DAG) structure.

- Navigate to AWS SageMaker Console
- Select SageMaker Studio from the left navigation panel and launch Studio
- In SageMaker Studio, navigate to Pipelines section in the left sidebar
- Review the pipeline visualization interface and DAG representation
- Understand that a SageMaker AI pipeline is "a series of interconnected steps in directed acyclic graph (DAG) that are defined using the drag-and-drop UI or Pipelines SDK" Pipelines overview
- Examine how "data dependencies are created when the properties of a step's output are passed as the input to another step" Pipelines overview

#### key characteristics of DAG structure:

- Directed: Steps have clear input/output flow direction
- Acyclic: No circular dependencies between steps
- Graph: Visual representation of step relationships

### Step 2: Pipeline Data Dependencies and Relationships

- Analyze how data flows between pipeline steps and creates execution dependencies.

- Create a new notebook in SageMaker Studio with Python 3 (Data Science) kernel
- Import basic SageMaker pipeline libraries to explore step types:

```python
   import sagemaker
   from sagemaker.workflow.pipeline import Pipeline
   from sagemaker.workflow.steps import ProcessingStep, TrainingStep
```

- Understand that "the structure of a pipeline's DAG is determined by the data dependencies between steps" Pipelines overview
- Analyze the example pipeline structure from the GitHub Training Repo:

- Process: Data preprocessing step
- Train: Model training step
- Eval: Model evaluation step
- Condition: Conditional logic step
- Register Model: Model registration step
- Create Model: Model creation step
- Batch: Batch inference step


- Document data flow patterns and dependency relationships between steps

### Step 3: Processing Steps for Data Preparation (20 minutes)

- Explore Processing steps for data preprocessing, feature engineering, and model evaluation.

- Understand that Processing steps like "Process" run "a preprocessing script on the data used for training" and can "fill in missing values, normalize numerical data, or split data into the train, validation, and test datasets"

#### Pipelines overview

- Navigate to SageMaker > Processing jobs to examine processing infrastructure
- Review Processing step characteristics:

- Data preprocessing: Feature engineering, data cleaning, normalization
- Data splitting: Train/validation/test dataset creation
- Model evaluation: Post-training model assessment and metrics calculation
- Custom scripts: Python scripts for specific processing tasks

