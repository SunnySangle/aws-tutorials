# What is Elastic Load Balancer (ELB) in AWS?

An **Elastic Load Balancer (ELB)** automatically distributes incoming traffic across multiple EC2 instances.

Instead of users directly accessing one EC2 server, traffic first goes to the Load Balancer, and then ELB sends requests to healthy servers.

---

# Why ELB is Used?

Suppose:

- 1 EC2 server handles your website
- Suddenly 10,000 users visit
- One server may crash

ELB helps by:

✅ Distributing traffic

✅ Preventing overload

✅ Improving availability

✅ Working with Auto Scaling

✅ Automatically checking healthy servers

---

# Real Example

Imagine:

You created:

- 2 EC2 web servers
- Both hosting same website

Without ELB:

- Users manually open specific EC2 IP
- If one EC2 fails → website down

With ELB:

Users access:

```
mywebsite-alb.amazonaws.com
```

ELB automatically sends traffic:

```
User 1 → EC2-1
User 2 → EC2-2
User 3 → EC2-1
```

If EC2-1 crashes:

```
All traffic → EC2-2
```

---

# Types of ELB in AWS

| Type | Use |
| --- | --- |
| Application Load Balancer (ALB) | HTTP/HTTPS traffic |
| Network Load Balancer (NLB) | High performance TCP/UDP |
| Gateway Load Balancer | Security appliances |

Mostly used:

# ALB (Application Load Balancer)

---

# Architecture We Will Build

```
User
   ↓
Application Load Balancer
   ↓
Auto Scaling Group
   ↓
EC2 Instances created from AMI
```

---

# Hands-on Practical

We will create:

1. EC2 instance
2. Install website
3. Create AMI
4. Create Target Group
5. Create Load Balancer
6. Create Launch Template
7. Create Auto Scaling Group
8. Test Auto Scaling

---

# STEP 1: Create EC2 Instance

Go to:

```
AWS Console → EC2 → Launch Instance
```

## Configure

| Setting | Value |
| --- | --- |
| Name | Web-Server |
| AMI | Amazon Linux 2 |
| Instance Type | t2.micro |
| Key Pair | Select/Create |
| Security Group | Allow HTTP + SSH |

---

# Security Group Rules

| Type | Port |
| --- | --- |
| SSH | 22 |
| HTTP | 80 |

---

# STEP 2: Install Apache Web Server

Connect using SSH:

```bash
ssh -i key.pem ec2-user@public-ip
```

---

## Update packages

```bash
sudo yum update -y
```

---

## Install Apache

```bash
sudo yum install httpd -y
```

---

## Start Apache

```bash
sudo systemctl start httpd
```

Enable after reboot:

```bash
sudo systemctl enable httpd
```

---

# STEP 3: Create Simple Website

Create HTML page:

```bash
sudo nano /var/www/html/index.html
```

Add:

```html
<h1>Welcome from AWS Web Server</h1>
```

Save:

```
CTRL + O
ENTER
CTRL + X
```

---

# STEP 4: Test Website

Open browser:

```
http://EC2-Public-IP
```

You should see:

```
Welcome from AWS Web Server
```

---

# STEP 5: Create AMI

# What is AMI?

AMI = Amazon Machine Image

It is a backup/template of EC2.

It stores:

✅ OS

✅ Installed software

✅ Website files

✅ Configurations

---

## Create AMI

Go to:

```
EC2 → Instances
```

Select instance →

```
Actions → Image and Templates → Create Image
```

Name:

```
WebServer-AMI
```

Click:

```
Create Image
```

Wait until:

```
AMI State = Available
```

---

# Why AMI is Important?

Auto Scaling uses AMI to create identical EC2 instances automatically.

Example:

```
Original EC2:
- Apache installed
- Website configured

AMI copies everything
```

New instances created automatically from same setup.

---

# STEP 6: Create Target Group

# What is Target Group?

Target Group contains EC2 instances where ELB sends traffic.

Go to:

```
EC2 → Target Groups
```

Click:

```
Create Target Group
```

---

## Configure

| Setting | Value |
| --- | --- |
| Target Type | Instances |
| Name | web-target-group |
| Protocol | HTTP |
| Port | 80 |

Next →

Register instance →

Select your EC2 →

```
Include as Pending Below
```

Create Target Group.

---

# STEP 7: Create Application Load Balancer

Go to:

```
EC2 → Load Balancers
```

Click:

```
Create Load Balancer
```

Choose:

```
Application Load Balancer
```

---

# Configure ALB

| Setting | Value |
| --- | --- |
| Name | My-ALB |
| Scheme | Internet-facing |
| IP Type | IPv4 |

---

## Select VPC and Subnets

Choose:

✅ Minimum 2 Availability Zones

