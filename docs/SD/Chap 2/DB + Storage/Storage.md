Storage is a mechanism that enables a system to retain data, either temporarily or permanently. This topic is mostly skipped over in the context of system design, however, it is important to have a basic understanding of some common types of storage techniques that can help us fine-tune our storage components. Let's discuss some important storage concepts:

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-raid "Permalink")RAID

RAID (Redundant Array of Independent Disks) is a way of storing the same data on multiple hard disks or solid-state drives (SSDs) to protect data in the case of a drive failure.

There are different RAID levels, however, and not all have the goal of providing redundancy. Let's discuss some commonly used RAID levels:

- **RAID 0**: Also known as striping, data is split evenly across all the drives in the array.
- **RAID 1**: Also known as mirroring, at least two drives contains the exact copy of a set of data. If a drive fails, others will still work.
- **RAID 5**: Striping with parity. Requires the use of at least 3 drives, striping the data across multiple drives like RAID 0, but also has a parity distributed across the drives.
- **RAID 6**: Striping with double parity. RAID 6 is like RAID 5, but the parity data are written to two drives.
- **RAID 10**: Combines striping plus mirroring from RAID 0 and RAID 1. It provides security by mirroring all data on secondary drives while using striping across each set of drives to speed up data transfers.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-comparison "Permalink")Comparison

Let's compare all the features of different RAID levels:

|Features|RAID 0|RAID 1|RAID 5|RAID 6|RAID 10|
|---|---|---|---|---|---|
|Description|Striping|Mirroring|Striping with Parity|Striping with double parity|Striping and Mirroring|
|Minimum Disks|2|2|3|4|4|
|Read Performance|High|High|High|High|High|
|Write Performance|High|Medium|High|High|Medium|
|Cost|Low|High|Low|Low|High|
|Fault Tolerance|None|Single-drive failure|Single-drive failure|Two-drive failure|Upto one disk failure in each sub-array|
|Capacity Utilization|100%|50%|67%-94%|50%-80%|50%|

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-volumes "Permalink")Volumes

Volume is a fixed amount of storage on a disk or tape. The term volume is often used as a synonym for the storage itself, but it is possible for a single disk to contain more than one volume or a volume to span more than one disk.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-file-storage "Permalink")File storage

File storage is a solution to store data as files and present it to its final users as a hierarchical directories structure. The main advantage is to provide a user-friendly solution to store and retrieve files. To locate a file in file storage, the complete path of the file is required. It is economical and easily structured and is usually found on hard drives, which means that they appear exactly the same for the user and on the hard drive.

**Example**: [Amazon EFS](https://aws.amazon.com/efs), [Azure files](https://azure.microsoft.com/en-in/services/storage/files), [Google Cloud Filestore](https://cloud.google.com/filestore), etc.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-block-storage "Permalink")Block storage

Block storage divides data into blocks (chunks) and stores them as separate pieces. Each block of data is given a unique identifier, which allows a storage system to place the smaller pieces of data wherever it is most convenient.

Block storage also decouples data from user environments, allowing that data to be spread across multiple environments. This creates multiple paths to the data and allows the user to retrieve it quickly. When a user or application requests data from a block storage system, the underlying storage system reassembles the data blocks and presents the data to the user or application

**Example**: [Amazon EBS](https://aws.amazon.com/ebs).

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-object-storage "Permalink")Object Storage

Object storage, which is also known as object-based storage, breaks data files up into pieces called objects. It then stores those objects in a single repository, which can be spread out across multiple networked systems.

**Example**: [Amazon S3](https://aws.amazon.com/s3), [Azure Blob Storage](https://azure.microsoft.com/en-in/services/storage/blobs), [Google Cloud Storage](https://cloud.google.com/storage), etc.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-nas "Permalink")NAS

A NAS (Network Attached Storage) is a storage device connected to a network that allows storage and retrieval of data from a central location for authorized network users. NAS devices are flexible, meaning that as we need additional storage, we can add to what we have. It's faster, less expensive, and provides all the benefits of a public cloud on-site, giving us complete control.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-hdfs "Permalink")HDFS

The Hadoop Distributed File System (HDFS) is a distributed file system designed to run on commodity hardware. HDFS is highly fault-tolerant and is designed to be deployed on low-cost hardware. HDFS provides high throughput access to application data and is suitable for applications that have large data sets. It has many similarities with existing distributed file systems.

HDFS is designed to reliably store very large files across machines in a large cluster. It stores each file as a sequence of blocks, all blocks in a file except the last block are the same size. The blocks of a file are replicated for fault tolerance