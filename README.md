# HIPAA Compliance Cloud Infrastructure using AWS
This project is an AWS CloudFormation template for HIPAA Compliance Auditing and Logging in Cloud Infrastructure.

# How to use it
Refer to [AWS Create the Stack guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.Walkthrough.html#GettingStarted.Walkthrough.createstack)

# Description of the template

The template is an AWS architecture for a small, made-up grocery store named GoodBuy which has pharmacy in its store to fill prescriptions for patients. The pharmacies have a pharmacy management system that keeps track of all prescriptions and patient information. GoodBuy is planning to migrate the server in each store to the AWS cloud.  Since this is a pharmacy all HIPAA regulations must be followed to secure patient data.

# HIPAA Compliance requirements
HIPAA Requirement (45 CFR 164.312 -Technical safeguards)  
▶ (a) (1) Standard: “...allow access only to those persons or software programs that have been granted access rights ...”.  
▶ (a) (2) Implementation specifications:  
  (i) Unique user identification (Required).  
  (ii) Emergency access procedure (Required).  
  (iii) Automatic logoff (Addressable).  
  (iv) Encryption and decryption (Addressable).  
▶ (b) Standard: Audit controls.  
▶ (c) (1) Standard: Integrity. protect PHI from improper alteration or destruction.  
▶ (c) (2) Implementation specification: Mechanism to authenticate electronic protected health information (Addressable).  
▶ (d) Standard: Person or entity authentication.  

# Cloud Solution Architecture
## Security Use cases.
Logging and Event management is a key security aspect and requirement for all the GoodBuy location/operations. The GoodBuy site’s actions and event triggering have been implemented through the use of AWS Cloud Trail and Cloud Watch. 

![alt text](https://raw.githubusercontent.com/shaza4061/aws-hipaa-example/master/img/img1.png)

The following use cases/checkpoint have been implemented to capture how a user will interact with the system:

*	Events/Rules be monitored
*	DataPipeline - Data movement throughout the network
*	EC2_StatusChange - Site and EC2 Instance Change Notification
*	IAM - All Identity Management Changes usage.
*	KMS - All Key Management usage.
*	S3_Read_Writes - All write and changes made to all S3 Bucket Events
*	Storage Gateway - AWS API Call via CloudTrail
 
 Here is the diagram of the how the event are processed using CloudTrail and a User’s actions.

![alt text](https://raw.githubusercontent.com/shaza4061/aws-hipaa-example/master/img/img2.png)

CloudTrail generates a log entry for every API call made our account. CloudTrail aggregates the log entries in JSON text files, zips the files, and copies them to the Amazon S3 bucket configured to receive CloudTrail log files.

*	 The log parsing logic is deployed as a Lambda function. The Lambda function is triggered when CloudTrail copies a new file to your S3 bucket.
*	The Lambda function uses a configuration file that contains a list of specific API keywords that, when detected, will trigger a notification. The configuration file is stored in an S3 bucket.
*	Whenever relevant keywords are detected in the CloudTrail logs, the Lambda function posts a notification to an SNS topic.
*	SNS dispatches the notification to every topic subscriber via email, Amazon SQS, SMS, HTTP call, or mobile push.
 
We then take these SNS Alerts and monitor them in CloudWatch. CloudWatch allows us to monitor AWS cloud resources and the applications we or a user is running on AWS. We can use CloudWatch to collect and track metrics, collect and monitor log files, set alarms, and giving the ability to automatically react to changes in your AWS resources.

## Cloud Security Architecture and Network Topology

![alt text](https://raw.githubusercontent.com/shaza4061/aws-hipaa-example/master/img/img3.png)
