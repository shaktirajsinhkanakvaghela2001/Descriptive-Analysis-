# Cloud Data Analytics Pipeline: Vancouver Cultural Spaces Analysis

## Project Overview
This project implements a comprehensive data analytics pipeline on AWS to analyze cultural spaces in Vancouver, with particular focus on identifying and characterizing privately-owned educational institutions. The solution leverages multiple AWS services to ingest, process, analyze, and visualize open data from the Vancouver Open Data Portal.

**Key Objectives:**
- Quantify the distribution of private educational institutions among cultural spaces
- Analyze spatial patterns and facility characteristics
- Establish a reusable data processing pipeline on AWS
- Implement cost-effective cloud-native analytics solution

## Dataset Description
The cultural dataset contains:
- **12 key attributes**: YEAR, CULTURAL_SPACE_NAME, WEBSITE, TYPE, PRIMARY_USE, ADDRESS, LOCAL_AREA, OWNERSHIP, SQUARE_FEET, NUMBER_OF_SEATS, ACTIVE_SPACE, Geomgeo_point_2d
- **Time period**: 2010-2023 (updated quarterly)
- **Data volume**: ~2,500 records (45MB uncompressed)

## AWS Implementation Architecture

![AWS Pipeline Architecture](media/pipeline_architecture.png)

### 1. Data Ingestion Process
**Implementation Details:**
- Created dedicated S3 buckets with lifecycle policies:
  - `prj-raw-sk` (Raw data zone)
  - `prj-trf-sk` (Transformed data zone)
- Implemented bucket versioning and cross-region replication
- Set up S3 event notifications to trigger downstream processes

**Technical Specifications:**
```bash
s3://prj-raw-sk/
└── cultural-sk/
    ├── cultural-spaces(2).csv
    ├── metadata.json
    └── ingest_logs/
## 2. Data Profiling & Quality Assessment

### Glue DataBrew Implementation
Implemented comprehensive data quality checks through:

- **Three-tier profiling strategy**:
  ```mermaid
  graph TD
    A[Full Dataset Profile] --> B[Identify global patterns]
    C[Stratified by LOCAL_AREA] --> D[Neighborhood-specific insights]
    E[Random Sample] --> F[Quality rule validation]

2. **Enhanced Data Cleaning Section**:
```markdown
## 3. Data Cleaning & Transformation

### Workflow Architecture
```mermaid
flowchart LR
    A[Raw CSV] --> B(DataBrew Cleaning)
    B --> C{Validation}
    C -->|Pass| D[JSON Output]
    C -->|Fail| E[Error Logging]
    D --> F[Glue Catalog]

3. **Pro Tip**: Add visual badges to showcase your tech stack:
```markdown
## Technical Specifications

**AWS Stack**:
![AWS Glue](https://img.shields.io/badge/AWS-Glue-orange?logo=amazonaws)
![S3](https://img.shields.io/badge/Storage-S3-blue?logo=amazonaws)
![Athena](https://img.shields.io/badge/Query-Athena-blueviolet?logo=amazonaws)

**Data Quality**:
![Great Expectations](https://img.shields.io/badge/Quality-Great_Expectations-green)
| Service       | Configuration          | Cost Optimization |
|--------------|-----------------------|-------------------|
| Glue DataBrew | 10 DPU profile jobs    | Spot instances    |
| S3           | Standard-IA storage   | Lifecycle rules   |
