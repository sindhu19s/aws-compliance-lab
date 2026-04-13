# AWS Compliance Lab	
## What I am building	
An end-to-end cloud governance lab using AWS S3,	
IAM, and Macie to govern loan application data.	

## Why it matters	
Loan approval AI is classified as HIGH RISK	
under EU AI Act Article III. This lab shows	
how to govern the data that feeds such a system.	
	
## Tools	
- AWS S3 (storage + access control)	
- AWS IAM (identity + least privilege)	
- AWS Macie (automated PII detection)	
- AWS Access Analyzer (audit)	
	
## Dataset	
German Credit Data — UCI Machine Learning Repository	

## Step 1 : Create S3 bucket and add Loan file to it
<img width="1425" height="690" alt="Screenshot 2026-04-08 at 12 01 10 PM" src="https://github.com/user-attachments/assets/5679e474-2a5d-4a1b-a0a9-e11aa4933a9d" />

<img width="1417" height="634" alt="Screenshot 2026-04-08 at 12 10 25 PM" src="https://github.com/user-attachments/assets/26ae28ff-ce47-47ac-be51-0faf6fe019a6" />

## Step 3 : Create IAM user - Auditor-User

## Step 3 : Create add Read policy (AmazonS3ReadOnlyAccess) to this IAM user. 

## Final Result shows : 1 Severity 
<img width="1470" height="956" alt="Screenshot 2026-04-11 at 6 46 40 PM" src="https://github.com/user-attachments/assets/4154df62-bdc9-4873-8a8f-b99f832c0d2e" />

## More Details!!!

1. The "Auditor-User" (Identity Governance)
   - What I did: I created a person (Auditor-User) and gave them Zero Permissions first, then a Read-Only policy.
   - Why it's Governance: This is the principle of Least Privilege. Governance isn't just about "locking doors"; it’s about having a paper trail of who is allowed       to do what. By making an "Auditor" who can see but not touch, you are following a legal requirement for most financial companies.
2. The "Access Analyzer" (The Guard at the Door)
	- What I did: I turned on a tool that scanned my account to see if any "outsiders" could get in.
    - Why it's Governance: This is Automated Compliance. Instead of me manually checking every folder (bucket) every day, the Analyzer does it for me. It 			"Governs" the perimeter. If I accidentally make a folder public, the Analyzer would flag it as a "Finding."
    - The Goal: To prove to a regulator (like the EU or the SEC) that I have a system in place to prevent data leaks.
3. Amazon Macie (The X-Ray for the Money Bags)
   	- What I did: I started a tool that actually "reads" the inside of your CSV files.
   	- Why it's Governance: This is Data Classification.Security is locking the safe.Governance is knowing exactly how many $100 bills and how many $1 bills are          inside the safe.
   	- Macie tells me: "Hey, this file contains Social Security Numbers (PII)." Once I know that, I am legally required to handle that file differently.
