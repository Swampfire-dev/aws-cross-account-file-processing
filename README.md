# AWS Cross-Account Secure File Processing Pipeline

## Project Overview

This project demonstrates a secure event-driven file processing solution using AWS services. The solution enables a user from one AWS account to upload files into an encrypted Amazon S3 bucket hosted in another AWS account. File uploads automatically trigger AWS Lambda, generate CloudWatch logs, and send email notifications through Amazon SNS.

## Architecture

Account A (IAM User)
↓
Cross-Account Upload
↓
Amazon S3 (SSE-KMS Encrypted)
↓
S3 Event Notification
↓
AWS Lambda (Python)
↙          ↘
CloudWatch      Amazon SNS
Logs             ↓
Email Alert

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

1. User uploads a file from Account A.
2. File is stored in a KMS-encrypted S3 bucket in Account B.
3. S3 Event Notification triggers Lambda.
4. Lambda extracts bucket and file information.
5. Lambda writes logs to CloudWatch.
6. Lambda publishes a notification to SNS.
7. SNS sends an email alert.


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

## Future Improvements

* Process files and move them to a processed bucket
* Infrastructure provisioning using Terraform
* CloudWatch Alarms and Monitoring
* Dead Letter Queue (DLQ) implementation

