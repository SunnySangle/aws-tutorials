IAM stands for:

```
Identity and Access Management
```

AWS Identity and Access Management is the AWS service used to control:

- Who can log in to AWS
- What they can access
- What actions they can perform

---

# Real-Life Example

Imagine a company office.

| Office | AWS IAM |
| --- | --- |
| Employees | Users |
| Departments | Groups |
| Permission Letter | Policy |
| Temporary Visitor Pass | Role |

---

# What is IAM?

IAM is the security guard of AWS.

It decides:

```
Who can access AWS?
What resources can they access?
What actions can they perform?
```

Example:

- Rahul can access S3 only.
- Priya can access EC2 only.
- Admin can access everything.

---

# What is a User?

A User is:

```
A person or application that needs AWS access.
```

Examples:

- Rahul
- Priya
- Developer
- DevOps Engineer

---

## Real Example

Company Employees:

```
Rahul
Priya
Amit
```

Create AWS users:

```
rahul
priya
amit
```

Each gets:

- Username
- Password
- Access Keys (optional)

---

# What is a Group?

Group means:

```
Collection of users with same permissions.
```

Example:

```
Developers Group
```

Members:

```
Rahul
Amit
Rohan
```

Instead of giving permissions one by one:

```
Give permissions to Group
```

All users inherit them.

---

# Why Use Groups?

Without Group:

```
Attach S3 Policy to Rahul
Attach S3 Policy to Amit
Attach S3 Policy to Rohan
```

With Group:

```
Developers Group
   ↓
Attach S3 Policy once
```

All members get access.

---

# What is a Policy?

Policy means:

```
Permission document written in JSON.
```

Policy controls:

- Allow
- Deny

actions in AWS.

---

# Example Policy

Allow S3 Read Access:

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Action":"s3:GetObject",
      "Resource":"*"
    }
  ]
}
```

Meaning:

```
User can read S3 objects
```

---

# Types of Policies

| Type | Description |
| --- | --- |
| AWS Managed Policy | Created by AWS |
| Customer Managed Policy | Created by You |
| Inline Policy | Attached directly |

---

# Project 1: Create IAM User

---

## Step 1

Login AWS Console.

Search:

```
IAM
```

Open IAM.

---

## Step 2

Click:

```
Users
```

---

## Step 3

Click:

```
Create User
```

---

## Step 4

Enter username:

```
rahul
```

---

## Step 5

Choose:

```
Provide user access to AWS Management Console
```

---

## Step 6

Set password:

```
Custom Password
```

Example:

```
Password@123
```

---

## Step 7

Click:

```
Next
```

---

## Step 8

Attach permissions later.

---

## Step 9

Click:

```
Create User
```

User created.

---

# Project 2: Create Group

---

## Step 1

IAM → User Groups

---

## Step 2

Click:

```
Create Group
```

---

## Step 3

Group Name:

```
Developers
```

---

## Step 4

Attach Policy:

Example:

```
AmazonS3ReadOnlyAccess
```

---

## Step 5

Click:

```
Create Group
```

Group created.

---

# Project 3: Add User to Group

---

## Step 1

Open User:

```
rahul
```

---

## Step 2

Click:

```
Add User To Group
```

---

## Step 3

Select:

```
Developers
```

---

## Step 4

Save.

Now Rahul gets all permissions from Developers Group.

---

# What is a Custom Policy?

Custom Policy means:

```
Policy created by you.
```

AWS Managed Policy:

```
Created by AWS
```

Custom Policy:

```
Created by You
```

---

# Example Requirement

Allow:

```
Only S3 Bucket Listing
```

Do NOT allow:

- Delete
- Upload

---

# Project 4: Create Custom Policy

---

## Step 1

IAM → Policies

---

## Step 2

Click:

```
Create Policy
```

---

## Step 3

Select:

```
JSON
```

---

## Step 4

Paste:

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Action":[
        "s3:ListBucket"
      ],
      "Resource":"*"
    }
  ]
}
```

---

## Step 5

Click:

```
Next
```

---

## Step 6

Policy Name:

```
S3ListOnlyPolicy
```

---

## Step 7

Create Policy.

Policy ready.

---

# Project 5: Attach Policy to User

---

## Step 1

IAM → Users

---

## Step 2

Open:

```
rahul
```

---

## Step 3

Permissions Tab

---

## Step 4

Click:

```
Add Permissions
```

---

## Step 5

Choose:

```
Attach Policies Directly
```

---

## Step 6

Select:

```
S3ListOnlyPolicy
```

---

## Step 7

Save.

Policy attached to User.

---

# Project 6: Attach Policy to Group

---

## Step 1

IAM → User Groups

---

## Step 2

Open:

```
Developers
```

---

## Step 3

Permissions

---

## Step 4

Click:

```
Add Permissions
```

---

## Step 5

Select:

```
S3ListOnlyPolicy
```

---

## Step 6

Save.

All users in Developers group now get this policy.

---

# What is a Role?

Role means:

```
Temporary AWS permissions assigned to a service or user.
```

Unlike User:

```
Role has NO username and password.
```

---

# Real-Life Example

Office Visitor Pass:

```
Temporary Access
```

After work:

```
Access ends
```

That is similar to IAM Role.

---

# Why Roles Are Used?

AWS Services need permissions too.

Example:

```
EC2 needs access to S3
Lambda needs access to DynamoDB
```

Instead of storing credentials:

```
Use IAM Role
```

---

# Example

```
EC2
 ↓
IAM Role
 ↓
S3 Access
```

---

# Project 7: Create IAM Role

---

## Step 1

IAM → Roles

---

## Step 2

Click:

```
Create Role
```

---

## Step 3

Trusted Entity Type:

```
AWS Service
```

---

## Step 4

Select Service:

```
EC2
```

---

## Step 5

Next

---

## Step 6

Attach Policy:

Example:

```
AmazonS3ReadOnlyAccess
```

---

## Step 7

Next

---

## Step 8

Role Name:

```
EC2-S3-Role
```

---

## Step 9

Create Role

Done.

---

# Attach Role to EC2

---

## Step 1

Open EC2

---

## Step 2

Select Instance

---

## Step 3

Actions

---

## Step 4

Security

---

## Step 5

Modify IAM Role

---

## Step 6

Choose:

```
EC2-S3-Role
```

---

## Step 7

Save

Now EC2 can access S3 without Access Keys.

---

# IAM Best Practices

✅ Use Groups for permissions

✅ Enable MFA

✅ Use Roles for AWS services

✅ Avoid Root User

✅ Follow Least Privilege Principle

```
Give only required permissions
```

---

# Interview Questions

## What is IAM?

```
IAM is AWS service used to manage authentication and authorization.
```

---

## Difference Between User and Role

| User | Role |
| --- | --- |
| Permanent Identity | Temporary Identity |
| Username + Password | No Password |
| Human Login | Service Access |

---

## Difference Between User and Group

| User | Group |
| --- | --- |
| Individual Person | Collection of Users |
| Direct Login | No Login |

---

## Difference Between Policy and Role

| Policy | Role |
| --- | --- |
| Permission Document | Uses Permissions |
| JSON | Temporary Identity |

---

# Final Architecture

```
Users
   ↓
Groups
   ↓
Policies
   ↓
Permissions

EC2 / Lambda
   ↓
Roles
   ↓
AWS Resources
```

# Easy One-Line Definitions

- **IAM** → Controls access to AWS.
- **User** → Individual identity.
- **Group** → Collection of users.
- **Policy** → Permission document (JSON).
- **Role** → Temporary permissions for users or AWS services.
