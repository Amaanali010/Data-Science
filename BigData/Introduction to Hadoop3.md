# Introduction to Hadoop

## Audience

Beginner students in:

- Computer Science
- Data Science
- Information Technology
- Big Data Analytics

---

# Learning Objectives

By the end of this lecture, students will be able to:

- Define Hadoop
- Understand why Hadoop was developed
- Explain Hadoop architecture
- Understand HDFS and MapReduce
- Identify Hadoop ecosystem tools
- Understand Hadoop workflow
- Explore real-world applications
- Recognize Hadoop advantages and limitations

---

# Lecture Outline

| Section | Topic |
|---|---|
| 1 | Introduction & Motivation |
| 2 | What is Hadoop? |
| 3 | Why Hadoop is Needed |
| 4 | Hadoop Architecture |
| 5 | HDFS (Hadoop Distributed File System) |
| 6 | MapReduce |
| 7 | Hadoop Ecosystem |
| 8 | Applications, Advantages & Limitations |
| 9 | Activity / Discussion |
| 10 | Quiz & Conclusion |

---

# PART 1 — Introduction & Motivation

## Opening Questions

Ask students:

- What happens when data becomes too large for one computer?
- Can traditional databases handle petabytes of data?
- How do companies like Google and Facebook process huge datasets?

---

## Real-World Examples

# YouTube

Processes:

- Videos
- Comments
- User activity

# Facebook

Stores:

- Photos
- Messages
- Reactions
- Friend connections

# Banks

Analyze:

- Millions of transactions
- Fraud detection patterns

---

## Problem Statement

Traditional systems face problems with:

- Large-scale storage
- Fast processing
- Fault tolerance
- Scalability

This led to the development of Hadoop.

---

# PART 2 — What is Hadoop?

## Definition

Hadoop is an open-source framework used for:

- Distributed storage
- Distributed processing
- Large-scale data analysis

across clusters of computers.

---

## Simple Explanation

Instead of using one powerful computer:

Hadoop uses many computers working together.

---

## Key Features

- Distributed Computing
- Scalability
- Fault Tolerance
- Cost Effectiveness
- Parallel Processing

---

## History of Hadoop

- Inspired by Google’s distributed computing papers
- Developed by Apache Software Foundation
- Named after creator’s toy elephant

---

## Core Idea

> “Store data across many machines and process it in parallel.”

---

# PART 3 — Why Hadoop is Needed

# Problems with Traditional Systems

| Traditional Systems | Problems |
|---|---|
| Single machine storage | Limited capacity |
| Centralized processing | Slow performance |
| Expensive hardware | High cost |
| Poor fault tolerance | Risk of failure |

---

# Hadoop Solutions

| Hadoop Feature | Benefit |
|---|---|
| Distributed storage | Massive scalability |
| Parallel processing | Faster analytics |
| Commodity hardware | Lower cost |
| Replication | Fault tolerance |

---

## Example

If one server fails:

Hadoop automatically retrieves data from another server copy.

---

# PART 4 — Hadoop Architecture

# Main Hadoop Components

- HDFS
- MapReduce
- YARN
- Hadoop Common

---

# 1. HDFS

Hadoop Distributed File System

Responsible for:

- Storing large files
- Splitting files into blocks
- Distributing blocks across machines

---

# 2. MapReduce

Programming model for processing big data.

Handles:

- Parallel computation
- Distributed processing

---

# 3. YARN

Yet Another Resource Negotiator

Responsible for:

- Resource management
- Job scheduling

---

# 4. Hadoop Common

Provides:

- Shared libraries
- Utilities
- APIs

---

# Hadoop Cluster

# Master Node

Controls the cluster.

# Slave Nodes

Store and process data.

---

## Architecture Diagram

Draw on board or slides:

Client → NameNode → DataNodes

Client → ResourceManager → NodeManagers

---

# PART 5 — HDFS (Hadoop Distributed File System)

# What is HDFS?

HDFS is Hadoop’s storage system.

