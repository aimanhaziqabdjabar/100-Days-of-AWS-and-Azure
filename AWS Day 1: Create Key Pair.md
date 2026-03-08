# 📌 Project Overview

As part of the **Nautilus DevOps Team's cloud adoption strategy**, this project represents the **first foundational phase** of migrating infrastructure to the **AWS Cloud**.

To minimize operational risk and service disruption, the migration process is executed in **structured and manageable phases**.

**Phase 1 focuses on establishing secure authentication mechanisms** to enable safe access to AWS compute resources, specifically **EC2 instances**.

This is achieved by generating a **secure RSA key pair** used for **SSH authentication**.

---

# 🎯 Objective

The objective of this phase is to create a **secure RSA key pair** that will allow engineers to securely connect to EC2 instances using **SSH key-based authentication** instead of passwords.

<img width="1326" height="886" alt="Screenshot 2026-02-22 235734" src="https://github.com/user-attachments/assets/5be5fdbd-801a-4f7a-9b39-f7f7dd32778e" />

---

# 🔑 Key Pair Specifications

| Parameter | Value |
|----------|------|
| Key Pair Name | `devops-kp` |
| Key Type | `RSA` |
| File Format | `.pem (OpenSSH)` |
| Usage | SSH access to EC2 instances |

---

# 🛠️ Implementation

Two methods were used to create the key pair:

1. **AWS Management Console**
2. **AWS CLI**

---

# Method 1: AWS Management Console

### Step 1 – Navigate to EC2 Dashboard
AWS Console → EC2 → Network & Security → Key Pairs
<img width="1369" height="838" alt="Screenshot 2026-02-22 235817" src="https://github.com/user-attachments/assets/aaa616b4-8bc1-4741-b756-3a570a866a47" />

<img width="1398" height="747" alt="Screenshot 2026-02-22 235909" src="https://github.com/user-attachments/assets/cf224cb6-7292-4b37-b401-784c1f0cf7be" />

---

### Step 2 – Create Key Pair

Click **Create Key Pair**
<img width="1407" height="797" alt="Screenshot 2026-02-22 235948" src="https://github.com/user-attachments/assets/dbaf7574-d3cb-4b3e-aedc-5d06a4c737da" />

---

### Step 3 – Configure Key Pair

Use the following configuration:

| Setting | Value |
|-------|------|
| Name | `devops-kp` |
| Key Type | RSA |
| File Format | `.pem` |

<img width="1012" height="835" alt="Screenshot 2026-02-23 000125" src="https://github.com/user-attachments/assets/1e364ff5-41f4-4b28-b8e1-3e8c0340994a" />

---

### Step 4 – Download Private Key

Download the generated **private key** and store it securely on your local machine.

⚠️ **Important:**  
This file can only be downloaded once. Losing it will require generating a new key pair.

<img width="1673" height="915" alt="Screenshot 2026-02-23 000149" src="https://github.com/user-attachments/assets/84168a25-a695-4ab4-a100-4ede63aed686" />

---

# 💻 Method 2: AWS CLI

For **automation and infrastructure consistency**, the key pair can also be created using the **AWS CLI**.

---

## AWS CLI Command

```bash
aws ec2 create-key-pair \
    --key-name devops-kp \
    --key-type rsa \
    --query 'KeyMaterial' \
    --output text > devops-kp.pem

What this command does?

1. Creates a new key pair in AWS
2. Retrieves the private key material
3. Saves the key locally as:

**devops-kp.pem**

----
**🔐 Secure the Private Key**

To ensure proper security, restrict the file permissions so only the owner can read it.

chmod 400 devops-kp.pem

This prevents unauthorized users from accessing the private key.

