# Machine Learning Operations Playbook Adoption Workshop – Phase 2: Data Services Integration Architecture - Hands On Workshop

**Session Type:** Explore and hands-on (2 hours recommended per lab)  
**Tools Required:** GCP, and PyCharm or VS Code  
**Files to Open (one per lab):**  
- `lab6_1_s3_model_conversion.py` — Lab 6.1: Amazon S3 Integration with SageMaker Workflows  
- `lab6_2_redshift_pipeline.py` — Lab 6.2: Amazon Redshift Data Pipeline and ML Integration  
- `lab6_4_gcs_vertex_conversion.py` — Lab 6.4: Cloud Storage Integration with Vertex AI Workflows

---

## 🧠 Overview

This Week 6 workshop examines how cloud data services are integrated into ML workflows. You will read and map conversion examples that show how local or legacy file/data patterns are migrated to cloud-native services and how those services are wired into orchestration frameworks (SageMaker Workflows and Vertex AI pipelines). No execution or editing — students only read the code, comments, and `# TODO: Lab X.Y.Z` anchors embedded in the conversion files.

---

## 🎯 Workshop Objectives

- See how S3 is used with SageMaker Workflows to replace local file I/O and enable durable artifact storage.  
- Understand how Redshift can be used as a data warehouse backend for ML pipelines and how ETL/ELT tasks are orchestrated and connected to training tasks.  
- Learn how Cloud Storage (GCS) replaces local files for Vertex AI pipelines and how artifacts flow through components.  
- Trace parameter handling, artifact URI parsing, metrics, and conditional registration patterns adapted for each cloud provider.

---

## 📚 Theory Summary

- Cloud object stores (S3, GCS) provide durable artifact storage; pipelines treat artifact URIs as typed inputs/outputs.  
- Data warehouses (Redshift, BigQuery) replace CSV/DataFrame file patterns with SQL-based access and pre-built integrations.  
- Orchestration (SageMaker Workflows, KFP/Vertex AI) converts sequential script logic into DAGs with explicit dependencies, artifacts, and metrics-driven branches.  
- Migration preserves core algorithm logic while re-homing I/O, monitoring, and registration to cloud-native services.

---

