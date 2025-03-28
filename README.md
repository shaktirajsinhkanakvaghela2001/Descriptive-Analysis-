# Cloud Data Analytics Pipeline: Vancouver Cultural Spaces Analysis by Shaktirajsinh Vaghela (2323871)

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


## DAP Design and Implementation
- The cultural dataset downloaded from the Vancouver Open data Portal, which have multiple columns namely “YEAR, CULTURAL_SPACE_NAME, WEBSITE, TYPE , PRIMARY_USE, ADDRESS, LOCAL_AREA, OWNERSHIP, SQUARE_FEET,     
  NUMBER_OF_SEATS, ACTIVE_SPACE, Geomgeo_point_2d” are having enough of data to analyze. The aim behind my analysis is to “Find the number of Privately Owned Educational Institute” which can be found by using 
  simple math equation (PRIMARY_USE(Educational Institute) / OWNERSHIP (Privately)) * 100. To find the analysis we used Amazon Web Services like S3, Glue, Glue data brew etc. 
- As shown in this diagram, I have stored the raw of cultural-spaces dataset in csv format downloaded from Vancouver open data portal in S3 Bucket in this URI “prj-raw-sk/cultural-sk/”. Then the Glue Data brew 
  service is used to prepare data in clean form, and is stored in trf bucket in this URI: 

**Clean data**:
- “/cultural-sk/cultural-cln-sk_04Mar2025_1741118801567/”
**Dataset**:
- “/cultural-sk/cultural-ds-sk_a163ddca935c222639863eef05acba291f65d18b39f91789147ee891a8653893.json” 
  The next service used is glue crawler and data-catalog made. The cleaned data going to be summarization in AWS Glue Visual ETL as shown in image. 

