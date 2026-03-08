AWS Cloud Migration: Phase 1 - Key Management
📌 Project Overview
As part of the Nautilus DevOps team's strategy to migrate infrastructure to the AWS Cloud, this project focuses on the initial foundational steps. To ensure a smooth transition and minimize disruption, the migration is handled in granular, manageable phases.

Phase 1 involves establishing secure access to our cloud resources by creating dedicated authentication credentials.

🎯 Task Objective
Create a secure RSA key pair to be used for SSH access to EC2 instances within the new AWS environment.

Specifications:
Key Pair Name: devops-kp

Key Type: rsa

Format: .pem (OpenSSH)

🛠️ Implementation Steps
Method 1: AWS Management Console
Navigate to the EC2 Dashboard.

Under Network & Security, select Key Pairs.

Click Create key pair.

Entered the name devops-kp and selected RSA as the key type.

Downloaded the private key file safely for local storage.

Method 2: AWS CLI (Command Line Interface)
To automate the process and maintain consistency, the following AWS CLI command was executed:

Bash
aws ec2 create-key-pair \
    --key-name devops-kp \
    --key-type rsa \
    --query 'KeyMaterial' \
    --output text > devops-kp.pem
Note: After creation, file permissions were restricted to the owner for security:

Bash
chmod 400 devops-kp.pem
🛡️ Key Learnings
Identity & Access Management: Understanding the importance of key-based authentication over passwords.

Infrastructure as Code (IaC) Readiness: Preparing manual steps that can later be translated into automation scripts.

Risk Mitigation: Applying a phased approach to large-scale cloud migrations.
