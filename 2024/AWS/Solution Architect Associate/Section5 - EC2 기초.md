# Section5: EC2 기초

##  EC2 기초

### Amazon EC2

- One of the most popular of AWS's offering
- EC2 = Elastic Compute Cloud = Infrastructure as a Service
- It mainly consists in the capability of:
  - Renting virtual machines(EC2)
  - Storing data on virtual drvies(EBS)
  - Distributing load across machines(ELB)
  - Scaling the services using an auto-scaling group(ASG)
- Knowing EC2 is fundamental to understand how to Cloud works



### EC2 sizing & configuration options

- Operating System(OS): Linux, Windows or MacOS
- How much compute power & cores(CPU)
- How much random-access memory(RAM)
- How much storage space:
  - Network-attached(EBS & EFS)
  - Hardware(EC2 Instance Store)
- Network card: speed of the card, Public IP address
- Firewall rules: security group
- Bootstrap script(configure at first launch): EC2 User Data



### EC2 User Data

- It is possible to bootstrap our instances using an EC2 User data script
- bootstraping means **launching commands when a machine starts**
- THat script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
  - Installing updates
  - Installing software
  - Downloading common files from the internet
  - Anything you can think of
- The EC2 User Data Script runs with the root user
  - everything runs with `sudo` command



## 웹사이트 실습

### Hands-On: Launching an EC2 Instance running Linux

- Launching our first virtual server using the AWS Console
- High-level approach to the various parameters
- Our web server is launched using EC2 user data
- How to start / stop / terminate our instance



## EC2 인스턴스 유형 기본 사항

### EC2 Instance Types - Overview

- You can use different types of EC2 instances that are optimized for different use cases
- AWS has the following naming convention:
  - `m5.2xlarge`
  - m: instance class
  - 5: generation (AWS improves them over time)
  - 2xlarge: size within the instance class



### EC2 Instance Types (1) General Purpose

- Great for a diversity of workloads such as **web servers** or **code repositories**
- Blance between:
  - Compute
  - Memory
  - Networking



### EC2 Instance Types (2) Compute Optimized

- Great for compute-instensive tasks that require high performance processors:
  - Batch processing workloads
  - Media transcoding
  - High performance web servers
  - High performance computing(HPC)
  - Scientific modeling & machine learning
  - Dedicated gaming servers



### EC2 Instance Types (3) Memory Optimized

- Fast performance for workloads that process large data sets in memory
- Use cases:
  - High performance, relational/non-relational databases
  - Distributed web scale cache stores(Elastic cache)
  - In-memory databases optimized for BI(business intelligence)
  - Applications performing real-time processing of big unstructured data



### EC2 Instance Types (4) Storage Optimized

- Greate for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage
- Use cases:
  - High frequency online transaction processing(OLTP) systems
  - Relational & NoSQL databases
  - Cache for in-memory databases(like Redis)
  - Data warehousing applications
  - Distributed file systems



## 보안 그룹 및 클래식 포트 개요

### Introduction to Security Groups

- Security Groups are the fundamental of network security in AWS
- They control how traffic is allowed into or out of our EC2 Instances
- Security groups only contain **"allow"** rules
- Security groups rules can reference by IP or by security group



### Security Groups Depper Dive

- Security groups are acting as a "firewall" on EC2 instances
- They regulate:
  - Access to Ports
  - Authorized IP ranges - IPv4 and IPv6
  - Control of inbound network (from other to the instance)
  - Control of outbound network (from the instance to other)



### Security Groups Diagram

- 기본적인 방화벽 작동방법

![Screenshot 2024-08-03 at 11.53.18 PM](./assets/Screenshot 2024-08-03 at 11.55.08 PM.png)



### Security Groups Good to know

- Can be attached to multiple instances
- Locked down to a region / VPC combination
- Does live "outside" the EC2 - if traffic is blocekd the EC2 instance won't see it
- It's good to maintain one separate security group for SSH access
- If your application is **not accessible (time out)**, then it's a **security group issue**
- If your application gives a **"connection refused"** error, then it's an **application error** or it's not launched
- All **inbound** traffic is **blocked** by default
- All **outbound** traffic is **authorized** by default



### Referencing other security groups Diagram

![Screenshot 2024-08-04 at 11.55.16 PM](./assets/Screenshot 2024-08-04 at 11.55.16 PM.png)



### Classic Ports to know

- 22 = SSH(Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) - upload files into a file share
- 22 = SFTP(Secure File Transfer Protocol) - upload files using SSH
- 80 = HTTP - access unsecured websites
- 443 = HTTPS - access secured websites
- 3389 = RDP (Remote Desktop Protocol) - log into a Windows instance



## SSH 개요

### SSH Summary Table

|               | SSH  | Putty | EC2 Instance Connect |
| ------------- | ---- | ----- | -------------------- |
| Mac           | O    |       | O                    |
| Linux         | O    |       | O                    |
| Windows < 10  |      | O     | O                    |
| Windows >= 10 | O    | O     | O                    |



### SSH troubleshooting

- Students have the most problems with SSH
- If thing's don't work
  - Re-watch the lecture.
  - Read the troubleshooting guide
  - Try EC2 Instance Connect



### How to SSH into your EC2 Instance Linux/MacOSX

- We'll learn how to SSH into your EC2 instance using Linux/Mac
- SSH is one of the most important function. It allows you to control a remote machine, all using the command line



