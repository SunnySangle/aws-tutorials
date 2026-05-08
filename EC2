---

# ✅ What is EC2? (Simple Definition)

**EC2 (Elastic Compute Cloud)** is an AWS service that gives you a **virtual computer (server)** on the cloud where you can:

- Install an OS (Linux / Windows)
- Run applications
- Host websites
- Practice Linux & AWS commands

👉 Instead of buying a physical laptop/server, AWS **rents you a server** on the internet.

---

# 🧠 Real-Life Example

Imagine:

- You want to open a **shop**
- Instead of buying land & building, you **rent a shop**

Similarly:

- Instead of buying a physical server
- You **rent a virtual server** → that is **EC2**

---

# 🖥️ What exactly do you get in EC2?

When you create an EC2 instance, AWS gives you:

| Component | Meaning |
| --- | --- |
| Instance | Virtual machine |
| CPU | Processing power |
| RAM | Memory |
| Storage (EBS) | Hard disk |
| IP address | To connect |
| OS | Linux / Windows |

---

# 🔑 Why it is called **Elastic**?

Because you can:

- Increase CPU/RAM anytime
- Stop, start, terminate anytime
- Pay only for what you use

---

# 🧩 Important EC2 Terms (Must Know)

### 1️⃣ AMI (Amazon Machine Image)

- Blueprint of OS
- Example: Ubuntu, Amazon Linux

👉 Like installing Windows or Linux on your laptop

---

### 2️⃣ Instance Type

- Hardware configuration
- Example: `t2.micro` (Free Tier)

👉 CPU + RAM size

---

### 3️⃣ Key Pair

- Used to **login securely**
- `.pem` file

👉 Like your **house key**

---

### 4️⃣ Security Group

- Acts as **firewall**
- Controls inbound & outbound traffic

👉 Like a **security guard**

---

### 5️⃣ EBS (Elastic Block Store)

- Storage attached to EC2

👉 Like your laptop hard disk

---

# 🏗️ How to Create EC2 (Step-by-Step – Easy)

## 🔹 Step 1: Login to AWS Console

- Go to **AWS Console**
- Search → **EC2**
- Click **Launch Instance**

---

## 🔹 Step 2: Choose AMI

Select:

- **Amazon Linux 2023** or **Ubuntu**
- Free tier eligible ✔️

👉 This is your OS

---

## 🔹 Step 3: Choose Instance Type

Select:

- **t2.micro**
- Free tier ✔️

👉 Small CPU & RAM (good for practice)

---

## 🔹 Step 4: Create Key Pair

- Click **Create new key pair**
- Name: `my-ec2-key`
- Download `.pem` file
- Save it safely ❗

👉 Without this, you **cannot login**

---

## 🔹 Step 5: Network & Security Group

Allow:

- **SSH (22)** → My IP
- **HTTP (80)** → Anywhere (if hosting website)

👉 Controls who can access your EC2

---

## 🔹 Step 6: Configure Storage

- Default: 8 GB
- Free tier ✔️

---

## 🔹 Step 7: Launch Instance

Click **Launch Instance** 🎉

Your EC2 is now **RUNNING** ✅

---

# 🔐 How to Connect to EC2 (Linux)

### Step 1: Open Terminal (Linux / Mac / Git Bash)

```bash
chmod 400 my-ec2-key.pem

```

### Step 2: Connect using SSH

```bash
ssh -i my-ec2-key.pem ec2-user@<Public-IP>

```

👉 For Ubuntu:

```bash
ssh -i my-ec2-key.pem ubuntu@<Public-IP>

```

---

# 🌐 Example: Host a Simple Website on EC2

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd

```

Create HTML file:

```bash
echo "Hello Sunny! EC2 is working" | sudo tee /var/www/html/index.html

```

Open browser:

```
http://<Public-IP>

```

🎉 Website LIVE!

---

# 💰 EC2 Pricing (Simple)

- Pay **per second/hour**
- Free tier: `t2.micro` for **750 hours/month**
- Stop instance → billing stops (except storage)

---

# 🧪 Why EC2 is Important for You (Career)

Since you are learning AWS:

- EC2 is **core service**
- Asked in **every AWS interview**
- Used in:
    - Web hosting
    - DevOps
    - Cloud projects
    - MNC roles

---
