# Machine Learning Operations Playbook Adoption Workshop – Phase 2: Data Services Integration Architecture - Hands-On Workshop

## 🚀 Migration Machine Learning Operations Data Services Integration
### Module Learning Objectives

- Review knowledge of Amazon S3 integration with SageMaker workflows  
- Review knowledge of Amazon Redshift integration with ML pipelines  
- Review how EC2/SageMaker models use S3 for artifact persistence and CSV/flat file input/output  
- Review how Redshift pipelines use COPY/UNLOAD and SQL transformations for ML data preparation  
- Prepare for migration by mapping AWS data service patterns to Google Cloud equivalents (Vertex AI, GCS, BigQuery)  
- Practice searching for and interpreting `# TODO: Lab 6.X.X.X.X` markers in code files (`model.py`, `ingest_model.py`)  

---

### Prerequisites

- AWS Management Console access with SageMaker and Redshift permissions  
- IAM role with `AmazonSageMakerFullAccess`, `AmazonS3FullAccess`, and Redshift query permissions  
- Python 3.9+ environment with `boto3`, `joblib`, `pandas`, and `psycopg2` or `sqlalchemy` installed  
- Access to the GitHub Training Repo containing `model.py` and `ingest_model.py` files with embedded TODO markers  
- Pre-created S3 bucket for input/output artifacts and Redshift cluster with sample schema  

---

# 🧪 Lab 6.1: Amazon S3 Integration with SageMaker Workflows (High-level Review)

**Difficulty:** Introductory Review  
**Tools Required:** GitHub Training Repo (`model.py`)  

---

## 🎯 Lab Objectives

- Review how ML models running on EC2 or SageMaker use S3 for artifacts  
- Identify boto3 usage patterns for uploading/downloading models and data  
- Understand local staging → S3 upload → SageMaker registry integration  
- Explore logging and metrics evolution from print/MLflow → CloudWatch/SageMaker metrics  

---

## 1. Prerequisites

- AWS account with SageMaker Studio or Notebook access  
- IAM role with `AmazonSageMakerFullAccess` and `AmazonS3FullAccess`  
- Python 3.9+ environment with `boto3` and `joblib` installed  
- Access to `model.py` in the GitHub Training Repo  

---

## 2. Theory Overview

Amazon S3 is the primary durable artifact store for ML workloads in AWS.  
- Trainers on EC2 or SageMaker stage files locally, then upload to S3 for persistence.  
- Models are serialized with `joblib` or `pickle` and stored in S3 buckets.  
- S3 also serves as input/output for CSVs and flat files.  
- Logging evolves from local print statements to CloudWatch metrics and SageMaker structured metrics.  

---

## 3. Sequential Lab Tasks

Each task maps directly to commented sections in `model.py`. Use VSCode/PyCharm search for `# TODO: Lab 6.1.X.X`.

- Search: `# TODO: Lab 6.1.1 - Line-by-Line Import Exploration`  
  - Where: Top of `model.py` imports  
  - What: Inspect `joblib`, `boto3` references  
  - Why: Understand which libraries enable local vs S3 persistence  

- Search: `# TODO: Lab 6.1.2 - Execution Model Translation`  
  - Where: `train()` function signature and persistence branches  
  - What: Compare `dat.get_handle()` vs manual S3 upload  
  - Why: Distinguish local dev vs orchestrated SageMaker workflows  

- Search: `# TODO: Lab 6.1.3 - Parameter and Artifact Evolution`  
  - Where: `_select_features()` and artifact naming logic  
  - What: Observe feature selection rules and artifact naming conventions  
  - Why: Understand reproducibility and artifact compatibility  

- Search: `# TODO: Lab 6.1.4 - S3 Data Loading Conversion`  
  - Where: `_s3_persist()` function  
  - What: Inspect `boto3.upload_file` usage  
  - Why: Learn durable storage and IAM/cost implications  

- Search: `# TODO: Lab 6.1.5 - Artifact Persistence and Model Registry Integration`  
  - Where: Branch where `model_path` starts with `s3://`  
  - What: Inspect local temp file → S3 upload pattern  
  - Why: Understand registry integration and artifact governance  

- Search: `# TODO: Lab 6.1.6 - Logging and Metrics Evolution`  
  - Where: End of `train()` function  
  - What: Inspect `LOG.info` statements for elapsed time, feature count, artifact path  
  - Why: Understand structured logging for reproducibility and monitoring  

---

# 🧪 Lab 6.2: Amazon Redshift Data Pipeline and ML Integration (High-level Review)

**Difficulty:** Introductory Review  
**Tools Required:** GitHub Training Repo (`ingest_model.py`)  

---

## 🎯 Lab Objectives

