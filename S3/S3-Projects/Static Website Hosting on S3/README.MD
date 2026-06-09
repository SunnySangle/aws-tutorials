# What is Static Website Hosting?

S3 can host:

✅ HTML

✅ CSS

✅ JavaScript

But NOT backend languages like:

❌ PHP

❌ Node.js

❌ Python

---

# Step 1: Create Bucket

Create bucket with unique name.

---

# Step 2: Upload Website Files

Upload:

```
index.html
error.html
style.css
```

---

# Step 3: Enable Public Access

Disable block public access.

Add bucket policy.

---

# Step 4: Enable Static Website Hosting

Go to:

```
Properties
```

Find:

```
Static Website Hosting
```

Click:

```
Enable
```

---

# Step 5: Enter Index Document

```
index.html
```

---

# Step 6: Enter Error Document

```
error.html
```

Save changes.

---

# Step 7: Open Website Endpoint

AWS gives:

```
Bucket Website Endpoint URL
```

Open browser.

Website hosted successfully.

---