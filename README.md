# Creating-IAM-Policies
### Creating IAM Policies for Secure AWS Access (EC2, S3, DynamoDB)
### Overview

This project demonstrates how to design and implement custom IAM policies to enforce least privilege access across AWS services.

Policies created:

EC2 access policy
S3 access policy
DynamoDB access policy

### What is IAM Policy?

An IAM Policy is a JSON-based security document that defines:

What actions are allowed or denied
Which resources are affected
Under what conditions access is granted

### Problem Statement

In many environments:

Users are given overly broad permissions
Policies are poorly defined
Access is not restricted properly

### The challenge:
How do we enforce least privilege while still enabling functionality?

### Solution

We created custom IAM policies that:

Grant only required permissions
Restrict access to specific resources
Use AWS best practices

### Implementation Steps

🔹 Step 1: Create EC2 Policy
Allow specific EC2 actions (Start, Stop, Describe)
Restrict scope to defined resources

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["ec2:StartInstances", "ec2:StopInstances"],
      "Resource": "*"
    }
  ]
}

🔹 Step 2: Create S3 Policy
Allow read-only or specific bucket access

{
  "Effect": "Allow",
  "Action": ["s3:GetObject"],
  "Resource": "arn:aws:s3:::example-bucket/*"
}


🔹 Step 3: Create DynamoDB Policy
Allow controlled database access

{
  "Effect": "Allow",
  "Action": ["dynamodb:GetItem", "dynamodb:PutItem"],
  "Resource": "*"
}

🔹 Step 4: Attach Policies
Attach to IAM users, groups, or roles

### Security Controls Implemented 

✅ Least privilege enforcement
✅ Default deny model
✅ Resource-level restrictions
✅ Granular access control


### Testing 
| Test Case            | Result     |
| -------------------- | ---------- |
| Allowed action       | Success ✅  |
| Unauthorized action  | Blocked ❌  |
| Resource restriction | Enforced ✅ |

### Key Security Insight

### IAM policies follow a “default deny” model.

This means:

Everything is denied unless explicitly allowed
Fine-grained control reduces risk significantly

### Future Improvements

Add condition-based policies (IP, MFA)
Implement service control policies (SCPs)
Use IAM Access Analyzer
Automate with Terraform
