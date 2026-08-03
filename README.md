AWS Cloud Security: Self-Healing Architecture

📌 Project Overview

In cloud environments, a single misconfiguration—such as an S3 bucket being accidentally made public—can lead to catastrophic data breaches. This project demonstrates a Serverless Auto-Remediation Pipeline built natively in AWS.

Instead of relying solely on alerts that a human must manually investigate, this architecture automatically detects the misconfiguration in near real-time, instantly revokes public access, and alerts the security team of the action taken.

🏗️ Architecture & Technologies Used

Amazon S3: The target resource (simulating a bucket containing sensitive data).

AWS CloudTrail: The audit trail that detects the API call modifying bucket permissions.

Amazon EventBridge: The rule engine that listens for the specific CloudTrail event and triggers the remediation.

AWS Lambda (Python/Boto3): The serverless "brain" that executes the Python script to forcefully revert the bucket to private.

Amazon SNS: The notification service that sends an immediate email alert detailing the incident and the automated response.

IAM (Identity and Access Management): Strict role-based access control to allow Lambda to modify S3 and publish to SNS.

🚀 Phase 1: Infrastructure Setup (The Target & Alarm)

Objective: Establish the secure baseline and the automated alerting mechanism.

Secure Storage Baseline: Provisioned an Amazon S3 bucket to act as the target resource. Enforced Block Public Access (BPA) at the bucket level to establish a secure, compliant storage baseline prior to emulation.

Automated SOC Alerting: Engineered an Amazon SNS (Simple Notification Service) topic (Security-Alerts). Configured and verified an email subscription to ensure the simulated Security Operations Center (SOC) receives real-time paging when an incident occurs.

Proof of Configuration:


Fig 1:![S3 bucket deployed with Block Public Access successfully enforced.](images/s3-baseline-private.png)
  

Fig 2: ![SNS Topic subscription confirmed for real-time SOC email alerting.
](images/sns-subscription-confirmed.png)
