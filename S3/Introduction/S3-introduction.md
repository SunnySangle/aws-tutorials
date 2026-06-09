# What is Amazon S3?

Amazon S3 is a storage service provided by Amazon Web Services.

S3 stands for:

```
Simple Storage Service
```

It is used to:

- Store files
- Store images
- Store videos
- Backup data
- Host static websites
- Store application logs
- Store cloud data

---

# Real Life Example

Think of S3 like:

```
Google Drive or Dropbox in the cloud
```

But designed for:

- applications
- developers
- companies
- backups
- websites

---

# Important S3 Concepts

| Term | Meaning |
| --- | --- |
| Bucket | Folder/container |
| Object | File stored inside bucket |
| Key | File name/path |
| Region | Location where bucket exists |

---

# Example

```
Bucket Name: my-photo-bucket
```

Files inside:

```
photo1.jpg
video.mp4
resume.pdf
```

---

# Benefits of S3

# 1. Unlimited Storage

You can store:

- TBs
- PBs
- huge files

---

# 2. Highly Durable

AWS stores copies of data automatically.

Durability:

```
99.999999999% (11 nines)
```

Very safe.

---

# 3. Low Cost

Pay only for:

- storage used
- requests
- data transfer

---

# 4. Accessible Anywhere

Can access files:

- globally
- anytime
- using internet

---

# 5. Static Website Hosting

You can host:

- HTML
- CSS
- JavaScript websites

directly from S3.

---

# 6. Backup and Recovery

Used for:

- database backup
- server backup
- snapshots
- logs

---

# 7. Security

Supports:

- IAM policies
- bucket policies
- encryption
- versioning

---

# 8. Integration with AWS Services

Works with:

- EC2
- Lambda
- CloudFront
- DynamoDB
- Glacier

---

# S3 Storage Classes

| Storage Class | Use Case |
| --- | --- |
| Standard | Frequently used data |
| Intelligent Tiering | Auto cost optimization |
| Standard-IA | Rarely accessed |
| One Zone-IA | Cheap storage |
| Glacier | Archival backup |
| Glacier Deep Archive | Long-term archive |

---

# Architecture

```
User ---> S3 Bucket ---> Files
```

---

# Hands-On Project

# How to Create Your First S3 Bucket

---

# Step 1: Login to AWS Console

Open:

[AWS Console](https://console.aws.amazon.com/?utm_source=chatgpt.com)

---

# Step 2: Open S3 Service

Search:

```
S3
```

Open:

[Amazon S3 Console](https://console.aws.amazon.com/s3?utm_source=chatgpt.com)

---

# Step 3: Click Create Bucket

Click:

```
Create bucket
```

---

# Step 4: Enter Bucket Name

Example:

```
my-first-s3-bucket-123
```

IMPORTANT:

- Bucket name must be globally unique
- No spaces
- Small letters only

---

# Step 5: Select AWS Region

Example:

```
Asia Pacific (Mumbai) ap-south-1
```

Choose nearest region.

---

# Step 6: Object Ownership

Keep default:

```
ACLs disabled
```

---

# Step 7: Block Public Access

Keep enabled for security.

For learning website hosting later:

- you may disable temporarily

For now:

- keep default settings

---

# Step 8: Bucket Versioning

Optional.

Purpose:

- recover deleted files
- restore older versions

For practice:

- Disable

---

# Step 9: Encryption

Keep:

```
Server-side encryption with Amazon S3 keys (SSE-S3)
```

Default is fine.

---

# Step 10: Create Bucket

Click:

```
Create bucket
```

Bucket created successfully.

---

# Upload Your First File

# Step 11: Open Bucket

Click bucket name.

---

# Step 12: Upload File

Click:

```
Upload
```

Choose:

- image
- pdf
- text file

Then click:

```
Upload
```

---

# Step 13: Verify File Uploaded

You will see file inside bucket.

Example:

```
hello.txt
```

---

# How S3 Stores Data

```
Bucket
   ↓
Objects (files)
```

Example:

```
mybucket
   ├── photo.jpg
   ├── resume.pdf
   └── video.mp4
```

---

# Important Interview Questions

# What is Bucket?

```
In Amazon S3, a Bucket is:

A container used to store files (objects)

Think of Bucket like:

A folder or storage box
Real-Life Example

Example Bucket:

my-photo-bucket

Inside bucket:

photo1.jpg
video.mp4
resume.pdf

Important Points About Bucket
Feature	Description
Stores objects/files	Yes
Must have unique name	Globally unique
Created in region	Example Mumbai
Can contain unlimited objects	Yes

Bucket Architecture
Bucket
   ├── image.jpg
   ├── notes.txt
   └── movie.mp4
```

---

# What is Object?

```
Object means:

A file stored inside S3 bucket

Examples of objects:

image.jpg
video.mp4
document.pdf
backup.zip
Simple Understanding
S3 Term	Real Meaning
Bucket	Folder/container
Object	File
Example

Bucket Name:

student-data

Objects inside:

resume.pdf
marksheet.pdf
photo.png

Here:

student-data = Bucket
resume.pdf = Object
photo.png = Object
```

---

# What is Key?

```
Every object has unique name/path called Key.

Example:

images/profile.jpg

Here:

Key = images/profile.jpg
Object Structure

An S3 object contains:

Part	Meaning
Key	File name/path
Data	Actual file
Metadata	Information about file
Example of Metadata
Metadata	Example
File Size	2 MB
Last Modified	Today
Content Type	image/png
Easy Analogy
Mobile Phone Example
Mobile Gallery	S3
Album	Bucket
Photo	Object
Final Flow
User
  ↓
S3 Bucket
  ↓
Object (files)
```

Example:

```
images/photo.jpg
```

---

# Real World Use Cases

| Use Case | Example |
| --- | --- |
| Static Website Hosting | Portfolio website |
| Backup | Database backup |
| Media Storage | Videos/photos |
| Application Logs | CloudTrail logs |
| Data Lake | Big Data |

---

# Small Practice Task

Try:

1. Create bucket
2. Upload image
3. Upload text file
4. Delete file
5. Re-upload file

This helps understand object operations.

---

# Final Flow

```
User
  ↓
S3 Bucket
  ↓
Stored Files
```