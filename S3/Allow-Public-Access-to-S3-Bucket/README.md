# Project 2 : How to Allow Public Access to S3 Bucket and Host index.html File

## Objective

In this project, you will learn:

* How to create an S3 bucket
* How to upload an `index.html` file
* How to allow public access
* How to enable Static Website Hosting
* How to access your website using the S3 website endpoint URL

---

# Step 1 : Login to AWS Console

1. Open AWS Console
2. Search for `S3`
3. Click on `S3`

---

# Step 2 : Create S3 Bucket

1. Click on `Create bucket`

---

## Bucket Configuration

### Bucket Type

Select:

```text
General Purpose
```

---

## Bucket Name Rules

1. Bucket name must be unique
2. Capital letters are not allowed
3. Special characters are not allowed
4. Length should be between 3 to 63 characters
5. Bucket name should not look like IP address

---

## Example Bucket Names

```text
my-static-website-project
cloudverse-demo-site
aws-s3-static-hosting
```

---

# Step 3 : Disable Block Public Access

Scroll down to:

```text
Block Public Access settings for this bucket
```

Uncheck:

```text
Block all public access
```

AWS will show warning message.

Check:

```text
I acknowledge that the current settings might result in this bucket and the objects within becoming public.
```

---

# Why We Disable Block Public Access?

Because:

```text
Static websites must be publicly accessible.
```

If public access is blocked:

* Users cannot open your website
* Browser will show Access Denied error

---

# Step 4 : Create Bucket

Click:

```text
Create bucket
```

---

# Step 5 : Upload index.html File

1. Open your bucket
2. Click `Upload`
3. Click `Add files`
4. Select:

```text
index.html
```

5. Click:

```text
Upload
```

---

# Step 6 : Enable Static Website Hosting

Inside bucket:

1. Open:

```text
Properties tab
```

2. Scroll down to:

```text
Static website hosting
```

3. Click:

```text
Edit
```

---

## Static Website Hosting Configuration

Enable:

```text
Enable
```

Hosting type:

```text
Host a static website
```

Index document:

```text
index.html
```

Error document:

```text
error.html
```

(Optional)

Click:

```text
Save changes
```

---

# Step 7 : Add Bucket Policy

Now we must allow public users to read files.

Open:

```text
Permissions tab
```

Scroll to:

```text
Bucket Policy
```

Click:

```text
Edit
```

---

# Bucket Policy

Replace:

```text
YOUR_BUCKET_NAME
```

with your real bucket name.

Example:

```text
my-static-website-project
```

---

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```

---

# What This Policy Does?

This policy allows:

```text
Anyone on the internet can read objects inside the bucket.
```

Important:

```text
Only GET access is allowed.
```

Users cannot:

* Delete files
* Upload files
* Modify files

---

# Step 8 : Save Policy

Click:

```text
Save changes
```

---

# Step 9 : Open Website Endpoint URL

Go to:

```text
Properties → Static Website Hosting
```

You will see:

```text
Bucket website endpoint
```

Example:

```text
http://my-static-website-project.s3-website-us-east-1.amazonaws.com
```

Click the URL.

Your static website will open.

---

# Architecture Flow

```text
User Browser
      ↓
S3 Website Endpoint
      ↓
Amazon S3 Bucket
      ↓
index.html File
```

---

# Common Errors

## 1. Access Denied

Reason:

* Block Public Access still enabled
* Bucket policy missing

Solution:

* Disable Block Public Access
* Add Bucket Policy correctly

---

## 2. 404 Not Found

Reason:

```text
index.html file missing
```

Solution:

Upload:

```text
index.html
```

---

## 3. Website Not Loading

Reason:

```text
Static Website Hosting not enabled
```

Solution:

Enable:

```text
Static Website Hosting
```

---

# Important AWS S3 Concepts Used

| Feature                | Purpose                               |
| ---------------------- | ------------------------------------- |
| S3 Bucket              | Stores website files                  |
| Object Storage         | Stores HTML, CSS, JS, Images          |
| Static Website Hosting | Hosts website publicly                |
| Bucket Policy          | Controls permissions                  |
| Public Access          | Allows internet users to access files |
| Website Endpoint       | URL to open website                   |

---

# Real World Uses of S3 Static Hosting

* Portfolio websites
* Landing pages
* Documentation websites
* Resume websites
* Company static websites
* React frontend hosting
* Angular frontend hosting
* Backup web pages

---

# Final Result

After completing this project:

✅ Your `index.html` website will be publicly accessible.

✅ Anyone with the website URL can open your website.

✅ Your website will be hosted completely serverless using AWS S3.

---

# Mini Revision

## Steps Summary

1. Create bucket
2. Disable Block Public Access
3. Upload index.html
4. Enable Static Website Hosting
5. Add Bucket Policy
6. Open Website Endpoint URL

---