- Review Redshift ingestion/extraction patterns (COPY, UNLOAD, Data API)  
- Identify ETL task mapping (CTAS, materialized views, pre-aggregation)  
- Understand orchestration and dependency mapping (Step Functions, Airflow, SageMaker Pipelines)  
- Explore data movement and performance considerations (distribution/sort keys, compression, cluster sizing)  
- Review model training integration with Redshift outputs staged to S3 or streamed via Data API  
- Discuss monitoring and cost trade-offs  

---

## 1. Prerequisites

- AWS account with Redshift cluster access  
- IAM role with `AmazonRedshiftFullAccess` and `AmazonS3FullAccess`  
- Python 3.9+ environment with `psycopg2` or `sqlalchemy` installed  
- Access to `ingest_model.py` in the GitHub Training Repo  

---

## 2. Theory Overview

Amazon Redshift serves as a data warehouse for ML pipelines.  
- Data access patterns include COPY from S3, UNLOAD to S3, and direct queries via JDBC/Data API.  
- ETL tasks transform data using SQL (CTAS, materialized views).  
- Trainers consume Redshift outputs either staged in S3 or streamed directly.  
- Performance depends on distribution/sort keys, compression, and cluster sizing.  
- Monitoring includes query cost, cluster utilization, and egress charges.  

---

## 3. Sequential Lab Tasks

Each task maps directly to commented sections in `ingest_model.py`. Use VSCode/PyCharm search for `# TODO: Lab 6.2.X.X`.

- Search: `# TODO: Lab 6.2.1 - Data Access Pattern Conversion`  
  - Where: `_read_from_redshift()` function  
  - What: Inspect `select_sql_from_dict` or `pd.read_sql` usage  
  - Why: Understand Redshift → DataFrame conversion patterns  

- Search: `# TODO: Lab 6.2.2 - ETL Task Mapping`  
  - Where: `prepare_redshift_training()` function  
  - What: Inspect ingest_obj methods and SQL transformations  
  - Why: Map SQL queries to ETL tasks  

- Search: `# TODO: Lab 6.2.3 - Orchestration and Dependency Mapping`  
  - Where: `orchestration_hint_tasks()` function  
  - What: Inspect documented task list (extract, transform, stage, train, register)  
  - Why: Understand DAG dependencies and orchestration  

- Search: `# TODO: Lab 6.2.4 - Data Movement and Performance Considerations`  
  - Where: `stage_table_to_s3()` and `quick_sample_pipeline()` functions  
  - What: Inspect UNLOAD vs client-side upload patterns  
  - Why: Learn efficiency vs cost trade-offs  

- Search: `# TODO: Lab 6.2.5 - Model Training Integration`  
  - Where: Return of `prepare_redshift_training()`  
  - What: Inspect `(df, s3_uri)` outputs  
  - Why: Understand training consumption patterns (in-memory vs staged artifacts)  

- Search: `# TODO: Lab 6.2.6 - Monitoring and Cost Trade-offs`  
  - Where: `teaching_checklist()` function  
  - What: Inspect listed monitoring signals and cost drivers  
  - Why: Understand observability and economics of Redshift pipelines  

---

### Module Learning Objectives

- Understand Cloud Storage integration with Vertex AI workflows  
- Learn how BigQuery ML can train models directly using SQL   

---

### Prerequisites

- GCP project with Vertex AI, BigQuery, and Cloud Storage enabled  
- Service account with `Storage Admin`, `BigQuery Admin`, and `Vertex AI Admin` roles  
- Python 3.9+ environment with `google-cloud-aiplatform`, `google-cloud-bigquery`, `google-cloud-storage` installed  
- Access to BigQuery public datasets (e.g., Penguins dataset)  
- GitHub Training Repo containing starter notebook code  

---

# 🧪 Lab 6.4: Cloud Storage Integration with Vertex AI Workflows

**Difficulty:** Intermediate  
**Tools Required:** Google Cloud Console, Cloud Storage, Vertex AI SDK for Python  

---

## 🎯 Lab Objectives

- Install and configure Vertex AI and BigQuery SDKs  
- Authenticate and set up project information  
- Create and configure a Cloud Storage bucket for ML artifacts  
- Assign service accounts for pipeline execution  
- Initialize Vertex AI SDK with Cloud Storage staging bucket  
- Compare Cloud Storage integration to Amazon S3 workflows from Lab 6.1  

---

## 1. Prerequisites

- GCP project with Vertex AI and Cloud Storage enabled  
- Service account with `Storage Admin` and `Vertex AI Admin` roles  
- Python environment with required SDKs installed  

---

## 2. Theory Overview

