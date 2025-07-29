# MLOPS Model Migration Workshop – Week 1: Introduction and Foundation Setup - Hands-On Workshop

---

## 🚀 Migration Overview and Business Case

### Module Learning Objectives

By the end of this workshop, participants will be able to:

- Analyze current AWS costs and identify optimization opportunities using AWS Console
- Navigate Google Cloud Console billing and cost management tools effectively
- Build a compelling business case for SageMaker to Vertex AI migration
- Establish cost baselines and tracking mechanisms for migration success

### Prerequisites

- AWS Management Console access with billing permissions
- Google Cloud Console access with billing account access
- Basic AWS and Google Cloud knowledge
- Web browser (Chrome, Firefox, Safari, or Edge)
- Participants are recommended to use browser capabilities such as Incognito or In private Browser Sessions due to single-sign-on and cached credential login challenges.

### Workshop Overview

This comprehensive workshop establishes the financial foundation for migrating AWS SageMaker workloads to Google Cloud Vertex AI. Participants will master cost management tools on both platforms using only web-based console interfaces and develop compelling business cases for migration decisions.

---

## 💰 Lab 1.1: AWS Cost Management Tools Exploration and Analysis

### Lab Information

- Duration: 4 hours
- Tools Required: AWS Management Console, web browser, spreadsheet application
- Difficulty: Intermediate

### Lab Objectives

- Master AWS Cost Explorer and AWS Budgets for SageMaker workloads
- Analyze current SageMaker spending patterns and trends
- Identify cost optimization opportunities in existing ML infrastructure
- Create detailed cost breakdown for migration planning

---

## Section 1: AWS Cost Explorer Deep Dive (60 minutes)

### Step 1.1: Access and Navigate AWS Cost Explorer (15 minutes)

#### 🎯 Goal

Set up and familiarize yourself with the AWS Cost Explorer interface.

#### Updated Instructions

1. Open your web browser
2. Navigate to the AWS Management Console
3. Sign in with your AWS credentials
4. In the **AWS Console Search Bar**, type **Cost Explorer**
5. Select **Cost Explorer** from the Billing and Cost Management feature
6. (Optional) Click **Launch Cost Explorer** (first-time users may experience up to a 24-hour delay for data population)

#### Initial Cost Explorer Setup

**Setup Checklist:**

- Verify the main dashboard is visible
- Set time range to **Last 3 months** using the date picker, and select **Apply**
- Set granularity to **Monthly**
- Group by **Service**
- In the Advanced options section, select **Show Forecasted values** at the bottom of the chart from the additional data settings.

#### Interface Familiarization

- Explore the dashboard chart area
- Try the built-in chart types (bar, line, stacked)
- Review the filters panel


💡 Pro Tip: Use preconfigured views like “Monthly costs by service” or “RI Utilization” for quick insights. Capture screenshots of your initial dashboard for later comparison.

---

### Step 1.2: SageMaker Cost Analysis (25 minutes)

⚠️ Important: Focus on **Amazon SageMaker** costs to understand current ML spend.

#### 1. Filter for SageMaker Services

- In the Filters panel, click **Service**
- Search and select **SageMaker**
- Click **Apply**
- Set the Date range to **6 months**
- Change granularity to **Daily**

#### 2. Analyze SageMaker Cost Components

- Select **Usage Type** and review.
- Identify top cost drivers
- Click chart segments to drill down
- Log findings in a spreadsheet. **Ask presenter to share template and example worksheet.**

#### 3. Create Cost Breakdown Analysis Table

| Component           | Monthly Cost | % of Total | Trend   | Instance Types/Notes         |
|---------------------|--------------|------------|---------|------------------------------|
| Training Instances  | $X,XXX       | XX%        | ↑/↓/→   | ml.p3.2xlarge, ml.g5.xlarge  |
| Notebook Instances  | $XXX         | XX%        | ↑/↓/→   | Development environments     |
| Endpoints           | $X,XXX       | XX%        | ↑/↓/→   | Production model serving     |
| Storage (S3)        | $XXX         | XX%        | ↑/↓/→   | Training data, models        |
| Data Transfer       | $XXX         | XX%        | ↑/↓/→   | Inter-region, internet       |
| Other Services      | $XXX         | XX%        | ↑/↓/→   | Supporting AWS services      |

#### 4. Document Key Findings

- The following questions should be answered in your analysis:
- Which instance types consume the most budget?
- When is usage the highest?
- Any idle periods or unnecessary resources?
- Ratio between training and inference costs?

---

### Step 1.3: Advanced Cost Analysis Techniques (20 minutes)

#### 1. Usage Pattern Analysis

**Important**: Enabling hourly granularity can take up to 48 hours to populate data. For hourly-level data, we charge $0.01 per 1,000 usage records monthly.

**Note**: This is optional but may not be available for all accounts.

- Switch to **Hourly** granularity for the recent week
- Detect peak usage periods and idle patterns
- Switch back to **Daily** to document seasonal behavior
- Use **Amazon Q Developer** for insights like:
  - “Which region had the largest cost increase last month?”

#### 2. Explore Additional Filters

Try filters for:

