---
layout: page
title: Big Data: The Big Picture Notes
permalink: /Courses/BigData/
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
- MapReduce is a two pass process. The first pass is the **Map step**, which splits up the data and performs pre-processing on the smaller batches. The Map step also outputs data in a key-value format that is sorted by the key. The second step is the **Reduce step**, which receives the output of the Map step and aggregates the data. This means it condenses all the data entries for a specific key from the Map step and outputs a single data entry per key.