## EC2 인스턴스 시작

### EC2 Instances Purchasing Options

- On-Demand Instances - short workload, predictalbe pridictable pricing, pay by second
- Reserved(1 & 3 years)
  - Reserved Instances - long workloads
  - Convertible Reserved Instances - long workloads with flexible instances
- Savings Plans (1 & 3 years) - commitmnet to an amount of usage, long workload
- Spot Instances - short workloads, cheap, can lose instances (less reliable)
- Dedicated Hosts - book an entire physical server, control instance placement
- Dedicated Instances - no other customers will share your hardware
- Capacity Reservations - reserve capacity in a specific AZ for any duration



### EC2 On Demand

- Pay for what you use
  - Linux or Windows - **billing per second, after the first minute**
  - All other operating systems - **billing per hour**
- Has the highest cost but no upfront payment
- No long-term commitment
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave



### EC2 Reserved Instances

- Up to 72% discount compared to On-demand
- You reserve a specific instance attributes(Instance Type, Region, Tenancy, OS)
- Reservation Period - 1 year(+discount) or 3 years(+++discount)
- Payment Options - No Upront, Partial Upfront, All Upfront
- Reserved Instance's Scope - Regional or Zonal(reserve capacity in an AZ)
- Recommended for steady-state usage applications (think database)
- You can buy and sell in the Reserved Instance Marketplace
- Convertible Reserved Instance
  - Can change the EC2 instance type, instance family, OS, scope and tenancy
  - Up to 66%



### EC2 Savings Plans

- Get a discount based on long-term usage (up to 72%)
- Commit to a certain type of usage($10/hour four 1 or 3 years)
- Usage beyond EC2 Sanges Plans is billed at the On-Demand price
- Locked to a specific instance family & AWS region (e.g., M5 in us-east-I)
- Flexible across
  - Instance Size(m5.xlarge, m5.2xlarge)
  - OS(Linux, Windows)
  - Tenancy(Host, Dedicated, Default)



### EC2 Spot Instances

- Can get a discount of up to 90% compared to On-demand
- Instances that you can "lose" at any point of time if your max price is less than the current spot price
- The MOST cost-efficient instances in AWS
- Useful for workloads that are resilient to failure
  - Batch jobs
  - Data analysis
  - Image processing
  - Any distributed workloads
  - Workloads with a flexible start and end time
- Not suitable for critical job or databases



### EC2 Dedicated Hosts

- A physical server with EC2 instance capacity fully dedicated to your use
- Allows you address compliance requirements and use your existing server-bound software licenses (per-soket, per-core, pe -- VM software licenses)
- Purchasing Options
  - On-demand
  - Reserved - 1 or 3 years (No Upfront, Partial Upfront, All Upfront)

- The most expensive option
- Useful for software that have complicated licensing model (BYOL - Bring Your Own License)
- Or for companies that have strong regulatory or compliance needs



### EC2 Dedicated Instances

- Instances run on hardware that's dedicated to you
- May share hardware with other instances in same account
- No control over instance placement (can move hardware after Stop/Start)



### EC2 Capacity Reservation

- Reserve On-Demand instances capacity in a specific AZ for any duration

- You always have access to EC2 capacity when you need it

- No time commitment(create/cancel anytime), no billing discounts

- Combine with Regional Reserved Instances and Savings Plans to benefit from billing discounts

- You're charged at On-Demand rate whether you run instances or not

  Suitable for short-term, uniterrupted workloads that needs to be in a specific AZ



### Which purchasing option is right for me?

- On demand: coming and staying in resort whenever we like, we pay the full price
- Reserved: like planning ahead and if we plan to stay for a long time, we may get a good discount
- Saving Plans: pay a certain amount per hour for certain period and stay in any room type
- Spot instances: the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms. You can get kicked out at any time
- Dedicated Hosts: We book an entire building of the resort



## 스팟 인스턴스 및 스팟 집합

### EC2 Spot Instance Requests

- Can get a discount of up to 90% compared to On-demand
- Define max spot price and get the instance while current spot price < max
  - the hourly spot price varies based on offer and capacity
  - if the current spot price > your max price you can choose to stop or terminate your instance with a 2 minutes grace period
- Used for batch jobs, data analysis, or workloads that are resilient to failures
- Not great for critical jobs or databases



### How to terminate Spot Instances?

- FIRST, **cancel the spot request** **FIRST**
- Then terminate the associated spot instnances



### Spot Fleets

- Spot Fleets = set of Spot Instances + (optional) On-Demand Instances
- The Spot Fleet will try to meet the target capacity with price constraints
  - Define possible launch pools: instance type(m5.large), OS, Availability Zone
  - Can have multiple launch pools, so that the fleet can choose
  - Spot Fleet stops launching instances when reaching capacity or max cost
- **Strategies to allocate Spot Instances** ⭐️
  - Lowest price: from the pool with the lowest price (cost optimization, short workload)
  - Diversified: distributed across all pools(great for availability, long workloads)
  - capacityOptimized: pool with the optimal capacity for the number of instances
  - priceCapacityOptimized (recommended): pools with highest capacity available, then select the pool with the lowest price(best choice for most workloads)
- <u>**Spot fleets allow us to automatically request Spot Instances with the lowest prices**</u>