- **Region**: Concentration of activity
- **Usage Type**: (e.g., ml.t3.medium)


#### 3. Cost Anomaly Detection Review

**New Feature:** Cost Anomaly Detection enabled by default (as of March 2025)

- In the AWS Console **Search Bar**, type **Cost Anomaly Detection**
- Select the service
- Select **Get started**, and take the tour if available. Do not create a new cost monitor. If needed, cancel to return to the main dashboard.
- Review existing **detected anomalies** and **cost anomaly detection summary**.
- Click into **cost monitors** and **Alert subscriptions** to review existing configurations.
- Document findings

💡 Pro Tip: Idle weekends or underutilized resources are low-hanging fruit for cost cuts.


## Section 2: AWS Budgets and Alerts Configuration (45 minutes)

---

### Step 2.1: Create SageMaker-Specific Budget (20 minutes)

#### 1. Navigate to AWS Budgets

- In the AWS Console search bar, type **“Budgets”**
- Select “AWS Budgets” from the search results
- Click the **Create budget** button

#### 2. Configure Cost Budget

**Budget setup:**

- Under **Budget setup**, choose **Customize (advanced)**
- Budget type: **Cost budget**
- Select **Next**
- Budget name: `SageMaker-ML-Workloads-Monthly`
- Period: **Monthly**
- Budget renewal type: **Recurring budget**
- Start month: Choose the current month

**Set budget amount:**

- Budgeting method: **Fixed**
- Enter amount: `$[Current monthly SageMaker spend + 20% buffer]`
- Advanced options: **Unblended costs**

**Budget scope (Filters):**

1. Select **Filter specific AWS cost dimensions**
2. Click **Add filter**
3. Select **Service** from the dropdown
4. Choose **Amazon SageMaker**
5. Click **Apply filter**

#### 3. Configure Alert Thresholds

**Note**: You do not need to create every alert threshold.

1. Click **Next** to proceed to alert configuration
2. Select **Add an alert threshold**
2. Set up multiple alerts:

   - **Alert 1 – Early Warning**
     - Threshold: 75%
     - Trigger: **Forecasted**
     - Recipients: ML team leads’ emails

   - **Alert 2 – Critical Alert**
     - Click **Add an alert threshold**
     - Threshold: 90%
     - Trigger: **Actual**
     - Recipients: Additional stakeholders

   - **Alert 3 – Budget Exceeded**
     - Click **Add an alert threshold**
     - Threshold: 100%
     - Trigger: **Actual**
     - Recipients: Management escalation contacts
     - Select **Next**

**Enhanced Alert Options (2025 Feature):**

- Check **AWS User Notifications**
- Configure AWS Chatbot alerts for Slack/Chime if available

3. Click **Next**, review configuration, then **Create budget**

---

### Step 2.2: Advanced Budget Configuration (25 minutes)

**Important**: > This task is optional. Participants can skip this task to proceed to the GCP section which is the main focus of the workshop.

#### 1. Create Environment-Specific Budgets

**Development Environment Budget:**

- Return to the Budgets dashboard and click **Create budget**
- Select **Customize (advanced)** → **Cost budget**
- Budget name: `ML-Development-Environment`
- Period: **Monthly**
- Method: **Fixed**
- Amount: `$500`
- Filters:
  - Tags: `Environment:Development`
  - Service: Amazon SageMaker

**Production Environment Budget:**

- Click **Create budget** again
- Budget name: `ML-Production-Environment`
- Period: **Monthly**
- Method: **Fixed**
- Amount: `$5,000`
- Filters focused on production resources

#### 2. Budget Actions Configuration (2025 Feature)

1. In the budget creation wizard, scroll to **Actions**
2. Click **Add action**
3. Configure automated response:
   - Action type: Apply IAM policy or target EC2/RDS instances
   - Threshold: 90% actual spend
   - Execution: Require approval (recommended) or Automatic
4. Define policy or instance targeting criteria

#### 3. Budget Monitoring Setup

- Navigate to the main Budgets dashboard
- Review all created budgets in list view
- Click each budget **radio box** to view details in the right panel **Budget preview.**
- Check the **Thresholds** column for status (Green, Yellow, Red) Green is OK, Yellow is approaching threshold, Red is over budget.
- Document the monitoring process

---

## Lab 1.1 Deliverables Checklist

- AWS cost analysis report with detailed SageMaker breakdown
- Configured AWS budgets with alert thresholds and actions
- Optimization recommendations document
- Ongoing monitoring process documentation
- Baseline cost data for GCP migration comparison

---

## ☁️ Lab 1.2: Google Cloud Console Cost Management and Billing Tools Deep Dive

---

### Lab Information

- Duration: 4 hours
- Tools Required: Google Cloud Console only, web browser, spreadsheet application
- Difficulty: Intermediate

### Lab Objectives

- Master Google Cloud billing and cost management tools using console interface only
- Understand GCP pricing models for Vertex AI and supporting services
- Implement cost controls and monitoring for GCP ML workloads through console
- Create comprehensive cost comparison framework between AWS and GCP

---

## Section 1: Google Cloud Billing Console Deep Dive (60 minutes)

