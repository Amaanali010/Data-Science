# Hadoop Architecture

## Audience

Students of:

- Computer Science
- Information Technology
- Data Science
- Big Data Analytics

---

# Learning Objectives

By the end of this lecture, students will be able to:

- Understand Hadoop architecture
- Explain Hadoop core components
- Understand HDFS architecture
- Explain YARN architecture
- Understand MapReduce workflow
- Identify master and slave nodes
- Explain data storage and processing in Hadoop
- Understand fault tolerance and scalability

---

# Lecture Outline

| Section | Topic |
|---|---|
| 1 | Introduction & Motivation |
| 2 | Overview of Hadoop Architecture |
| 3 | Hadoop Core Components |
| 4 | HDFS Architecture |
| 5 | YARN Architecture |
| 6 | MapReduce Architecture & Workflow |
| 7 | Fault Tolerance & Scalability |
| 8 | Real-World Applications |
| 9 | Activity / Discussion |
| 10 | Quiz & Conclusion |

---

# PART 1 — Introduction & Motivation

## Opening Questions

Ask students:

- Can one computer process petabytes of data?
- What happens if one server fails?
- How do companies process huge datasets efficiently?

---

## Real-World Examples

# Google

Processes billions of searches daily.

---

# Facebook

Stores massive user data.

---

# Netflix

Analyzes viewing behavior from millions of users.

---

## Problem with Traditional Systems

Traditional systems face:

- Limited storage
- Slow processing
- High hardware costs
- Single point of failure

---

## Solution

Hadoop architecture solves these problems using:

- Distributed storage
- Distributed processing
- Fault tolerance
- Parallel computing

---

# PART 2 — Overview of Hadoop Architecture

# What is Hadoop Architecture?

Hadoop Architecture is the structure of Hadoop components working together for:

- Data storage
- Resource management
- Distributed processing

---

# Main Components of Hadoop Architecture

- HDFS
- YARN
- MapReduce
- Hadoop Common

---

# High-Level Workflow

Data → HDFS → YARN → MapReduce → Output

---

# Key Features

- Distributed storage
- Parallel processing
- Scalability
- Reliability
- Fault tolerance

---

# Hadoop Cluster

A Hadoop cluster consists of:

# Master Nodes

Manage the cluster.

# Slave Nodes

Store and process data.

---

# PART 3 — Hadoop Core Components

# 1. Hadoop Common

Provides:

- Shared libraries
- Utilities
- APIs

Acts as the foundation for Hadoop modules.

---

# 2. HDFS

Responsible for:

- Distributed storage
- File replication
- Fault tolerance

---

# 3. YARN

Responsible for:

- Resource management
- Job scheduling

---

# 4. MapReduce

Responsible for:

- Parallel data processing
- Computation

---

# Hadoop Architecture Diagram

Draw on board or slides:

Client → NameNode → DataNodes

Client → ResourceManager → NodeManagers

---

# PART 4 — HDFS Architecture

# What is HDFS?

HDFS stands for:

> Hadoop Distributed File System

Designed to store:

- Very large files
- Across multiple machines

---

# HDFS Components

# 1. NameNode (Master Node)

Responsible for:

- Metadata management
- File system namespace
- Tracking block locations

---

## Example Metadata

- File name
- File permissions
- Block locations

---

## Important Point

NameNode does NOT store actual file data.

It stores metadata only.

---

# 2. DataNode (Slave Node)

Responsible for:

- Storing actual data blocks
- Reading and writing data
- Sending reports to NameNode

---

# Block Storage

Large files are divided into blocks.

## Example

1 GB file split into multiple blocks.

### Default Block Size

128 MB (commonly)

---

# Replication

Each block is copied multiple times.

### Default Replication Factor

3

### Purpose

- Fault tolerance
- Data availability

---

# HDFS Workflow

## Step 1

Client uploads file.

## Step 2

File divided into blocks.

## Step 3

Blocks distributed across DataNodes.

## Step 4

Replicas created automatically.

---

# HDFS Read Operation

1. Client requests file
2. NameNode provides block locations
3. Client retrieves blocks from DataNodes

---

# HDFS Write Operation

1. Client contacts NameNode
2. NameNode selects DataNodes
3. Data written to DataNodes
4. Replicas created

---

# Advantages of HDFS

