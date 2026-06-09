# AWS EBS Snapshot Explained Step by Step (Easy Practical Flow)

# 🔹 What is Snapshot in AWS?

An AWS EBS Snapshot is a **backup copy of an EBS volume** stored in Amazon S3 internally by AWS.

It helps:

✅ Protect data from crash

✅ Recover deleted data

✅ Create new volumes

✅ Backup important files

✅ Disaster recovery

---

# 🔹 Real Flow

```
EC2 Instance
   ↓
EBS Volume Attached
   ↓
Store Files
   ↓
Take Snapshot
   ↓
Create New EBS from Snapshot
   ↓
Attach to EC2
   ↓
Recover Files
```

---

# 🔹 Step 1: Create EC2 Instance

Launch:

| Setting | Value |
| --- | --- |
| AMI | Amazon Linux / Ubuntu |
| Instance | t2.micro |

Connect using SSH.

---

# 🔹 Step 2: Create and Attach EBS Volume

Go to:

EC2 → Volumes → Create Volume

Example:

| Size | 5 GB |
| --- | --- |
| Type | gp3 |
| AZ | Same as EC2 |

Attach volume to EC2.

Example device name:

```bash
/dev/xvdb
```

---

# 🔹 Step 3: Check Attached Volumes

Run:

```bash
lsblk
```

Meaning:

```
List block storage devices
```

Example output:

```
xvda   8:0    0   8G
└─xvda1

xvdb   8:16   0   5G
```

Here:

```
xvdb = new EBS volume
```

---

# 🔹 Step 4: Become Root User

Run:

```bash
sudo su
```

Now you are root user.

---

# 🔹 Step 5: Check File System

Run:

```bash
file -s /dev/xvdb
```

If new volume, output looks like:

```
/dev/xvdb: data
```

Meaning:

```
No filesystem exists
```

---

# 🔹 Step 6: Create File System

Format volume:

\text{mkfs.ext4 } /dev/xvdb

Command:

```bash
mkfs.ext4 /dev/xvdb
```

Meaning:

```
Create ext4 filesystem
```

---

# 🔹 Step 7: Verify Again

Run:

```bash
file -s /dev/xvdb
```

Now output shows:

```
ext4 filesystem
```

Success ✅

---

# 🔹 Step 8: Create Mount Directory

Run:

```bash
mkdir /data
```

---

# 🔹 Step 9: Mount EBS Volume

Run:

```bash
mount /dev/xvdb /data
```

Meaning:

```
Attach storage to directory
```

---

# 🔹 Step 10: Verify Mount

Run:

```bash
mountpoint /data
```

Output:

```
/data is a mountpoint
```

Success ✅

---

# 🔹 Step 11: Move into Volume

Run:

```bash
cd /data
```

Check files:

```bash
ls
```

---

# 🔹 Step 12: Create Some Files

Create file:

```bash
echo "Sunny" > abc.txt
```

Check:

```bash
ls -lh
```

Output:

```
abc.txt
```

---

# 🔹 Step 13: Check Disk Usage

Run:

```bash
df -h
```

Meaning:

```
Shows mounted disk usage
```

---

# 🔹 Step 14: Create Snapshot

Go to:

EC2 → Volumes

Select EBS volume.

Click:

```
Actions → Create Snapshot
```

Add name:

```
my-ebs-backup
```

Create snapshot.

---

# 🔹 Step 15: Add More Files After Snapshot

Now create extra files:

```bash
echo "This is new file in ebs volume" > xyz.txt
```

OR

```bash
echo "This is new file in ebs volume" > /data/pql.txt
```

Check:

```bash
cd /data
ls -lh
```

Now:

```
abc.txt
xyz.txt
pql.txt
```

---

# 🔹 Important Concept

Snapshot only contains data present at snapshot creation time.

Files created AFTER snapshot are NOT included.

---

# 🔹 Step 16: Create New EBS Volume from Snapshot

Go to:

EC2 → Snapshots

Select snapshot.

Click:

```
Create Volume from Snapshot
```

You can change:

✅ Size

✅ Volume type

✅ Availability Zone

---

# 🔹 Step 17: Attach New EBS to EC2

Attach to same or another EC2.

Example device:

```bash
/dev/xvdc
```

---

# 🔹 Step 18: Check Attached Volume

Run:

```bash
lsblk
```

---

# 🔹 Step 19: Check File System

Run:

```bash
file -s /dev/xvdc
```

IMPORTANT:

Snapshot volume already has filesystem.

Output should show:

```
ext4 filesystem
```

---

# 🔹 Very Important Mistake

❌ DO NOT RUN:

```bash
mkfs.ext4 /dev/xvdc
```

on snapshot-restored volume.

Why?

Because formatting deletes snapshot data.

---

# 🔹 Step 20: Create Mount Directory

Run:

```bash
mkdir /dataone
```

---

# 🔹 Step 21: Mount Snapshot Volume

Run:

```bash
mount /dev/xvdc /dataone
```

---

# 🔹 Step 22: Verify Mount

Run:

```bash
mountpoint /dataone
```

Output:

```
/dataone is a mountpoint
```

---

# 🔹 Step 23: Check Restored Files

Run:

```bash
cd /dataone
ls -lh
```

You should see files that existed during snapshot:

```
abc.txt
```

But files created after snapshot may not appear.

---

# 🔹 Real Meaning of Snapshot

```
Snapshot = Point-in-time backup
```

---

# 🔹 Real Company Use Cases

Companies use snapshots for:

✅ Backup before updates

✅ Disaster recovery

✅ Restore deleted data

✅ Clone environments

✅ Migration

---

# 🔹 Important Interview Point

Snapshots are:

✅ Incremental

✅ Stored in S3 internally

✅ AZ-independent inside same region

---

# 🔹 Common Commands Summary

| Command | Purpose |
| --- | --- |
| lsblk | List disks |
| file -s | Check filesystem |
| mkfs.ext4 | Create filesystem |
| mount | Attach volume |
| mountpoint | Verify mount |
| df -h | Check storage |
| ls -lh | List files |

---

# 🔹 Important Warning

## New Empty EBS

✅ Format required

```bash
mkfs.ext4
```

---

## Snapshot-Based EBS

❌ Do NOT format again

Otherwise data erased.

---

# 🔹 Interview Answer

**What is EBS Snapshot?**

An EBS Snapshot is a point-in-time backup of an EBS volume stored by AWS. It is used for backup, disaster recovery, and creating new EBS volumes with existing data.

---

# 🔹 Final Summary

```
Create EC2
→ Attach EBS
→ Create filesystem
→ Mount volume
→ Store files
→ Create snapshot
→ Create new volume from snapshot
→ Attach new volume
→ Mount and recover files
```