**Image 1: Cultural-dataset AWS services diagram**
 ![Picture1](https://github.com/user-attachments/assets/544aa177-d7e0-425a-8e71-3ac5007e018a)


**1st Step: Data Ingestion Process**
- In the very first step I have stored the csv file by using s3 bucket as I stored csv file namely "cultural-spaces(2).csv" in the folder namely "cultural-sk" of bucket namely "prj-raw-sk". 
- Here is successful URI: s3://prj-raw-sk/cultural-sk/cultural-spaces(2).csv.

*Why:*
- •	S3 provides scalable, secure, and durable storage for raw data.
- •	Keeping raw data in an organized folder structure helps in efficient data retrieval and processing.

**Image 2: Data Ingestion Process**
![Picture2](https://github.com/user-attachments/assets/1f327454-d21e-4bac-8d04-49ce73fa4499)

 

**2nd Step: Data Profiling Process**
- The second thing I did was Data Profiling by using the AWS: Glue Data Brew service. This service is used in order to clean and preparing the data. Also, we can use to find some missing values, invalid data 
  removal or replacing and so on.

**Image 3: created dataset in AWS: Glue data brew**
![Picture3](https://github.com/user-attachments/assets/cc1e025e-c9d2-4f04-943a-65226cd9f54b)

 
**Image 4: By using crawler, the profile job successfully ran**
 ![Picture4](https://github.com/user-attachments/assets/31ee54e8-b42a-4a7c-9d2a-5008888c4c50)


**3rd Step: Data Cleaning**
- In this step I did used this service to prepare the data and cleaning it, so I used it in order to find missing values, replacing data which are invalid and so on. As you can see in this image 6  that the 
  saved cleaned Data-set file in “trf” bucket in JSON format.

**Image 5: Project is created**
![Picture5](https://github.com/user-attachments/assets/87055149-144d-4ca1-bddc-184b38d1756d)

 
**Image 6: Project created so recipe job successfully ran**
 ![Picture6](https://github.com/user-attachments/assets/7155ef03-52dc-43d0-a337-04d3a6fa9888)


**Image 7: Bucket where cleaned data is saved**
![Picture7](https://github.com/user-attachments/assets/184d7297-61ff-4c0e-8d2d-3129cc6382d8)

 
**Image 8: Dataset Profile Overview**
 ![Picture8](https://github.com/user-attachments/assets/aa99ed9b-7f32-4cf1-ac8d-109946de0ff6)

**Image 9: Data Cleaning**
 ![Picture9](https://github.com/user-attachments/assets/1ea6690f-819b-4c0b-a39b-45700486f9c1)


**4th Step: Data Cataloging** 
- This service is used to easily discover, to access, and to understand the data within an organization. For this process I used Glue service called crawlers which automatically classify the data as well as it 
  scans the data which we stored in S3 bucket. It extracts metadata and store the info which are findable, organized and consistent.


**Image 10: AWS: Glue Crawlers**
![Picture10](https://github.com/user-attachments/assets/ac4e4b06-4d2d-41cb-93e0-fbdd656cc547)

**Image 11: Glue-Visual ETL**
![Picture11](https://github.com/user-attachments/assets/1d9e3424-f90d-49d1-b095-1f733cd1a79e)


**5th Step: Data Summarization**
- Data summarization means using the raw data to convert it to useful summary and insightful so, for this I used AWS Glue service visual ETL as this can clean and analyze the data to get the key metrics for 
  example, sum, avg, count, and many more. These types of multiple metrics can be helpful in data analytical tasks. 

**Image 12: Final SQL Query code to get Output**
 ![Picture12](https://github.com/user-attachments/assets/01c508d4-54ae-474d-b516-d2821d9de647)

**Image 13: Summarization Pipeline**  
![Picture13](https://github.com/user-attachments/assets/eb7027c7-7d38-4b02-bc5b-ad33ff56e834)

**Image 14: Final Output Data Result Table**
![Picture14](https://github.com/user-attachments/assets/df1d83f3-2dcc-4329-ad8b-54364acfd998)


**AWS Services Estimated Cost:**
- The AWS Pricing Calculator used to estimate the provided outlines which projected the costs for using the Amazon’s S3 and AWS Glue services. The total estimated monthly cost is 0.11USD, with no upfront costs, 
  resulting in a total of 0.11USD,withnoupfrontcosts,resultinginatotalof1.32 USD over 12 months.

- For Amazon S3, the estimate amount to use service includes 4 GB of Standard storage per month, comes with various request types and data processing activities. AWS Glue costs are based on the how much user use 
  the Data Processing Units (DPUs) for Apache Spark and Python Shell jobs, with 10 DPUs allocated for Spark jobs and 0.0625 DPUs for Python Shell jobs.

- This estimated cost doesn’t include the taxes, and all so actual cost may be differ than this one. It also depends on the usage patterns, and also some other factors like that. To measure the accurate amount, 
  its better to review it together with the usage and monitoring it.

**Image 15: AWS Estimated Cost**
![Picture15](https://github.com/user-attachments/assets/aa2eaa1a-6fd9-4891-8fa3-2aba5a3edc41)

**Image 16: AWS Estimated Cost**
![Picture16](https://github.com/user-attachments/assets/f30fe0fa-9129-42d5-ae89-2967074dcb30)

**Image 17: AWS Estimated Cost**
![Picture17](https://github.com/user-attachments/assets/99ac60d3-d493-48bf-ba9f-c4cfbfe3ef5e)

**Image 18: AWS Estimated Cost**
![Picture18](https://github.com/user-attachments/assets/53f5d742-3203-49aa-a8c9-21df631af257)



**Step 5: Data Analysis**
- Users can run simplified SQL queries within Amazon Athena to filter and sort cultural dataset information and generate data patterns through summarization. Saved output data from queries exists on S3 storage 
  platforms and users can create visual dashboards by using QuickSight. Amazon Athena provides users with a capability to count artifacts according to their nation of origin throughout date range analysis of 
  artifacts.

**Image 19: AWS Estimated Cost**
![Picture19](https://github.com/user-attachments/assets/0a562415-d805-4e0c-9fdc-583a47bc0427)

**Image 20: AWS Estimated Cost**
![Picture20](https://github.com/user-attachments/assets/418dfa10-549f-497f-9ef2-87f3712addad)

  
**Step 6: Data Security**
- AWS KMS encryption provides data protection because only authorized users have access to your information. Complete IAM policies need to be established to enforce access rights restrictions for reading and 
  writing and querying the dataset. The authorization controls function as security mechanisms to guard cultural information from unauthorized users.

**Step 7: Data Governance**
- THE MANAGEMENT OF YOUR DATA BY USERS SHOULD BE TRACED THROUGH AWS CLOUDTRAIL TO VIEW EVENTS WHEN USERS ACCESS YOUR DATA AND MODIFY YOUR INFORMATION AND THEIR TIME STAMPS. In order to establish better 
  organizational structure both Glue tables and S3 files require the addition of metadata tags including owner names and project identifiers.

**Step 8: Data Monitoring**
- CloudWatch provides two features to both check system performance and identify system errors. Enable data monitoring through alerts which will notify you about the failure of Athena queries together with 
  unusual S3 events and delayed Glue crawler operations. Users can detect upcoming problems through the quick dashboard before they turn into major issues.
 

