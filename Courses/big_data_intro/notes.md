---
layout: page
title: Big Data: The Big Picture Notes
permalink: /Courses/big_data_intro
---

# This course is a Pluralsight course taught by Andrew J. Brust.

## Big data defined

  - Big data can be defined by projects using 100s of terabytes of data and more.
  - Big data uses Hadoop for analytics.
  - The Three V's of big data are volume(amount of data), velocity(how quickly data is arriving), and variety(the structure of the data)
  - Big data projects are usually using amounts of data that are too large for operational databases to handle.
  - Big data projects also typically use distributed/parallel processing

## MapReduce

- MapReduce is an algorithmic approach to dealing with big data. It is a process to take a large amount of data, separate that data into small batches, and then perform analytics on those small batches.
- Google was the first company to create MapReduce and publish a paper on it. Then others create several open source versions, one of the most popular is Hadoop.
- MapReduce is a two pass process. The first pass is the **Map step**, which splits up the data and performs pre-processing on the smaller batches. The Map step also outputs data in a key-value format that is sorted by the key. The second step is the **Reduce step**, which receives the output of the Map step and aggregates the data. This means it condenses all the data entries for a specific key from the Map step and outputs a single data entry per key.

## Hadoop

- Hadoop is an Apache project which combines MapReduce with a distributed file system(HDFS)
- HDFS(Hadoop File System) allows for the local discs on individual nodes in a Hadoop cluster to operate as a single pool of storage.
- Files cannot be updated in HDFS.
- The Hadoop Stack(Bottom to top)
  - MapReduce,HDFS -> Database -> Query Language -> RDBMS -> Machine Learning / Data Mining -> Log File Integration
- Hive is a SQL-like abstraction over MapReduce. It has it's own HDFS table format and can act as a bridge to many BI products.

## Massively Parallel Processing(MPP)

- Splits up query work into sub-queries and distributes them over nodes in a cluster.
- Uses SQL typically
- Returns a single result set and packaged as physical appliances
- Often combined with column store technology

## NoSQL databases

- NoSQL databases are used for storing unstructured and semi-structured data
- They sacrifice database consistency for ease of partitioning/clustering
- There are 4 types: key-value stores, document stores, graph databases, and wide column/column family stores
- **CAP Theroem** - ![CAP Theroem](/resources/images/bigdata/CAPTheroem.PNG)

## NewSQL

- NewSQL databases challenge the dichotomy of the CAP theorem:
  - Schema-free storage and availability
  - Relational and consistent
  - Acknowledges value and prevalence of SQL skillsets

## HDFS Challenges

- Availability - Name node is single point of failure, even with Warm standby
- Manageability - Direct attached storage are hard to manage
- Enterprise readiness - Most enterprises have investments in networked storage
- Cost inefficiencies - HDFS replication creates three instances of everything by default
- The solution - Swap HDFS with an API-compatible, enterprise alternative.
