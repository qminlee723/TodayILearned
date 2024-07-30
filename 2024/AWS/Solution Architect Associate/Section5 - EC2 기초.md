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



## EC2 인스턴스 유형 기본 사항

