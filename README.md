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

# 