Example:

```
us-east-1a
us-east-1b
```

---

# Security Group for ALB

Allow:

| Type | Port |
| --- | --- |
| HTTP | 80 |

---

# Listener

| Protocol | Port |
| --- | --- |
| HTTP | 80 |

Forward to:

```
web-target-group
```

Create Load Balancer.

---

# STEP 8: Test ELB

Copy:

```
ALB DNS Name
```

Example:

```
my-alb-123.us-east-1.elb.amazonaws.com
```

Open browser.

You should see website.

---

# Traffic Flow

```
Browser
   ↓
ALB
   ↓
Target Group
   ↓
EC2 Instance
```

---

# STEP 9: Create Launch Template

# Why Launch Template?

Auto Scaling needs instructions:

```
Which AMI?
Which instance type?
Which security group?
```

Launch Template stores all these.

---

Go to:

```
EC2 → Launch Templates
```

Click:

```
Create Launch Template
```

---

## Configure

| Setting | Value |
| --- | --- |
| Name | web-launch-template |
| AMI | Select your AMI |
| Instance Type | t2.micro |
| Key Pair | Select |
| Security Group | Allow HTTP |

Create Launch Template.

---

# STEP 10: Create Auto Scaling Group

Go to:

```
EC2 → Auto Scaling Groups
```

Click:

```
Create Auto Scaling Group
```

---

# Configure

| Setting | Value |
| --- | --- |
| Name | web-asg |
| Launch Template | Select created template |

Next.

---

# Select Network

Choose:

✅ Same VPC

✅ Multiple AZs

Next.

---

# Attach Load Balancer

Choose:

```
Attach existing load balancer
```

Select:

```
My-ALB
```

Choose target group:

```
web-target-group
```

Next.

---

# Group Size

| Setting | Value |
| --- | --- |
| Desired Capacity | 2 |
| Minimum Capacity | 2 |
| Maximum Capacity | 4 |

Meaning:

```
Minimum 2 servers always running
Maximum 4 servers can scale
```

---

# STEP 11: Configure Scaling Policy

Choose:

```
Target Tracking Scaling Policy
```

Metric:

```
Average CPU Utilization
```

Target:

```
50%
```

Meaning:

If CPU > 50%

→ Auto Scaling launches new EC2 instance.

---

# STEP 12: Create Auto Scaling Group

Click:

```
Create Auto Scaling Group
```

Now AWS automatically launches:

✅ 2 EC2 instances

✅ Registers them with ALB

---

# STEP 13: Verify Instances

Go to:

```
EC2 → Instances
```

You will see:

```
2 instances running
```

Both created from AMI.

---

# STEP 14: Test Load Balancing

Open ALB DNS multiple times.

Traffic distributes between instances.

---

# STEP 15: Test Auto Scaling

SSH into one instance.

Install stress tool:

```bash
sudo yum install stress -y
```

Run CPU stress:

```bash
stress --cpu 2 --timeout 300
```

CPU increases.

Auto Scaling detects high CPU.

AWS launches new instance automatically.

---

# What Happens Internally?

```
High Traffic
    ↓
CPU increases
    ↓
CloudWatch alarm triggers
    ↓
Auto Scaling launches new EC2
    ↓
New EC2 created from AMI
    ↓
Attached to ELB
    ↓
Traffic distributed automatically
```

---

# Complete Flow Diagram

```
               Users
                  ↓
        Application Load Balancer
                  ↓
         Target Group
          ↓        ↓
      EC2-1      EC2-2
          ↓        ↓
      Auto Scaling Group
                  ↓
        Launch Template
                  ↓
               AMI
```

---

# Important Interview Questions

## 1. Why ELB is used?

To distribute traffic across multiple servers and improve availability.

---

## 2. Difference between ELB and Auto Scaling?

| ELB | Auto Scaling |
| --- | --- |
| Distributes traffic | Adds/removes servers |
| Improves availability | Improves scalability |

---

## 3. Why AMI is required in Auto Scaling?

AMI acts as template to create identical EC2 instances automatically.

---

## 4. What is Target Group?

Group of EC2 instances receiving traffic from Load Balancer.

---

# Real Production Example

Example:

Food delivery app.

During lunch time:

```
Traffic increases massively
```

Auto Scaling:

```
2 → 10 EC2 instances
```

ELB distributes users among all servers.

At night:

```
Traffic decreases
```

Auto Scaling removes extra servers to save money.

---

# Important Services Used

| Service | Purpose |
| --- | --- |
| EC2 | Web servers |
| AMI | Server template |
| ELB | Traffic distribution |
| Target Group | EC2 grouping |
| Auto Scaling | Automatic scaling |
| CloudWatch | Monitoring CPU |