### Step 1.1: Billing Account Setup and Navigation (20 minutes)

1. Open your web browser
2. Navigate to the Google Cloud Console and sign in: [Google Cloud Console](https://console.cloud.google.com/)

![Google Cloud Console Welcome Page](media/images/GCP_Console_Welcome.png)

3. In the top left corner of the console by the Google Cloud logo, Select the **Project Picker**. The project picker may display your organization name or a project name. For example, it may display **cloudlearningsolution** or the project **MFAv2**. It may also display **No organization** if you are not part of an organization.

![Google Cloud Console Welcome Page](media/images/Project_Picker.png)

3. After selecting the project picker regardless of the default setting, ergo; **cloudlearningsolution**. In the **Select a resource** box, select if not already displayed the organization **cloudlearningsolution**, then select your project by clicking **All** and then selecting your project name. Review the Type column to ensure you are selecting a project and not an organization or folder.
    **Note**: You may need to expand the domain name to see and select your project.

![Google Cloud Console Welcome Page](media/images/Project_Name_Selected.png)
3. In the **GCP Console Search Bar**, type `All Products` and select **All Products** from the drop-down options.
4. On the All Products page, under the **Management** section, click **Billing**
5. Select your billing account from the Billing screen. You may need to select **My projects** to see your billing account.

#### Billing Account Configuration Review

- Click **Account management**
- Verify permissions:
  - Click or view **+ Add principal** (**Note**: You may not have permission)
  - Confirm your billing role (Billing Account; Administrator, User, or Viewer) by reviewing the **Role / Principal** column. Click to expand the role names to view the users or services known as principals.
  - Document your access level
- Review account hierarchy in the **Account management** section:
  - Note linked projects
- Check payment settings:
  - Click **Payment settings**
  - Review but do not edit or request to edit payment methods and automatic payment alerts

#### Initial Billing Dashboard Overview

- Click **Overview**
- Review current month spending:
  - Note total month-to-date spend
  - Identify top spending services
  - Check spending by viewing the billing report
  - Select **View report** under the **Top Services** chart
- Analyze service-level breakdown: click **Group by (Service)** (Note: By default the report groups cost by "Service")
- Interact with the Chart: Hover your pointer over any part of the chart. A tooltip will appear showing costs for each service.


---

### Step 1.2: Cloud Billing Reports Analysis (25 minutes)

1. In the **GCP Console Search Bar**, type `Reports` and select **Reports**, which is also available under **Cost management**
2. Familiarize yourself with the Reports interface

#### Configure Analysis View

- Set time range to **Last 90 days**
- Group by: Service, Project, Project hierarchy (folder-level), or SKU. Leave as default **Service**.
- Apply filters: Projects, Services, SKUs, Locations, Labels, Folders & Organizations

#### Analyze Current GCP Usage for ML Services

- Use the Filters panel to include only AI/ML services: Note: To toggle panel filters, click the **Filters** button in the top right corner of the Reports interface its icon looks like the following symbol **"<|"**
  - Vertex AI
  - Compute Engine
  - Cloud Storage
  - Artifact Registry
- Participants take note of the current baseline:
  - Note usage patterns

#### Enhanced Report Features (2025)

- Save custom view: click **Save as new**, name “ML Migration Baseline” and set it as your monitoring view
- Export report data: click **Print** or select **Download CSV** for offline AWS/GCP comparison

---

### Step 1.3: Advanced Billing Analysis Features (15 minutes)

#### Custom Time Ranges and Detailed Views

- In the Reports interface date picker, try:
  - **Last 30 days** for recent patterns
  - **Last 12 months** for long-term trends
- Toggle granularity between **Monthly** and **Daily**

#### Enhanced Savings and Credits Analysis (2025)

1. In the **GCP Console Search Bar**, type `FinOps hub` and select **FinOps hub** (formerly Savings & credits). In a later task, you will learn how to use the FinOps hub to analyze savings and credits.

2. Review subcategories in Cost optimization: committed use discounts and CUD analysis.

---

### Step 1.4: GCP Cost Projection Matrix

Create this table in your spreadsheet for future ML workload planning:

| Service Category       | Current Monthly Cost | Projected ML Cost | Migration Notes                  |
|------------------------|----------------------|-------------------|----------------------------------|
| Vertex AI Training     | $0                   | $X,XXX            | Based on AWS SageMaker analysis  |
| Vertex AI Prediction   | $0                   | $XXX              | Endpoint hosting equivalent      |
| Compute Engine         | $XXX                 | $X,XXX            | Custom training VMs              |
| Cloud Storage          | $XXX                 | $XXX              | Data storage migration           |
| Networking             | $XXX                 | $XXX              | Data transfer and egress         |
| Other Services         | $XXX                 | $XXX              | Supporting infrastructure        |


---


## Section 2: Google Cloud Budgets and Alerts Configuration (45 minutes)

---

### Step 2.1: Create ML Workload Budget (20 minutes)

1. Navigate to Budget Creation

   - In the billing console left sidebar, click “Budgets & alerts”
   - Click “Create budget” button

2. Budget Scope and Configuration

   **Budget details:**
   - Name: `Vertex-AI-ML-Workloads`
   - Time range: Monthly (recurring)
   - Enhanced options (2025): Monthly, Quarterly, Yearly, or Custom range available

   **Budget scope:**
   - Projects: Select “All projects” or specific ML-related projects
   - Services: Click “Add filter” → “Services” then select Vertex AI, Compute Engine, Cloud Storage
   - Optional filters: Labels, folders, or credit filters (leave unfiltered for broader coverage)

3. Set Budget Amount

   - Type: “Specified amount”
   - Alternative (2025): “Last period’s spend” for dynamic budgeting
   - Amount: `$[Enter estimated monthly ML spend based on AWS analysis]`
   - Currency: Auto-detected based on billing account (verify)

4. Configure Alert Thresholds

   - Click “Next” to proceed
   - Set multiple threshold rules:
     - 50% Alert – Early Warning (Actual spend) to billing admins and users
     - 75% Alert – Planning Alert (Actual spend)
     - 90% Alert – Critical (Actual spend)
     - 100% Forecasted Alert (Forecasted spend)
   - Click “Finish” to create the budget

---

### Step 2.2: Environment-Specific Budget Setup (25 minutes)

1. Create Development Environment Budget

   - In Budgets & alerts, click “Create budget”
   - Name: `ML-Development-Environment`
   - Time range: Monthly
   - Budget amount: $500
   - Currency: [Verify billing account currency]
   - Scope: Projects for development/testing and Services filter for Vertex AI and Compute Engine
   - Alert thresholds:
     - 50% – Early alert
     - 75% – Mid-cycle planning
     - 90% – Critical
   - Click “Finish”

   Tip: Define projects using naming conventions (e.g., dev-, test-) for governance efficiency.

2. Create Production Environment Budget

   - Click “Create budget”
   - Name: `ML-Production-Environment`
   - Time range: Monthly
   - Budget amount: $5,000
   - Currency: [Verify billing account currency]
   - Scope: Projects for production and Services for prediction-related services (Vertex AI, Cloud Storage)
   - Alert thresholds:
     - 25% – Initial spend signal
     - 50% – Midpoint
     - 75% – Escalation
     - 90% – Critical
     - 100% Forecasted – Predictive alert
   - Click “Finish”

3. Budget Dashboard Review

   - Return to “Budgets & alerts” in the billing console
   - Review all budgets: Confirm naming, amounts, and scope; ensure thresholds are set
   - Monitor current spend vs. budget
   - Test alert email functionality: temporarily adjust threshold to 1%, monitor for alert email, restore original threshold

   Note: Alert testing may not generate emails immediately due to notification lags and single-trigger-per-threshold limits.


---

## Section 3: Google Cloud Pricing Calculator Analysis (60 minutes)

---

### Step 3.1: Access and Setup Pricing Calculator (15 minutes)

1. Access Google Cloud Pricing Calculator

   - Open a new browser tab
   - Navigate to: [Google Cloud Pricing Calculator](https://cloud.google.com/products/calculator)
   - Select **+ Add to estimate**
   - Review available products by clicking **Sort by most popular**, then select **Sort by product name** from the drop down menu


2. Prepare for ML Workload Estimation

   - Reference your AWS analysis: have your SageMaker cost breakdown available
   - Reference region to match typical AWS usage by region

---

### Step 3.2: Vertex AI Training Cost Estimation (20 minutes)

1. Add Vertex AI Custom Training

   - In the calculator, Search by product name by searching for “Vertex AI training”
   - Configure training parameters based on your AWS analysis:
     - Region: Use the same region as your AWS SageMaker usage
     - Machine type: n1-standard-8 (closest to ml.m5.2xlarge). Alternatively, use machine types similar to your AWS instance types.
     Note: Machine Types Website: https://cloud.google.com/vertex-ai/docs/training/configure-compute#machine-types
     - In Accelerator Type, select **No accelerator**, alternatively, select **GPU, or TPU** if your AWS SageMaker training job uses acclerators.
     - In the Machine Type Machine Family section, select **General purpose**, alternatively select **Compute optimized or Memory optimized** based on your AWS instance type.
     - In Series, select **N1** or **N2** based on your AWS instance type.
     - In Machine Type, select **n1-standard-4**, or **n2-standard-4**.
     - Average training job length (hours): [Based on AWS SageMaker analysis] Enter **6**
     - Number of training jobs per month: [Based on current frequency] Enter **90**

   - **Do not add any additional training jobs at this time. The following information is for future consideration**:
   - Add GPU configuration if needed:
     - GPU type: NVIDIA V100 (if using GPU instances)
     - Number of GPUs: match AWS configuration
     - GPU hours per month: [Based on AWS usage]

   - The following information can be completed by using the same task steps as aforementioned in the section **Add Vertex AI Custom Trianing**.
   - Add storage for training:
     - Select from Service type, **Persistent disk**: 100 GB SSD
     - Zonal Standard PD: 100 GB
     - Ensure the same region as your training jobs
     - Snapshot Storage: 100 GiB
     - Total Disks: Enter **1** (default)
     - (Optional) Adjust size based on your storage needs

2. (Optional) Configure Multiple Training Scenarios

   - Development training: smaller instances, fewer hours
   - Production training: larger instances, include batch jobs

---

### Step 3.3: Vertex AI Prediction and Supporting Services (25 minutes)

1. Add Vertex AI Prediction Endpoints

   - In the calculator, click **“Vertex AI” →  "prediction”**

2. Add Cloud Storage Estimation

   - Search for “Cloud Storage”
   - Configure storage tiers:
     - Standard: [GB] for active data
     - Nearline: [GB] for infrequent data
     - Archive: [GB] for long-term retention
   - Operations:
     - Class A operations (uploads/writes): [Count]
     - Class B operations (downloads/reads): [Count]

3. Add Compute Engine for Custom ML Workloads

   - Search for “Compute Engine”
   - Configure VM instances:

4. Add Networking Costs

   - Search for “Network”
   - Configure data transfer:
     - Egress to internet: [GB]
     - Inter-region traffic: [GB]

---

### Step 3.4: Generate and Analyze Estimate (10 minutes)

1. Review Total Estimate

   - Scroll to the Estimated Costs section
   - Review monthly total
   - Select **Open Detailed View** to see breakdown by service
   - Review the Cost Estimate Summary


2. Save and Export Estimate

   - Share estimate: click “Share" and save the URL Link
   - Export data: click Download CSV → download CSV for detailed analysis


---

## Section 4: Cost Comparison Framework Development (45 minutes)

---

### Step 4.1: Create Comprehensive AWS vs GCP Comparison (25 minutes)

1. Compile Detailed Cost Comparison

Create a comprehensive comparison matrix in your spreadsheet:

| Service Component        | AWS SageMaker | GCP Vertex AI | Monthly Difference | Annual Difference | Notes                                |
|--------------------------|---------------|---------------|--------------------|-------------------|--------------------------------------|
| Training Compute         | $X,XXX        | $X,XXX        | ±$XXX              | ±$X,XXX           | Include GPU costs                    |
| Prediction Endpoints     | $X,XXX        | $X,XXX        | ±$XXX              | ±$X,XXX           | Auto-scaling comparison              |
| Development Environment  | $XXX          | $XXX          | ±$XX               | ±$XXX            | Notebook instances vs Workbench      |
| Storage Costs            | $XXX          | $XXX          | ±$XX               | ±$XXX            | S3 vs Cloud Storage                  |
| Data Transfer            | $XXX          | $XXX          | ±$XX               | ±$XXX            | Egress and inter-region              |
| Management Overhead      | $XXX          | $XXX          | ±$XX               | ±$XXX            | Operational costs                    |
| Support and SLA          | $XXX          | $XXX          | ±$XX               | ±$XXX            | Enterprise support levels            |
| **Total Monthly**        | $X,XXX        | $X,XXX        | ±$XXX              | ±$X,XXX           | Net difference                       |

2. Document Key Assumptions

- Usage patterns remain constant
- Similar performance requirements
- Equivalent SLA requirements

Identify cost variables:

- Factors that could increase costs
- Potential for additional savings
- Regional pricing differences

Note service capability differences:

- Features available in one platform but not the other
- Performance differences that might affect costs

---

### Step 4.2: Total Cost of Ownership (TCO) Analysis (20 minutes)

1. Expand Analysis Beyond Direct Cloud Costs

Create a comprehensive TCO analysis:

| Cost Category               | One-Time Costs | Ongoing Monthly Costs | Notes                                              |
|-----------------------------|----------------|-----------------------|----------------------------------------------------|
| Direct Cloud Costs          | –              | $X,XXX                | From comparison above                              |
| Migration Costs             | $X,XXX         | –                     | Data transfer, application modification            |
| Training and Certification  | $X,XXX         | –                     | Team upskilling                                    |
| Operational Changes         | $X,XXX         | $XXX                  | New tools and processes                            |
| Risk Mitigation             | $XXX           | $XXX                  | Security and compliance                            |
| Opportunity Costs           | $X,XXX         | –                     | Development delays                                 |
| **Total TCO**               | $X,XXX         | $X,XXX                | Complete picture                                   |

2. Calculate Break-Even Analysis

- Determine monthly savings: GCP monthly cost – AWS monthly cost
- Calculate break-even period: Total one-time costs ÷ Monthly savings
- Create scenarios:
  1. Best case (maximum savings)
  2. Realistic case (expected savings)
  3. Worst case (minimal savings)

---

## Section 5: Cost Monitoring and Governance Setup (30 minutes)

---

### Step 5.1: Mobile App Integration and Monitoring (15 minutes)

1. Google Cloud Console Mobile App Setup (2025 Feature)

- Download Google Cloud Console mobile app from app store
- Sign in with your Google Cloud credentials
- Navigate to billing information features
- Set up mobile notifications for budget alerts
- Test mobile access to cost estimates and billing reports

2. Advanced Monitoring Setup

- In Google Cloud Console, navigate to **Monitoring**
- Create custom dashboards for cost monitoring:
  1. Click **Dashboards** → **Create Dashboard**
  2. Name: `ML Workload Cost Monitoring`
  3. Add charts for cost-tracking metrics
  4. Configure time ranges and aggregation
- Save dashboard for regular monitoring

---

### Step 5.2: Establish Cost Governance Framework (15 minutes)

1. Create Cost Review Process Documentation

# Google Cloud ML Cost Management Process

## Daily Tasks (5 minutes)

- [ ] Check billing overview dashboard
- [ ] Review any budget alerts
- [ ] Validate no unexpected resource creation

## Weekly Tasks (30 minutes)

- [ ] Generate and review cost reports
- [ ] Analyze spending trends using Reports interface
- [ ] Update cost forecasts based on current usage
- [ ] Review and adjust budgets if necessary

## Monthly Tasks (2 hours)

- [ ] Complete budget reconciliation
- [ ] Implement identified cost optimizations
- [ ] Prepare stakeholder cost summary reports
- [ ] Update pricing calculator estimates based on actual usage
- [ ] Review and validate cost allocation across projects

## Contact Information

- FinOps Team: [Contact information]
- Cloud Operations: [Contact information]
- MLOPS Team Lead Strategist: [Contact information]
- Manager: [Contact information]
- Model Ops Director: [Contact information]
---

## Lab 1.2 Deliverables Checklist

- Google Cloud cost analysis report with projected ML costs
- Configured GCP budgets with appropriate alert thresholds
- Comprehensive cost comparison framework between AWS and GCP
- TCO analysis with break-even calculations
- Cost governance framework documentation
- Mobile monitoring setup for ongoing cost management

---

## 🎯 Workshop Success Validation

### Immediate Success Indicators

**Technical Competency Validation**

- Navigation Proficiency: can independently navigate both AWS and GCP billing consoles
- Data Analysis Skills: successfully extract and analyze cost data from both platforms
- Tool Configuration: properly configure budgets, alerts, and monitoring
- Export Capabilities: ability to export and save cost data for offline analysis

**Business Analysis Validation**

- Cost Baseline Established: documented current AWS ML spending with detailed breakdown
- Projection Accuracy: realistic GCP cost projections using pricing calculator
- Optimization Identification: specific, actionable cost optimization opportunities
- TCO Understanding: comprehensive understanding of total cost factors

**Process Implementation Validation**

- Monitoring Setup: working budget alerts and monitoring processes
- Documentation Quality: clear, actionable documentation and runbooks
- Governance Framework: appropriate cost review and approval processes
- Stakeholder Communication: clear articulation of findings and recommendations

---

## Key Achievements Summary

**Financial Foundation Established**

- ✅ AWS Cost Baseline: comprehensive understanding of current SageMaker spending patterns and optimization opportunities
- ✅ GCP Cost Projections: realistic estimates created using official Google Cloud pricing calculator
- ✅ Cost Comparison Framework: detailed AWS vs GCP comparison with total cost of ownership analysis
- ✅ Financial Governance: established cost monitoring, budgeting, and review processes

**Technical Competencies Developed**

- ✅ Console Mastery: proficient navigation of AWS and GCP billing consoles
- ✅ Cost Analysis Skills: ability to extract insights from billing data and identify trends
- ✅ Monitoring Configuration: working budget alerts and cost monitoring systems
- ✅ Data Export and Analysis: skills to export, analyze, and present cost data effectively

**Business Capabilities Enhanced**

- ✅ ROI Analysis: clear understanding of migration financial benefits and timeline
- ✅ Risk Assessment: identified and quantified financial risks and mitigation strategies
- ✅ Stakeholder Communication: ability to present compelling business case for migration
- ✅ Decision Support: framework for making informed, data-driven migration decisions

**Organizational Impact**

- ✅ Process Documentation: clear, actionable cost management procedures
- ✅ Knowledge Transfer: documented processes enable team knowledge sharing
- ✅ Continuous Improvement: framework for ongoing cost optimization and management
- ✅ Strategic Alignment: cost management integrated with broader migration strategy


---

# 📋 Google Cloud ML Cost Management Runbook

---

## 📋 Purpose and Scope

This runbook provides standardized operational procedures for managing Google Cloud costs for machine learning workloads, specifically designed for teams migrating from AWS SageMaker to Google Cloud Vertex AI. All procedures are console-based and require no programming knowledge.

---

## 🎯 Key Performance Indicators (KPIs)

- **Budget variance:** <10% monthly variance from planned spend
- **Cost optimization:** 5% quarterly cost reduction through optimization
- **Alert response time:** <2 hours for budget threshold alerts
- **Monthly reporting:** Complete cost analysis within 3 business days of month-end

---

## 📅 Daily Tasks (Console-Based)

**⏱️ Estimated Time: 15–20 minutes**

### Morning Cost Health Check (10 minutes)

**1. Billing Overview Dashboard Review**

- Navigate to **Billing Overview**
- Check current month spend vs. budget
- Review "Top spending services"
- Verify daily spend trend vs. historical patterns
**Action Required:** If spend exceeds 150%, trigger emergency procedures

**2. Budget Alert Status Check**

- Go to **Budgets & Alerts**
- Check budget alert status for all ML workloads
**Action Required:** Investigate if any budget exceeds 75% utilization mid-month

**3. Cloud Monitoring Dashboard Check**

- Access **Cloud Monitoring**
- Open "ML Workload Cost Monitoring" dashboard
- Review charts and anomalies
**Action Required:** If cost deviates >20% from baseline, document and investigate

### Resource Validation Sweep (5–10 minutes)

**4. Vertex AI Resource Check**

- Navigate to **Vertex AI**
- Check for running training jobs or idle endpoints
- Confirm Workbench instances are stopped outside hours
**Action Required:** Stop unnecessary resources

**5. Compute Engine Instance Review**

- Navigate to **Compute Engine**
- Scan for unauthorized/idle VMs
**Action Required:** Document and escalate as needed

---

### ✅ Daily Checklist Completion Log:

- **Date:** ___________
- **Daily Budget Status:** ✓ On Track / ⚠️ Warning / 🚨 Alert
- **Unexpected Resources Found:** Yes / No
- **Issues Requiring Follow-up:** ___________
- **Completed by:** ___________

---

## 📊 Weekly Tasks (Analysis and Planning)

**⏱️ Estimated Time: 45–60 minutes**

### Monday: Weekly Cost Analysis (30 minutes)

1. Generate Detailed Cost Reports
   - Cost Reports → Time Range: “Last 7 days”
   - Group by Service & Project
   - Export to CSV
   **Deliverable:** Weekly trend analysis spreadsheet

2. Service-Level Deep Dive
   - Filter for Vertex AI
   - Analyze training vs. prediction, Storage, Compute
   **Deliverable:** Optimization recommendations

3. Usage Pattern Analysis
   - Set to Daily granularity
   - Compare weekend vs. weekday usage
   - Identify off-peak scheduling opportunities
   **Deliverable:** Usage optimization schedule

### Friday: Planning and Forecasting (30 minutes)

4. Budget Performance Review
   - Budgets & Alerts → Compare usage to thresholds
   **Action Required:** Adjust budgets if needed

5. Forecast Validation and Updates
   - Pricing Calculator → Update saved estimates
   **Deliverable:** Updated cost forecast

---

### 🧾 Weekly Analysis Template

- **Week of:** ___________
- **Total Weekly Spend:** $___________
- **Variance:** ±___%
- **Top Cost Driver:** ___________
- **Key Optimization:** ___________
- **Next Week Forecast:** $___________
- **Red Flags:** ___________
- **Analyst:** ___________

---

## 📈 Monthly Tasks (Governance and Reporting)

**⏱️ Estimated Time: 2–3 hours**

### Month-End Analysis (Day 1–3)

1. Budget Reconciliation
   - Compare actual vs. budgeted for ML services
   **Deliverable:** Budget variance report

2. Implement Cost Optimizations
   - Right-size, clean up unused resources
   **Deliverable:** Optimization log

3. Stakeholder Reporting
   - Executive summary + trend charts + ROI update
   **Deliverable:** Leadership report

### Mid-Month Strategic Review (Day 15)

4. Cross-Platform Cost Comparison
   - Update AWS vs. GCP matrix
   **Deliverable:** Cost-benefit analysis

5. Project Cost Allocation Review
   - Group by Project
   - Validate labeling & cost centers
   **Deliverable:** Allocation accuracy report

---

### 📊 Monthly Report Template

- **Month:** ___________
- **Spend:** $___________
- **Variance:** ±___%
- **Top Cost Area:** ___________
- **Savings Achieved:** $___________
- **ROI Status:** On Track / Behind / Ahead
- **Recommendations:** ___________
- **Prepared by:** ___________
- **Approved by:** ___________
- **Distribution:** Finance, IT, ML Teams

---

## 📋 Quarterly Tasks (Strategic Review)

**⏱️ Estimated Time: 4–6 hours**

### 1. TCO Update (2 hours)

- Use 3-month cost data
- Update actual vs. projected TCO
- Recalculate migration ROI
**Deliverable:** Updated 3-Year TCO Model

### 2. Service Optimization Review (2 hours)

- Identify under-utilized resources
- Review and optimize scaling policies
**Deliverable:** Optimization roadmap

### 3. Long-Term Planning (1–2 hours)

- Forecast seasonal/project needs
- Update estimates for new initiatives
**Deliverable:** Next quarter budget

---

### 📝 Quarterly Review Checklist

- **Quarter:** Q___ 20___
- **Variance:** ±___%
- **Migration Savings:** $___________
- **Top Opportunities:**
  1. ___________
  2. ___________
  3. ___________
- **Impact Assessment:** ___________
- **Recommendations:** ___________
- **Committee:** ___________

---

## 🚨 Emergency Procedures

---

### Budget Overage Response Protocol

#### Immediate Actions (Within 1 hour)

**1. Access Billing Console**

- Navigate to **Billing Overview**
- Identify specific services causing overage
- Document exact overage amount and timeframe

**2. Resource Usage Investigation**

- Check **Vertex AI** for unexpected training jobs
- Review **Compute Engine** for unauthorized instances
- Examine **Cloud Storage** for data transfer spikes

**3. Immediate Cost Controls**

- Stop non-critical training jobs
- Scale down over-provisioned prediction endpoints
- Implement temporary spending limits if available

---

#### Follow-up Actions (Within 4 hours)

**4. Stakeholder Notification**

- Email finance team with initial findings
- Notify ML team leads of service disruptions
- Escalate to management if overage >25% of monthly budget

**5. Root Cause Analysis**

- Use **Cost Reports** to identify the source
- Check recent changes or deployments
- Document the timeline of contributing events

**6. Prevention Planning**

- Update budget thresholds
- Implement additional monitoring alerts
- Plan process improvements

---

### Unexpected Cost Spike Investigation

#### Investigation Workflow

**1. Time-Based Analysis**

- Set Cost Reports granularity to **Hourly**
- Identify cost spike window
- Correlate with recent deployments or updates

**2. Service Identification**

- Filter reports by **Service**
- Investigate unusual usage or anomalies
- Review supporting services for cascading costs

**3. Resource Correlation**

- Cross-reference with **Cloud Monitoring** metrics
- Identify resource scaling events or deviations
- Verify performance or configuration changes

**4. Mitigation Implementation**

- Apply immediate controls
- Enable targeted alerts
- Document the incident

---

### Emergency Contact Escalation Matrix

| Alert Level                             | Escalation Path                                                  |
|-----------------------------------------|-------------------------------------------------------------------|
| >10% monthly budget variance            | ML Team Lead → Finance Business Partner                           |
| >25% monthly budget variance            | IT Ops Manager → Finance Manager → Program Director               |
| >50% monthly budget variance            | Finance Director → IT Director → Executive Leadership             |
| >100% budget breach (Critical)          | Full escalation + External vendor support                         |

---

## 📞 Key Contacts and Resources

### Team Contacts

- **Finance Team:** finance-ml@sysco.com |
- **Cloud Operations:** cloudops@sysco.com |
- **Lead MLOPS Strategist:** david.santana@sysco.com |
- **Escalation Manager:** cost-escalation@sysco.com |

### Emergency Contacts (24/7)

- **IT Operations Center:** (555) 999-0000
- **Finance Emergency Line:** (555) 999-0001
- **Executive On-Call:** (555) 999-0002

### External Support

- **Google Cloud Support:** Support Case Portal
- **Account Manager:** [From Google Cloud Console]
- **TAM:** [If applicable]

---

## 🔗 Quick Access Console URLs

### Daily Operations

- [Billing Overview](https://console.cloud.google.com/billing)
- [Budgets & Alerts](https://console.cloud.google.com/billing/budgets)
- [Cloud Monitoring](https://console.cloud.google.com/monitoring)
- [Vertex AI Console](https://console.cloud.google.com/vertex-ai)

### Analysis and Reporting

- [Cost Reports](https://console.cloud.google.com/billing/reports)
- [Pricing Calculator](https://cloud.google.com/products/calculator)
- [Resource Manager](https://console.cloud.google.com/cloud-resource-manager)

### Service Management

- [Compute Engine](https://console.cloud.google.com/compute/instances)
- [Cloud Storage](https://console.cloud.google.com/storage)
- [IAM & Admin](https://console.cloud.google.com/iam-admin)

---

## 📋 Documentation and Change Log

**Runbook Maintenance**

- **Last Updated:** [Date]
- **Version:** 1.0
- **Next Review Date:** [Quarterly]
- **Owner:** [Cost Management Team]

**Change History**

| Date     | Version | Changes                 | Approved By |
|----------|---------|--------------------------|--------------|
| [Date]   | 1.0     | Initial runbook creation | [Name]       |

### Training and Certification

- **Required Training:** Google Cloud Cost Management Fundamentals
- **Certification Renewal:** Annual
- **Training Records:** Maintained in [System/Location]

---

## 📌 Quick Reference Card

**Print and keep at desk for emergencies**

### EMERGENCY COST SPIKE RESPONSE

1. Open Billing Overview → Identify spike
2. Review recent resource usage
3. Stop non-critical services
4. Email finance team findings
5. Escalate if >25% budget variance

### DAILY HEALTH CHECK (15 min)

- ✓ Billing overview dashboard
- ✓ Budget alerts status
- ✓ Monitoring dashboard
- ✓ Resource scan
- ✓ Issue documentation

**KEY CONTACTS**

- **Finance:** (555) 123-4567
- **CloudOps:** (555) 234-5678
- **Emergency:** (555) 999-0000

---

## Final Reminder

The financial discipline and analytical skills you've developed in this module will be essential throughout your cloud migration. Continue reviewing, optimizing, and aligning costs with strategic goals.

---

## 🎯 Workshop Module 1 Complete!

Congratulations! You’ve built a robust financial foundation for your AWS → GCP ML migration. The budgeting, tracking, and governance systems you’ve implemented will drive success in future modules.

---

## 📄 License

This workshop content is provided under the **MIT License**. See the LICENSE file for details.

---

## 🤝 Contributing

Contributions are welcome! Please review the contributing guidelines before submitting pull requests.

---

## 📞 Support

For help with this workshop:

- Create an issue in the repository
- Contact the workshop maintainers
- Review the troubleshooting section above

---

© 2025 - 2026 **ML Migration Workshop Series**
