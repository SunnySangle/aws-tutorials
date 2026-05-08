# How to Install Python on EC2

## Step by Step Guide (Amazon Linux & Ubuntu)

Python is often already installed on EC2, but in real projects you may need:

✅ Latest Python version
✅ pip
✅ Virtual environment
✅ Flask/Django setup

We’ll cover:

1. Launch EC2
2. Connect with SSH
3. Check Python
4. Install Python
5. Install pip
6. Run Python program

---

# 🔹 Step 1: Launch EC2 Instance

Go to AWS Console:

AWS → EC2 → Launch Instance

Choose:

| Setting        | Value                       |
| -------------- | --------------------------- |
| AMI            | Amazon Linux 2023 OR Ubuntu |
| Instance Type  | t2.micro                    |
| Security Group | Allow SSH (22)              |

Launch instance.

---

# 🔹 Step 2: Connect to EC2 Using SSH

Copy public IP.

---

## For Amazon Linux

Username:

```text id="jlwm42"
ec2-user
```

SSH command:

```bash id="0zjdrh"
ssh -i my-key.pem ec2-user@PUBLIC-IP
```

---

## For Ubuntu

Username:

```text id="4r3t9n"
ubuntu
```

SSH command:

```bash id="jlwmk8"
ssh -i my-key.pem ubuntu@PUBLIC-IP
```

---

# 🔹 Step 3: Check Existing Python Installation

Run:

```bash id="n7mjlwm"
python3 --version
```

Example output:

```bash id="0h8jlwm"
Python 3.12.1
```

If already installed → good.

---

# 🔹 Install Python on Amazon Linux 2023

Amazon Linux 2023 uses:

```text id="ycf1rr"
dnf
```

---

## Step 4A: Update Packages

```bash id="c2jlwm"
sudo dnf update -y
```

---

## Step 5A: Install Python

```bash id="jlwm8a"
sudo dnf install python3 -y
```

---

## Step 6A: Verify Installation

```bash id="fjlwm9"
python3 --version
```

---

# 🔹 Install Python on Ubuntu

Ubuntu uses:

```text id="jlwm0b"
apt
```

---

## Step 4B: Update Packages

```bash id="gjlwm1"
sudo apt update -y
```

---

## Step 5B: Install Python

```bash id="hjlwm2"
sudo apt install python3 -y
```

---

## Step 6B: Verify Installation

```bash id="ijlwm3"
python3 --version
```

---

# 🔹 Step 7: Install pip

pip is Python package manager.

---

## Amazon Linux

```bash id="jjlwm4"
sudo dnf install python3-pip -y
```

---

## Ubuntu

```bash id="kjlwm5"
sudo apt install python3-pip -y
```

---

## Verify pip

```bash id="ljlwm6"
pip3 --version
```

---

# 🔹 Step 8: Create Python File

Create file:

```bash id="mjlwm7"
nano app.py
```

Add:

```python id="njlwm8"
print("Hello from EC2 Python Server")
```

Save:

```text id="ojlwm9"
CTRL + O
ENTER
CTRL + X
```

---

# 🔹 Step 9: Run Python Program

```bash id="pjlwm0"
python3 app.py
```

Output:

```text id="qjlwm1"
Hello from EC2 Python Server
```

Success ✅

---

# 🔹 Step 10: Install Python Libraries

Example install Flask:

```bash id="rjlwm2"
pip3 install flask
```

Install requests:

```bash id="sjlwm3"
pip3 install requests
```

---

# 🔹 Step 11: Create Virtual Environment (Best Practice)

Very important in real projects.

Install:

```bash id="tjlwm4"
sudo dnf install python3-virtualenv -y
```

OR Ubuntu:

```bash id="ujlwm5"
sudo apt install python3-venv -y
```

---

## Create Virtual Environment

```bash id="vjlwm6"
python3 -m venv myenv
```

---

## Activate Environment

```bash id="wjlwm7"
source myenv/bin/activate
```

Now prompt changes:

```text id="xjlwm8"
(myenv)
```

---

## Deactivate

```bash id="yjlwm9"
deactivate
```

---

# 🔹 Step 12: Install Flask Example

Inside virtual environment:

```bash id="zjlwm0"
pip install flask
```

Create:

```bash id="ajlwm1"
nano app.py
```

Code:

```python id="bjlwm2"
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Flask App Running on EC2"

app.run(host='0.0.0.0', port=5000)
```

Run:

```bash id="cjlwm3"
python3 app.py
```

---

# 🔹 Step 13: Open Security Group Port

Allow:

```text id="djlwm4"
Custom TCP
Port 5000
```

Then access:

```text id="ejlwm5"
http://PUBLIC-IP:5000
```

---

# 🔹 Common Errors

## Error 1: python command not found

Use:

```bash id="fjlwm6"
python3
```

---

## Error 2: pip command not found

Install pip:

```bash id="gjlwm7"
sudo dnf install python3-pip -y
```

---

## Error 3: Permission denied

Use:

```bash id="hjlwm8"
sudo
```

---

# 🔹 Real Production Setup

