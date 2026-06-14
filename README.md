# AWS Cross-Account Secure File Processing Pipeline

## Project Overview

This project demonstrates a secure event-driven file processing solution using AWS services. The solution enables a user from one AWS account to upload files into an encrypted Amazon S3 bucket hosted in another AWS account. File uploads automatically trigger AWS Lambda, generate CloudWatch logs, and send email notifications through Amazon SNS.

## Architecture

<img width="1130" height="756" alt="image" src="https://github.com/user-attachments/assets/2052c1c4-01c3-44d0-adb7-085271746a19" />




## AWS Services Used

* Amazon S3
* AWS Lambda
* AWS IAM
* AWS KMS
* Amazon SNS
* Amazon CloudWatch

## Key Features

* Cross-account S3 file uploads
* KMS-based encryption
* Event-driven Lambda execution
* CloudWatch monitoring and logging
* SNS email notifications
* IAM and resource-based access control

## Workflow
Step 1: User Uploads File from Account A
* An IAM user  from Account A uploads a file to the S3 bucket hosted in Account B. Cross-account access is enabled through S3 Bucket Policy and KMS Key Policy.


Step 2: File Stored in KMS-Encrypted S3 Bucket
* The uploaded object is stored in the S3 bucket <bucket_name> using Server-Side Encryption with AWS KMS (SSE-KMS). The KMS key ensures data is encrypted at rest.

S3 Bucket
↓
SSE-KMS Encryption
↓
Encrypted Object Stored


Step 3: S3 Event Notification Detects Upload
* S3 continuously monitors object events. When a new object is created, the configured Event Notification (ObjectCreated) is triggered.

ObjectCreated Event
↓
S3 Event Notification


Step 4: Lambda Function is Invoked
The S3 event payload is automatically sent to the Lambda function. No manual execution is required.

Lambda receives metadata such as:
Bucket Name
Object Name
Event Time
Event Type


Step 5: Lambda Processes Event Data
The Lambda function extracts required information from the event payload using Python.

Operations performed:
Read S3 event JSON
Extract bucket name
Extract object name
Generate custom notification message


Step 6: Lambda Writes Logs to CloudWatch
The Lambda function records execution details in Amazon CloudWatch Logs for monitoring and troubleshooting.

Logged Information:
Lambda execution status
Bucket name
Uploaded file name
Error messages (if any)


Step 7: Lambda Publishes Notification to SNS
Using the SNS Publish API, Lambda sends a message to the SNS Topic.

The notification contains:
Bucket Name
File Name
Upload Status
Timestamp

Lambda
 ↓
sns.publish()
 ↓
SNS Topic


Step 8: SNS Sends Email Alert
Amazon SNS forwards the notification to all confirmed subscribers.


### Skills Demonstrated

* AWS IAM
* Amazon S3
* AWS Lambda
* AWS KMS
* Amazon SNS
* Amazon CloudWatch
* Python
* Cross-Account Access Management
* AWS Troubleshooting



