# My-Portfolio

Data Analytic Platform for the City of Vancouver:

The pictures below show the DAP design for the City of Vancouver property tax department.

![image](https://github.com/user-attachments/assets/e2ff7874-56f8-419a-9495-5984d2b23bb6)
Figure: shows the DAP for the City of Vancouver, source: self

Components and their significance:

•	AWS Athena: Interactive query service for analyzing data using standard SQL directly from S3.

•	Storage cost: Monitoring storage usage and estimating costs

•	Data event count: Track data events and usage metrics

•	Replication A, B, C: Data is replicated across different locations for redundancy.

•	AWS key management service (KWS): Manages encryption keys for secure data storage

•	Key: represents encryption keys used for data protection.

Step 5: Data Analysis

I want to analyze the parameters below from the City of Vancouver, Property Tax, and Land data using Amazon Athena.

![image](https://github.com/user-attachments/assets/f57728df-05ec-485d-a637-8fa9c76d8e01) 

Figure: Maximum Previous_Land_Value parameter, source: self

Below is the query used to achieve the above assumption:

![image](https://github.com/user-attachments/assets/27d41424-3adb-4b3c-b7c1-7a47407708de)

Figure: Shows the SQL query used, source: self

The output successfully executes the visualization in Figure (1).

![image](https://github.com/user-attachments/assets/fc420bad-8a18-48e2-a04e-37f410fddd5a) 

Figure: shows the output of the SQL query in Amazon Athena, source: self

Step 6: Data Security

Data protection is mandatory for the City of Vancouver's Property Tax system to protect personal and financial information. Data protection complies with laws like PIPEDA and FIPPA, protects against unauthorized usage, and guards against cyber attacks. 

(i)	So, we have implemented key services for the City of Vancouver to add a layer of protection. In AWS, a key enhances security, access control, and encryption. Here we have used a Key Management Services (KMS) key to encrypt data. 

The screenshot below shows that a key named “cov-pro-tax-key-sir” has been created using Amazon Key management services.

![image](https://github.com/user-attachments/assets/a1b3ecf9-0723-4e55-8921-a03eb5df95cf) 

Figure: Key generated for all the buckets as a part of data protection, source: self

(ii)	Enabling Default encryption: By default, this setting is disabled in AWS, meaning AWS uses its own key for encryption and decryption. Now that we have our own key, we must update this by navigating to our buckets and changing the ‘Default Encryption’ settings.

The following screenshots show that the keys are successfully implemented to the buckets.

![image](https://github.com/user-attachments/assets/f2aae86f-5b05-4ff0-8d39-4813110ec768)

Figure: key encrypted for raw bucket, source: self

![image](https://github.com/user-attachments/assets/156bda45-4fdf-418e-a881-3be96b0d02e4)

Figure: key encrypted for transform bucket, source: self

![image](https://github.com/user-attachments/assets/e508dcf7-b5c8-4071-a97b-39a8292c7d75) 

Figure: key encrypted for curated bucket, source: self

(iii)	Bucket Versioning: AWS S3 bucket versioning keeps multiple versions of an object to prevent accidental deletion or overwrites. It is crucial to data recovery and compliance when storing every change. This ensures business continuity, protects against human errors, and enables easy rollback to previous versions, making data management more reliable and secure.

The screenshots below show that the bucket versioning has been enabled for all the buckets in our Data Analytics Platform (DAP).

![image](https://github.com/user-attachments/assets/51757ad0-6b85-41ee-9642-849fb9d6f854)

Figure: Shows that the bucket versioning is enabled for raw bucket, source: self

![image](https://github.com/user-attachments/assets/8af1ce4b-d9d2-4b11-94f9-07f40ca7c789)

Figure: Shows that the bucket versioning is enabled for the transformed bucket, source: self

![image](https://github.com/user-attachments/assets/72b21e1b-2ccc-45ed-a1f8-eac83f3d1505)

Figure: Shows that the bucket versioning is enabled for the curated bucket, source: self

(iv)	AWS replication offers high availability, disaster recovery, and performance optimization across regions and services. It helps to avoid data loss and allows users to access copies faster. The replication process has been done to raw, curated, and transformed buckets to increase environmental availability protection by creating backup buckets and applying steps (i),(ii), and (iii) to them.

The screenshots below show that the replication process was successfully implemented for all the S3 buckets in the DAP.

![image](https://github.com/user-attachments/assets/7d20fb79-3e86-4965-bfa2-3fa4bb76db05)

Figure: Replication configuration successfully updated for the raw bucket, source: self

![image](https://github.com/user-attachments/assets/bb59615f-646e-4f9d-8c55-20829aee59f9)

Figure: Replication configuration successfully updated for the transformed bucket, source: self

![image](https://github.com/user-attachments/assets/98e0e1f2-4c63-4236-8daa-9a28cbc08914)

Figure: Replication configuration successfully updated for the curated bucket, source: self

Step 7: Data Governance

Data governance means keeping the data accurate, well-organized, and secure. Good data governance allows the City of Vancouver to make better decisions, avoid errors, and keep details safe and organized for effective operations.

The picture below describes a Visual ETL job created using AWS glue for property tax data, in which I check for data freshness and uniqueness as prominent features. 

![image](https://github.com/user-attachments/assets/d6f3697d-4f40-48a7-930d-1912273bf5f9)

Figure: Data quality check Visual ETL, source: self

Then, the passed and failed quality check data were stored in a transformed S3 bucket.

![image](https://github.com/user-attachments/assets/4ba75fa3-a5b6-4a61-b5fb-7f9d745a5fdf)

Figure: shows the passed quality check record saved in S3 transformed bucket, source: self

![image](https://github.com/user-attachments/assets/7dfecb61-cc3a-44d6-9fdf-80e3098dd930)

Figure: shows the failed quality check record saved in S3 transformed bucket, source: self

Step 8: Data Monitoring

Data Monitoring helps the City of Vancouver maintain accurate, secure, and reliable property tax records. Things like dashboards provide real-time insights, while alarms quickly detect errors, security threats, etc. 

I have created a dashboard for S3 buckets, and the AWS glue job runs for real-time insights as below. Dashboards are very flexible and can be adjusted according to the frequency.

![image](https://github.com/user-attachments/assets/e5bd7c1c-6e17-4da5-8df6-d9681083e426)

Figure: Image showing dashboard in AWS for s3 and job runs in AWS glue, source: self

As a part of controlling, I have created an alarm for S3 bucket storage with a threshold limit as shown below, but I set the threshold to a minimum to check if the alarm status changes or not; it has changed to “in alarm”; hence, it is working.

![image](https://github.com/user-attachments/assets/3cc45899-9546-4239-b478-c15f24cd39ee) 

Figure: created an alarm for S3 storage with threshold, source: self

Lastly, to help the City of Vancouver log user activity, I created a trail using the AWS Cloud trial 

![image](https://github.com/user-attachments/assets/4b41f377-0d29-4651-a0fe-a7f74386635c)

Figure: Showing the trial created using AWS Cloud Trial, source: Self

DAP Architecture Analysis:

1.	Operational Excellence: The Operation Excellence Pillar in AWS is primarily about efficient operations, automation, monitoring, and continuous improvement. We have used this in both project part 1 and part 2.

•	In the data monitoring, we have used AWS CloudWatch, alarms, and CloudTrail to ensure real-time tracking. 

•	Aws Glue checks if the data is fresh and unique by keeping it accurate and high-quality

•	Cost efficiency is maintained by estimating AWS service costs, using AWS Glacier for long-term storage, and optimizing Glue DPUs. 

These implementations align strongly with operational excellence by improving system resilience and continuous improvement.

2.	Security: The security pillar in AWS focuses on protecting data, systems, and assets through risk assessment and mitigation strategies. Our project used this in various steps as below:

•	Data Encryption: AWS Key Management Services (KMS) encrypted data in all S3 buckets, ensuring secure storage and access control.

•	Data Protection: Bucket versioning was done for all the S3 buckets to prevent data loss.

•	Replication & Backup: Backup buckets have been created and replicated with the original bucket’s data, thus by improving disaster recovery.
