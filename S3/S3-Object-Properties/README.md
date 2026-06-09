# Important Object Properties

When file uploads in S3:

You can see:

| Property | Meaning |
| --- | --- |
| URL | File access URL |
| Owner | File owner |
| Region | Bucket region |
| ARN | Unique AWS resource name |
| Last Modified | Last update time |
| Type | File type |
| Object URL | Direct access link |
| Key | Object file path |

---

# Example of Object Key

```
sunny/vid/got.mp4
```

Here:

| Part | Meaning |
| --- | --- |
| sunny/vid | Prefix |
| got.mp4 | File name |

---

# What is Prefix?

Prefix means folder path before file.

Example:

```
images/photo.png
```

Prefix:

```
images/
```

---

# Tags During Upload

While uploading object you can add:

```
Tags
```

Example:

| Key | Value |
| --- | --- |
| Environment | Production |

Used for:

✅ Billing

✅ Management

✅ Automation