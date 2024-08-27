# SECTION 7. EC2 Instance Storage Section

## EBS 개요

### What's an EBS Volume?

- EBS(Elastic Block Store) Volume is a network drive you can attach to your instances while they run
- it allows your instances to persist data, even after their termination
- They can only be mounted to one instance at a time (at the CCP level)
- They are bound to a specific availability zone
- Analogy: Think of them as a "network USB stick"
- Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month



### EBS Volume

- It's a network drive (i.e. not a physical drive)
  - it uses the network to communicate the instance, which means there might be a bit of latency
- It's locked to an Availability Zone (AZ)
  - An EBS Volume in us-east-1a can't be attached to us-east-1b
  - To move a volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs, and IOPS)
  - You get billed for all the provisioned capacity
  - You can increase the capacity of the drive over time



### EBS - Delete on Termination attribute

- Controls the EBS behavior when an EC2 instnace terminates
  - By default, the root EBS volume is deleted (attribute enabled)
  - By default, any other attached EBS volume is not deleted(attribute disabled)
- This can be controlled by the AWS console / AWS CLI
- Use case: preserve root volume when instance is terminated



## EBS Sanpshots

### EBS snapshots

- Make a backup(snapshot) of yoru EBS volume at a point in time
- Not necessary to detach volume to do snapshot, but recommended
- Can copy snapshots across AZ or Region



### EBS Snapshots Features

- EBS sanpshot Archive
  - Move a Snapshot to an "archive tier" that is 75% cheaper
  - Takes within 24 to 72 hours for restoring the archive
- Recycle Bin for EBS Snapshots
  - Setup rules to retain deleted snapshots so you can recover them after an accidental deletion
  - Specify retention(fron 1 day to 1 year)
- Fast Snapshot Restore(FSR)
  - Force full initialization of snapshot to have no latency on the first use ($$$)



## AMI

### AMI Overview

- AMI = Amazon Machine Image
- AMI are customizatino of an EC2 instance
  - You add your own software, configuration, operating system, monitoring
  - Faster boot / configuration time because all your software is pre-packaged
- AMI are built for a specific region (and can be copied across regions)
- You can launch EC2 instances from
  - A Public AMI: AWS provided
  - Your own AMI: you make and maintain them yourself
  - An AWS Marketplace AMI: an AMI someone else made (and potentially sells)



### AMI Process (from an EC2 instance)

- Start an EC2 instance and customize it
- Stop the instance (for data integrity)
- Build an AMI - this will also create EBS snapshots
- Launch instances from other AMIs



## EC2 Instance Store

### EC2 Instance store

- EBS volumes ar entwork drives with good but limited performance
- if you need a high-performance hardware disk, use EC2 Instance Store
- Better I/O Performance
- EC2 Instance Store lose their storage if they're stopped (ephemeral)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fails



## EBS Volume Types

### EBS Volume Types

- EBS Volume come in 6 types
  - Gp2 / gp3 (SSD)
  - Io1 / io2 Block Express (SSD)
  - St1 (HDD)
  - Sc1 (HDD)
- EBS Volumes are characterized in 
  - Size
  - Throughput
  - IOPS(I/O Ops Per Sec)
- When in doubt always consult the AWS documentation 
- Only gp2/gp3 and io1/io2 Block Express can be used as boot volumes



### EBS Volume Types Use cases

#### General Purpose SSD

- Cost effective storage, low latency
- System boot volumes, Virtual desktops, Development and test environments
- 1 GB to 16 TB
- gp3
  - Baseline of 3000 IOPS and throughput of 125 MB/s
  - Can increase IOPS up to 16000 and throughput up to 1000 MB/s independently
- gp2
  - Small gp2 volumes can burst IOPS to 3000
  - Size of the volume and IOPS are linked, max IOPS is 16000
  - 3 IOPS per GB, means at 53334 GB we are at the max IOPS



#### Provisioned IOPS(PIOPS) SSD

- Critical business applications with sustained IOPS performance
- Or applications that need more than 16000 IOPS
- Great for databases workloads (sensitive to storage perf and consistency)
- Io1 (4GB - 16TB)
  - Max PIOS: 64000 for Nitro EC2 instances & 32000 for other
  - Can increase PIOPS independently from storage size
- Io2 Block Express (4GB - 64 TB)
  - Sub millizecon latnecy
  - Max PIOPS: 256000 with an IOPS: GB ratio of 1000:1
  - Supports EBS Multi-attach



#### Hard Disk Drives (HDD)

- Cannot be a boot volume
- 125 GB to 16 TB
- Throughput Optimized HDD (**ST1**)
  - Big Data, Data Warehouses, Log Processing
  - Max throughput 500 MB/s - max IOPS 500
- Cold HDD (**SC1**)
  - For data that is infrequently access(for archives)
  - Scenarios where lowest cost is important
  - Max throughput 250 MB - max IOPS 250