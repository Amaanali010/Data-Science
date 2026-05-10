# Introduction to Apache Oozie and HDFS Processing

## Complete 2-Hour Lecture Plan

---

# Lecture Information

- **Topic:** Introduction to Apache Oozie and HDFS Processing
- **Duration:** 2 Hours
- **Audience:** Beginners in Hadoop Ecosystem
- **Prerequisites:** Basic Linux knowledge and understanding of distributed systems

---

# Learning Objectives

By the end of this lecture, students will be able to:

- Understand Hadoop ecosystem basics
- Explain HDFS architecture and processing
- Use common HDFS commands
- Understand Apache Oozie workflow scheduling
- Create basic Oozie workflows
- Execute and monitor workflows
- Integrate HDFS operations with Oozie

---

# Lecture Breakdown

| Time | Topic |
|---|---|
| 0:00 – 0:10 | Introduction to Hadoop Ecosystem |
| 0:10 – 0:35 | HDFS Fundamentals |
| 0:35 – 0:55 | HDFS Commands & Processing |
| 0:55 – 1:05 | Break / Q&A |
| 1:05 – 1:25 | Introduction to Apache Oozie |
| 1:25 – 1:45 | Oozie Workflow Components |
| 1:45 – 1:55 | Hands-on Example |
| 1:55 – 2:00 | Summary & Quiz |

---

# PART 1 — Introduction to Hadoop Ecosystem

**Duration:** 10 Minutes

---

## What is Big Data?

Big Data refers to extremely large and complex datasets that traditional databases cannot process efficiently.

---

## Characteristics of Big Data (5Vs)

### 1. Volume
Large amounts of data

### 2. Velocity
Fast data generation speed

### 3. Variety
Different formats:

- Text
- Video
- Audio
- Logs

### 4. Veracity
Data quality and accuracy

### 5. Value
Useful business insights

---

## Hadoop Ecosystem Overview

### Core Hadoop Components

| Component | Purpose |
|---|---|
| HDFS | Storage |
| YARN | Resource Management |
| MapReduce | Data Processing |
| Oozie | Workflow Scheduling |
| Hive | SQL Processing |
| Pig | Scripting |
| Spark | Fast Analytics |

---

## Why Hadoop?

### Advantages

- Distributed storage
- Parallel processing
- Scalability
- Fault tolerance
- Cost-effective

---

# PART 2 — HDFS Fundamentals

**Duration:** 25 Minutes

---

## What is HDFS?

HDFS stands for:

> **Hadoop Distributed File System**

It is a distributed file system designed to store very large files across multiple machines.

---

## Features of HDFS

### Key Features

#### 1. Distributed Storage
Files stored across many servers

#### 2. Fault Tolerance
Data replicated automatically

#### 3. High Throughput
Fast data access

#### 4. Scalability
Easy to add new nodes

#### 5. Reliability
Handles hardware failures

---

## HDFS Architecture

### Main Components

### 1. NameNode

Master server

#### Responsibilities:

- Stores metadata
- Manages namespace
- Tracks file locations

---

### 2. DataNode

Worker nodes

#### Responsibilities:

- Store actual data blocks
- Perform read/write operations

---

### 3. Secondary NameNode

Checkpoint manager

#### Responsibilities:

- Merges metadata snapshots
- Helps recovery process

---

## HDFS Storage Concept

### Block Storage

Files are divided into blocks.

### Example

500 MB file with 128 MB block size:

| Block | Size |
|---|---|
| Block 1 | 128 MB |
| Block 2 | 128 MB |
| Block 3 | 128 MB |
| Block 4 | 116 MB |

---

## HDFS Replication

**Default Replication Factor = 3**

Each block stored on 3 different DataNodes.

### Benefits

- High availability
- Data recovery
- Fault tolerance

---

## HDFS Read Operation

### Steps

1. Client requests file
2. NameNode returns block locations
3. Client reads from nearest DataNode

---

## HDFS Write Operation

### Steps

1. Client contacts NameNode
2. NameNode allocates DataNodes
3. Data written to DataNodes
4. Replication occurs automatically

---

## Advantages of HDFS

- Handles huge datasets
- Reliable storage
- Supports parallel access
- Cheap commodity hardware

---

## Limitations of HDFS

- Not suitable for small files
- High latency
- NameNode bottleneck
- Not ideal for real-time systems

---

# PART 3 — HDFS Commands & Processing

**Duration:** 20 Minutes

---

## Basic HDFS Commands

### 1. List Files

```bash
hdfs dfs -ls /
