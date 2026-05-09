# How Files Are Stored in HDFS

## Course

Big Data / Hadoop

---

## Audience

Students of:

- Computer Science
- Information Technology
- Data Science
- Big Data Analytics

---

# Learning Objectives

By the end of this lecture, students will be able to:

- Understand HDFS fundamentals
- Explain how files are stored in HDFS
- Understand blocks and replication
- Explain NameNode and DataNode roles
- Understand HDFS write and read operations
- Understand fault tolerance in HDFS
- Explain HDFS architecture workflow
- Perform basic HDFS file operations

---

# Lecture Outline

| Section | Topic |
|---|---|
| 1 | Introduction to HDFS |
| 2 | HDFS Architecture Overview |
| 3 | HDFS Storage Concepts |
| 4 | How Files Are Written in HDFS |
| 5 | How Files Are Read from HDFS |
| 6 | Replication & Fault Tolerance |
| 7 | HDFS Commands Demonstration |
| 8 | Advantages & Limitations |
| 9 | Activity / Discussion |
| 10 | Quiz & Conclusion |

---

# PART 1 — Introduction to HDFS

## Opening Questions

Ask students:

- Can one computer store petabytes of data?
- What happens if a storage server crashes?
- How does Hadoop store huge files safely?

---

# What is HDFS?

HDFS stands for:

> Hadoop Distributed File System

It is Hadoop’s storage system designed for:

- Large files
- Distributed storage
- Fault tolerance

---

# Why HDFS Was Created

Traditional file systems face problems:

- Limited storage
- Single point of failure
- Poor scalability

HDFS solves these using:

- Distributed storage
- Replication
- Cluster computing

---

# Key Features of HDFS

- Distributed storage
- Fault tolerance
- Scalability
- High throughput
- Data replication

---

# PART 2 — HDFS Architecture Overview

# Main Components of HDFS

# 1. NameNode (Master Node)

Responsible for:

- Metadata management
- File system namespace
- Block location tracking

---

# 2. DataNode (Slave Nodes)

Responsible for:

- Storing actual data blocks
- Reading and writing data

---

# 3. Client

User or application interacting with HDFS.

---

# Simple Architecture Diagram

Draw on board or slides:

Client → NameNode → DataNodes

---

# Important Point

NameNode stores metadata only.

## Metadata Includes

- File names
- Permissions
- Block locations

DataNodes store actual data.

---

# PART 3 — HDFS Storage Concepts

# 1. File Splitting into Blocks

Large files are divided into smaller blocks.

---

## Example

Suppose:

- File size = 500 MB
- Block size = 128 MB

The file is divided into multiple blocks.

---

# Why Block Storage?

## Advantages

- Parallel processing
- Distributed storage
- Faster access

---

# 2. Block Size

Default HDFS block size:

> 128 MB (common)

Can be configured.

---

# 3. Replication

Each block is copied multiple times.

## Default Replication Factor

> 3

---

## Example of Replication

### Block A

- Copy 1 → DataNode 1
- Copy 2 → DataNode 2
- Copy 3 → DataNode 3

---

# Why Replication?

Provides:

- Fault tolerance
- Data availability
- Reliability

---

# 4. Rack Awareness

HDFS stores replicas across different racks.

## Purpose

Prevent data loss during rack failure.

---

# PART 4 — How Files Are Written in HDFS

# HDFS Write Operation

Explain step-by-step.

---

# Step 1 — Client Sends Request

Client requests NameNode to store file.

### Example

```bash
upload data.csv
