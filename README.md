# C06-Cloud-Anomaly-Detection-02
C06-Cloud-Anomaly-Detection-02

## Instructions					
Every screenshot requested in this workbook is compulsory and carries 5 marks.
Each of (EC2, Dynamodb, Kinesis, and SNS) setup in Task 1 will carry 20 marks each.
In Task 2, S3 setup via Cloudformation will carry 20 marks. Also, complete codedeploy setup will also carry 20 marks.
In Task 3, complete Lambda setup via Cloudformation will carry 20 marks.
		
>Resource Clean Up				
Cloud is always pay per use model and all resources/services that we consume are chargeable. Cleaning up when you’ve completed your lab or project is always necessary. This is true whether you’re doing a lab or implementing a project at your workplace.
After completing the lab, make sure to delete each resource created in reverse chronological order.

## Anomaly Detection using CloudFormation and CodeDeploy 
### Introduction

The anomaly detection M03P01 where AWS services used were all provisioned manually by using the AWS console. In the mentioned Project, we have configured services such as Kinesis, SNS, EC2 instance creation, setting up lambda handler, setting up the kinesis trigger, pushing data in DynamoDB etc. Once the services are up and running and data is pushed, the deployed lambda handler will perform anomaly detection, and it will trigger the SNS notification and detected data will be pushed on DynamoDB.

As we are moving more and more towards task automation. It makes sense if we can automate the service setup used in Anomaly detection Project using CloudFormation and CloudDeploy. The idea here is to slowly and gradually automate all the tasks involved in the M03P01. That is why the basic dummy python script which pushes data over cloud will be provided. The lambda handler code that performs anomaly detection will also be provided as a file. The focus is on automated setup, no changes are expected to be made in the actual python code which is a simple functioning dummy example, except for SNS topic ARN.

>Expected Kinesis data stream name - m03p02_raw_data_stream
Expected Dynamodb anomaly table name - m03p02_anomaly_data
Expected SNS topic name - m03p02_anomaly_alerts

1.	Raw data (Python script):
    a. This file is named as dummy_temp_data.py will generate the random environment temperature data using the random library. 
    b. This python file will publish the data over Kinesis stream, from there data will be pulled by lambda service.
2.	Anomaly detection (Lambda Handler):
    a. This anomaly_detection.py python file is configured to perform the anomaly detection on the raw data. 
    b.	After anomaly detection, data (detected) will be pushed in DB and a notification will be generated using SNS arn. 

