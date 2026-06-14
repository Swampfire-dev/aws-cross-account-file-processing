# Troubleshooting Guide

## Issue 1: KMS Access Denied

Error:

kms:GenerateDataKey AccessDenied

Root Cause:

Cross-account IAM user was not authorized to use the KMS key.

Resolution:

Updated KMS Key Policy and added required permissions for external account access.

---

## Issue 2: S3 PutObject Access Denied

Error:

PutObject AccessDenied

Root Cause:

Bucket Policy did not allow uploads from external AWS account.

Resolution:

Configured cross-account S3 Bucket Policy.

---

## Issue 3: Lambda Not Triggering

Root Cause:

S3 Event Notification was not configured correctly.

Resolution:

Created ObjectCreated event notification and attached Lambda trigger.

---

## Issue 4: SNS Notification Not Received

Root Cause:

Lambda function lacked SNS publish permissions.

Resolution:

Attached SNS policy to Lambda execution role and implemented sns.publish().

---

## Issue 5: Understanding Event Payload

Challenge:

Understanding how S3 passes bucket and file information to Lambda.

Resolution:

Analyzed S3 event JSON structure and extracted values using:

event['Records'][0]['s3']['bucket']['name']

event['Records'][0]['s3']['object']['key']




