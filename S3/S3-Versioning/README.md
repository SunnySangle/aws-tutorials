# What is Versioning?

Versioning stores multiple versions of same object.

It helps:

✅ Recover deleted files

✅ Restore old files

✅ Prevent accidental deletion

---

# Important Point

⚠️ Versioning increases storage cost because old versions are also stored.

---

# Step 1: Open Bucket

Go to:

```
Bucket → Properties
```

---

# Step 2: Enable Versioning

Find:

```
Bucket Versioning
```

Click:

```
Enable
```

Save changes.

---

# Example

Upload:

```
file.txt
```

Edit and upload again.

S3 stores:

```
Version 1
Version 2
Version 3
```

---

# How Deletion Works?

If you delete object:

S3 adds:

```
Delete Marker
```

Actual file still exists internally.

---

# How to Recover Deleted Object?

1. Open bucket
2. Enable:

```
Show Versions
```

1. Delete delete-marker
2. Old object restored  