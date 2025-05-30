# 🔐 AWS Access Control Overview

## Service Control Policies (SCPs)

- SCPs are **guardrails** that define the **maximum permissions** an AWS account or Organizational Unit (OU) can use.
- They **do not grant access**; they only **restrict**.
- SCPs apply to:
  - All IAM identities in the account (users, roles)
  - The root user as well

---

## IAM Policies (Users, Roles, Groups)

- **Grant permissions** to identities to call AWS service actions.
- Policies can be attached to:
  - Users
  - Groups
  - Roles

---

## 📦 Resource-Based Policies

These policies are attached to AWS resources directly and define **who can access them**.

**Examples:**
- S3 Bucket Policies
- SNS Topic Policies
- KMS Key Policies
- Lambda Resource Policies

---

## 🔲 Permission Boundaries

- IAM **Permission Boundaries** restrict what a user or role can do — even if their IAM policy allows more.
- Commonly used in **delegated IAM role creation** scenarios (e.g., developers creating roles within boundaries).

---

## ⏱️ Session Policies (STS)

- Temporary policies used when assuming roles via `sts:AssumeRole`.
- They **restrict permissions** for the **lifetime of the session** only.

---

## 🌐 VPC Endpoint Policies (PrivateLink)

- Control access to AWS services **over VPC endpoints**.
- Can restrict traffic based on:
  - Source VPC
  - IAM principal
  - Requested actions

---

## 🔍 Access Analyzer / Policy Validation

- Use **IAM Access Analyzer** to simulate and validate policy logic.
- Helps identify:
  - Overly permissive IAM/resource policies
  - Unused permissions
  - Cross-account or public access

| Type                  | Scope                       | Grants or Limits Access ? | Use Cases |
|-----------------------|-----------------------------|---------------------------|-----------|
| SCP                   | Org / Account Wide          | Limits Only               |           |
| IAM Policy            | Principal (User /Role )     | Grants                    |           |
| Resource Based Policy | Resource Itself             | Grants                    |           |
| Permission Boundary   | Attached to Identity        | Limits                    |           |
| Session Policy        | Temporary Session           | Limits                    |           |
| VPC Endpoint Policy   | VPC level Traffic Filtering | Limits                    |           |