- Fault tolerant
- Scalable
- Reliable
- Distributed storage

---

# Limitations of HDFS

- Not suitable for small files
- High latency
- NameNode can become a bottleneck

---

# PART 5 — YARN Architecture

# What is YARN?

YARN stands for:

> Yet Another Resource Negotiator

Responsible for:

- Resource management
- Job scheduling

---

# Why YARN Was Introduced

Earlier Hadoop versions had scalability limitations.

YARN separates:

- Resource management
- Data processing

---

# YARN Components

# 1. ResourceManager

Master service responsible for:

- Resource allocation
- Cluster management

---

# 2. NodeManager

Runs on slave nodes.

Responsible for:

- Managing resources on each node
- Monitoring containers

---

# 3. ApplicationMaster

Responsible for:

- Managing application execution
- Negotiating resources

---

# 4. Containers

Provide:

- CPU
- Memory
- Execution environment

---

# YARN Workflow

1. Client submits job
2. ResourceManager allocates resources
3. ApplicationMaster starts
4. Tasks execute in containers
5. Results returned

---

# Advantages of YARN

- Better scalability
- Improved resource utilization
- Supports multiple processing engines

---

# PART 6 — MapReduce Architecture & Workflow

# What is MapReduce?

Programming model for processing massive datasets.

---

# Two Main Phases

# 1. Map Phase

Processes input into key-value pairs.

## Example

### Input

> “Hadoop is powerful”

### Output

- (Hadoop,1)
- (is,1)
- (powerful,1)

---

# 2. Reduce Phase

Aggregates intermediate results.

## Example

- (Hadoop,5)

---

# MapReduce Workflow

Input Data → Split → Map → Shuffle → Reduce → Output

---

# Detailed Workflow

# Step 1

Input split into blocks.

# Step 2

Mapper processes each block.

# Step 3

Shuffle and Sort phase groups keys.

# Step 4

Reducer aggregates data.

# Step 5

Final output stored in HDFS.

---

# Word Count Example

## Sentence

> “Hadoop Hadoop Big Data”

### Map Output

- (Hadoop,1)
- (Hadoop,1)
- (Big,1)
- (Data,1)

### Reduce Output

- (Hadoop,2)
- (Big,1)
- (Data,1)

---

# Advantages of MapReduce

- Parallel processing
- Fault tolerance
- Scalability

---

# Limitations

- Slower than Spark
- High disk I/O

---

# PART 7 — Fault Tolerance & Scalability

# Fault Tolerance

If one DataNode fails:

Replicas from other nodes are used.

---

# Scalability

To increase capacity:

Add more nodes to the cluster.

---

# Load Balancing

Data distributed evenly across nodes.

---

# PART 8 — Real-World Applications

# Applications of Hadoop Architecture

# Banking

- Fraud detection

---

# Healthcare

- Patient analytics

---

# E-Commerce

- Recommendation systems

---

# Social Media

- Trend analysis

---

# Telecom

- Call data analysis

---

# PART 9 — Activity / Discussion

# Classroom Activity

Ask students:

> “How would YouTube use Hadoop architecture?”

---

## Expected Answers

- Store videos
- Analyze user behavior
- Recommendation systems

---

# PART 10 — Quiz & Conclusion

# Quiz

## Q1

Which Hadoop component stores metadata?

A. DataNode  
B. NameNode  
C. Reducer  
D. Container  

**Answer:** B

---

## Q2

Which Hadoop component manages resources?

A. HDFS  
B. YARN  
C. Hive  
D. Pig  

**Answer:** B

---

## Q3

What is the default purpose of replication?

A. Compression  
B. Visualization  
C. Fault tolerance  
D. Encryption  

**Answer:** C

---

## Q4

Which phase groups intermediate keys?

A. Input  
B. Map  
C. Shuffle  
D. Split  

**Answer:** C

---

# Summary

Today we learned:

- Hadoop architecture overview
- HDFS architecture
- YARN architecture
- MapReduce workflow
- Fault tolerance
- Scalability

---

# Final Thought

> “Hadoop architecture enables organizations to store and process massive data efficiently across distributed systems.”

---

# Suggested Homework

1. Explain NameNode and DataNode roles.
2. Draw Hadoop architecture diagram.
3. Compare YARN and MapReduce responsibilities.