Cloud Storage is the **artifact backbone** for Vertex AI workflows.  
- Buckets store datasets, intermediate files, and exported models  
- Vertex AI pipelines reference GCS URIs (`gs://bucket-name/path`) for inputs and outputs  
- IAM roles control access to buckets, ensuring reproducibility and governance  
- Cloud Storage replaces S3 in AWS workflows, but the integration pattern is nearly identical  

---

## 3. Sequential Lab Tasks

- **Task 6.4.1 — Install SDKs**  
  - Command: `! pip3 install --upgrade --quiet pyarrow google-cloud-aiplatform google-cloud-bigquery google-cloud-bigquery-storage db-dtypes`  
  - WHY: Enable Python environment to interact with Vertex AI and BigQuery  

- **Task 6.4.2 — Authenticate Environment**  
  - Code: `auth.authenticate_user()` (Colab only)  
  - WHY: Ensure secure access to GCP resources  

- **Task 6.4.3 — Set Project Information**  
  - Code: `PROJECT_ID = "..."`, `LOCATION = "us-east1"`  
  - WHY: Required for all GCP API calls  

- **Task 6.4.4 — Create Cloud Storage Bucket**  
  - Code: `BUCKET_URI = f"gs://churn-user19-{PROJECT_ID}-unique"`  
  - Command: `! gsutil mb -l {LOCATION} {BUCKET_URI}`  
  - WHY: Buckets store datasets and exported models  

- **Task 6.4.5 — Configure Service Account**  
  - Code: `SERVICE_ACCOUNT = "vertex-pipeline-executor@..."`  
  - WHY: Service accounts provide secure, auditable access  

- **Task 6.4.6 — Initialize SDKs**  
  - Code:  
    ```python
    aiplatform.init(project=PROJECT_ID, staging_bucket=BUCKET_URI)
    bqclient = bigquery.Client(project=PROJECT_ID)
    ```  
  - WHY: Required for pipeline jobs and queries  

---

# 🧪 Lab 6.5: BigQuery ML and Vertex AI Integration Patterns

**Difficulty:** Intermediate to Advanced  
**Tools Required:** Google Cloud Console, BigQuery, Vertex AI SDK for Python  

---

## 🎯 Lab Objectives

- Train ML models directly in BigQuery using SQL  
- Evaluate BigQuery ML models with SQL functions  

---

## 1. Prerequisites

- GCP project with BigQuery and Vertex AI enabled  
- Service account with `BigQuery Admin` and `Vertex AI Admin` roles  
- Python environment with required SDKs installed  
- Access to BigQuery public datasets (e.g., Penguins dataset)  

---

## 2. Theory Overview

BigQuery ML allows you to **train ML models directly in SQL**.  
- Models are stored as BigQuery resources  
- Evaluation uses SQL functions like `ML.EVALUATE`  
- Exported models can be uploaded to Vertex AI for deployment  
- Integration pattern: BigQuery ML → Cloud Storage → Vertex AI Model Registry → Endpoint deployment  

---

## 3. Sequential Lab Tasks

- **Task 6.5.1 — Create BigQuery Dataset**  
  - SQL: `CREATE SCHEMA penguins`  
  - WHY: Organize tables and models in BigQuery  

- **Task 6.5.2 — Train BigQuery ML Model**  
  - SQL:  
    ```sql
    CREATE OR REPLACE MODEL penguins
    OPTIONS(model_type='DNN_CLASSIFIER', labels=['species'])
    AS SELECT * FROM `bigquery-public-data.ml_datasets.penguins`
    ```  
  - WHY: Learn SQL‑based ML training  

- **Task 6.5.3 — Evaluate Model**  
  - SQL:  
    ```sql
    SELECT * FROM ML.EVALUATE(MODEL penguins)
    ORDER BY roc_auc DESC LIMIT 1
    ```  
  - WHY: Validate model performance  

---

## ✅ Summary

- ## **Lab 6.4** teaches Cloud Storage integration with Vertex AI workflows, mirroring S3 integration 
- **Lab 6.5** teaches BigQuery ML integration with Vertex AI, mirroring Redshift + AWS ML workflows  
- Both labs use the **scavenger hunt style** with `# TODO` anchors, guiding learners to record WHERE, WHAT, and WHY for each integration step.

---

- # **Lab 6.6: Google Cloud Data and Analytics Architecture for ML is a hands‑on exercise that teaches how to design and implement an end‑to‑end machine learning workflow using Google Cloud’s data and analytics services. It focuses on connecting BigQuery, Vertex AI,

- ### Data ingestion and storage

- ### Using BigQuery as the central data warehouse for structured datasets.
- ### Model training in BigQuery ML
- ### Model registration in Vertex AI
