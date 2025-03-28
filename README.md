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

![AWS Pipeline Architecture by Draw.io] ![Picture1](https://github.com/user-attachments/assets/01d0f0bd-4e3f-4abc-86be-bab9a6edd863)


### 1. Data Ingestion Process
**Implementation Details:**
- Created dedicated S3 buckets with lifecycle policies:
  - `prj-raw-sk` (Raw data zone)
  - `prj-trf-sk` (Transformed data zone)
- Implemented bucket versioning and cross-region replication
- Set up S3 event notifications to trigger downstream processes![Picture1](https://github.com/user-attachments/assets/8747fb5d-b9c1-49fc-aa83-874c21f8bf0a)
![Picture5](https://github.com/user-attachments/assets/38cd5ff9-76b9-4343-ac56-6896e23eeafe)


**Technical Specifications:**
s3://prj-raw-sk/
└── cultural-sk/
    ├── cultural-spaces(2).csv
    ├── metadata.json
    └── ingest_logs/
## 2. Data Profiling & Quality Assessment

### Glue DataBrew Implementation
Implemented comprehensive data quality checks through:
![Picture6](https://github.com/user-attachments/assets/dc8247a3-a548-4cc0-ab93-73a5c32695ee)
![Picture9](https://github.com/user-attachments/assets/f9762b95-032e-4a61-a5ac-12b637ead6a4)
![Picture10](https://github.com/user-attachments/assets/2e06882c-c550-4318-971b-7623bb889765)

- **Three-tier profiling strategy**:

  graph TD
    A[Full Dataset Profile] --> B[Identify global patterns]
    C[Stratified by LOCAL_AREA] --> D[Neighborhood-specific insights]
    E[Random Sample] --> F[Quality rule validation]

2. **Enhanced Data Cleaning Section**:

## 3. Data Cleaning & Transformation

### Workflow Architecture

flowchart LR
    A[Raw CSV] --> B(DataBrew Cleaning)
    B --> C{Validation}
    C -->|Pass| D[JSON Output]
    C -->|Fail| E[Error Logging]
    D --> F[Glue Catalog]
![Picture7](https://github.com/user-attachments/assets/d8d9df41-de61-4517-9143-ee0f99eebfb7)
![Picture12](https://github.com/user-attachments/assets/6aad2ea0-cd2d-427d-87d8-b9222c931597)

3. **Pro Tip**: Add visual badges to showcase your tech stack:

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

4. **AWS Cost Estimation**:
   ![Picture14](https://github.com/user-attachments/assets/cfb58a28-a284-4383-be08-73951bd9ad26)
![Picture16](https://github.com/user-attachments/assets/ca91bf4f-a128-437e-972f-2d2643c343f2)

5. **Draw.Io Charts**:

   ![Picture2](https://github.com/user-attachments/assets/b88d2391-28db-406e-9c50-a0f0101d7588)
![Picture3](https://github.com/user-attachments/assets/63d95432-27b1-4b67-a3aa-c6ee16b09386)
![Picture4](https://github.com/user-attachments/assets/f35fa0d6-8e8c-4bdb-8651-3952d2b32133)
![Picture8](https://github.com/user-attachments/assets/e8de4e8f-9588-4344-9669-ef90690da7ed)
![Picture11](https://github.com/user-attachments/assets/1b115317-fcab-4dd7-9f45-694c4a45db1c)
![Picture17](https://github.com/user-attachments/assets/d285a506-ccfe-4b02-831b-9fbe46435b2e)
![Picture18](https://github.com/user-attachments/assets/c925c1ad-b497-4cdb-a025-7b8ee467b34a)

6. **Other Images**:

   ![Picture13](https://github.com/user-attachments/assets/7e890da2-e854-4a93-a93a-4b998161ea12)
![Picture15](https://github.com/user-attachments/assets/f466c07f-7100-413d-817a-15e184616495)
![Picture19](https://github.com/user-attachments/assets/79975ddc-3e2a-45bf-b3f4-8bb43700d390)
![Picture20](https://github.com/user-attachments/assets/661095fc-ecb5-41a1-a89c-d55785d7cff5)



