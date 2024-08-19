# Section6: EC2 - Solutions Architect Associate Level

##  프라이빗  vs 퍼블릭 vs 탄력적 IP

### Private vs Public IP (IPv4)

- Networking has two sorts of IPs. IPv4 and IPv6
  - IPv4 - 4개 숫자가 점으로 나뉘어져 있음 
    - `1.160.10.240`
  - IPv6
    - 좀 더 김
    - `3ffe:1900:4545:3:200:f8ff:fe21:67cf`
- IPv4 is still the most common format used online
- IPv6 is newr and solves problems for the Internet of Things(IoTs)
- IPv4 allows for 3.7 billion differnet addresses in the public space
- IPv4 `[0-255].[0-255].[0-255].[0-255]`



### Fundamental Differencs btwn Private and Public IP

- Public IP
  - Public IP means the machine can be identified on the internet(WWW)
  - Must be unique across the whole web (not two machiens can have the same public IP)
  - Can be geo-located easily
- Private IP
  - Private IP means the machine can only be identified on a private network only
  - The IP must be unique across the private network
  - BUT two different private networks (two companies) can have the same IPs
  - Machines connect to WWW using a NAT + internet gateway (a proxy)
  - Only a specified range of IPs can be used as private IP



### Elastic IPs

- When you stop and then start an EC2 instance, it can change its public IP
- if you need to have a fixed public IP for your instance, you need an Elastic IP
- An Elastic IP is a public IPv4 IP you won as long as you don't delete it
- You can attach it to one instance at a time
- With an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account
  - You can only have 5 Elastic IP in your account (you can ask AWS to increase that, but's quite rare)
- Overall, try to **avoid using Elastic IP**
  - They often reflect poor architectural decisions
  - Instead, **use a random public IP** and register a DNS name to it
  - or use a Load balancer and don't use a public IP at all



## EC2 배치 그룹

### Placement Groups

- Sometimes you want control over teh EC2 Instance placement strategy
- That strategy can be defined using placement groups
- When you create a placement group, you specify one of the following strategies for the group
  - Cluster
    - clusters instances into a low-latency group in a single Availability Zone
  - Spread
    - spread instances across underlying hardware (max 7 instances per group per AZ) - critical applications
  - Partition
    - spread instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group (Hadoop, Cassandra, Kafka)



### Cluster

- Pros: Great network
  - 10 Gbps bandwith between instances with Enhanced Networking enabled
  - no latency
- Cons: if the AZ fails, all instances will fail at the same time
- Use Case:
  - Big Data job that needs to be completed fast
  - Application that needs extremely low latency and high network throughput



### Spread

- Pros: 
  - Can span across Availability Zone(AZ)
  - Reduced risk is simultaneous failure
  - EC2 instance are on different physical hardware
- Cons
  - **Limited to 7 instances** per AZ per placement group
- Use Case
  - Application that needs to maximize high availability
  - Critical Applications where each instance must be isolated from failure from each other



### Partition

- Pros
  - Up to 7 partitions per AZ
  - Can span acorss multiple AZs in the same region
  - Up to 100s of EC2 instances
  - The instances in a partition do not share racks with the instances in the other partitions
  - A partition failure can affect many EC2 **but won't affect other partitions**
  - EC2 instances get access to the partition information as metadata
- Use Case
  - Big data applications such as HDFS, Hbase, Cassandra, Kafka



## ENI(Elastic Network Interfaces)

### Elastic Network Interfaces(ENI)

- Logical component in a VPC that represents a virtual network card
- The ENI can have the following attributes:
  - Primary private IPv4, one or more secondary IPv4
  - One Elastic IP (IPv4) per private IPv4
  - One Public IPv4
  - One or more Security group[s
  - A MAC address
- You can create ENI independently and attach them on the fly(move them) on EC2 instances for failover
- Bound to a specific availability zone (AZ)



## EC2 Hibernate 모드

### EC2 Hibernate

- We know we can stop, terminate instances
  - Stop
    - the data on disk(EBS) is kept intact in the next start
  - Terminate
    - any EBS volumes(root) also set-up to be destroyed is lost
- On start, the following happens
  - First start: the OS boots & the EC2 User Data script is run 
  - Following starts: the OS boots up
  - Then your application starts, caches get warmed up, and that can take time
- Introducing EC2 Hibernate
  - The in-memory (RAM) stat is preserved
  - The instance boot is much faster(the OS is not stopped/restrated)
  - Under the hood, the RAM state is written to a file in the root EBS volume
  - The root EBS volume must be encrypted
- Use cases
  - Long-running processing
  - Saving the RAM state
  - Services that take time to initialize



### Good to know

- Supported Instance Families
  - C3, C4, C5, I3, M3, M4, R3, R4, T2, T3, ...
- Instance RAM size
  - must be **less than 150GB**
- Instance Size
  - not supported for bare metal instances
- AMI
  - Amazon Linux 2, Linux AMI, Ubuntu, RHEL, CentOS & Windows
- Root Volume
  - must be EBS, encrypted, not instance store, and large
- Available for On-Demand, Reserved and Spot Instances
- An instance can NOT be hibernated more than **60 days**