Designed to:

- Store huge files
- Run on multiple machines
- Provide fault tolerance

---

# HDFS Concepts

# 1. Blocks

Large files are divided into smaller blocks.

### Example

1 GB file split into multiple blocks.

---

# 2. Replication

Each block is copied multiple times.

### Default

3 copies

### Purpose

- Prevent data loss

---

# 3. NameNode

Master server responsible for:

- Metadata
- File locations
- Block management

---

# 4. DataNode

Stores actual data blocks.

---

# HDFS Workflow

1. Client uploads file
2. File split into blocks
3. Blocks distributed across DataNodes
4. Replicas created

---

# Advantages of HDFS

- Highly scalable
- Fault tolerant
- Handles massive data

---

# Limitations

- Not suitable for small files
- High latency for real-time systems

---

# PART 6 — MapReduce

# What is MapReduce?

A programming model for processing large datasets in parallel.

---

# Two Main Phases

# 1. Map Phase

Processes input data into key-value pairs.

### Example — Word Count

Input:

> “Big data is powerful”

### Output

- (Big,1)
- (data,1)
- (is,1)
- (powerful,1)

---

# 2. Reduce Phase

Aggregates results.

### Example Output

- (Big,3)
- (data,5)

---

# Workflow

Input Data → Map → Shuffle → Reduce → Output

---

# Advantages

- Parallel processing
- Scalable
- Fault tolerant

---

# Example Use Cases

- Log analysis
- Search indexing
- Sales analytics

---

# Simple Word Count Example

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

# PART 7 — Hadoop Ecosystem

# Important Hadoop Tools

| Tool | Purpose |
|---|---|
| Hive | SQL queries |
| Pig | Data scripting |
| HBase | NoSQL database |
| Spark | Fast data processing |
| Sqoop | Data transfer |
| Flume | Log collection |
| Oozie | Workflow scheduling |

---

# Hadoop Ecosystem Flow

Data Sources → HDFS → Processing → Analytics

---

# PART 8 — Applications, Advantages & Limitations

# Real-World Applications

# 1. Banking

- Fraud detection
- Risk analysis

---

# 2. Healthcare

- Disease prediction
- Patient analytics

---

# 3. E-Commerce

- Recommendation systems
- Customer behavior analysis

---

# 4. Social Media

- Trend analysis
- Advertisement targeting

---

# Advantages of Hadoop

- Open source
- Scalable
- Fault tolerant
- Cost effective
- Distributed processing

---

# Limitations of Hadoop

- Complex setup
- High learning curve
- Slower for real-time analytics
- Security challenges

---

# PART 9 — Activity / Discussion

# Group Activity

Ask students:

> “How would Netflix use Hadoop?”

---

## Expected Answers

- Store viewing data
- Analyze recommendations
- Process user behavior

---

# PART 10 — Quiz & Conclusion

# Quiz

## Q1

What does HDFS stand for?

A. Hadoop Data File System  
B. Hadoop Distributed File System  
C. Hybrid Data Framework System  
D. Hadoop Dynamic File Storage  

**Answer:** B

---

## Q2

Which component manages resources in Hadoop?

A. HDFS  
B. YARN  
C. Hive  
D. Pig  

**Answer:** B

---

## Q3

Which node stores actual data?

A. NameNode  
B. DataNode  
C. ClientNode  
D. MasterNode  

**Answer:** B

---

## Q4

MapReduce mainly supports:

A. Gaming  
B. Parallel processing  
C. Image editing  
D. Networking  

**Answer:** B

---

# Summary

Today we learned:

- What Hadoop is
- Why Hadoop is needed
- Hadoop architecture
- HDFS
- MapReduce
- Hadoop ecosystem
- Applications and challenges

---

# Final Thought

> “Hadoop changed the way organizations store and process massive amounts of data.”

---

# Suggested Homework

1. Compare HDFS and traditional file systems.
2. Explain the role of NameNode and DataNode.
3. Research one Hadoop ecosystem tool.
