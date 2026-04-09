---
layout: post
title: "Duckdb Basic"
date: 2026-04-08
categories: practice
tags: [duckdb, olap]
---

## Overview
This post covers the basic concepts of DuckDB and the reasons behind its
popularity. It is based on my review of DuckDB blog post, ["Why
DuckDB?"](https://duckdb.org/why_duckdb).

## Why DuckDB?
### DuckDB is fast
DuckDB is an **OLAP-centered database** using SQL. OLAP stands for Online Analytical
Processing, which focuses on data analysis and data science rather than just
inserting or deleting records. It excels at analyzing databases through
operations like aggregation and filtering.

People choose DuckDB for OLAP primarily because it is incredibly fast. But how
exactly does it achieve this speed? These are what I have understood so far.

#### Columnar Storage 
DuckDB stores data **column-wise** rather than the row-wise format typically
observed in traditional table storage. Usually, when we analyze a database, we
apply aggregations like:
``` sql
SUM(Salary)
```
This means we only need to consider a single column rather than entire rows.
Column-wise storage directly supports this feature of OLAP, making the whole
process much faster.
 
#### DuckDB has no server

Traditional databases like PostgreSQL always require a server to be running.
When you download PostgreSQL and start the program, it asks for a port and a
server address (such as localhost). This is for several reasons, one of which is
concurrency control, allowing multiple people to access the data at the same
time. Another reason is the ability to use high-performance computers or the
cloud as servers, as handling many transactions simultaneously is heavy
computing work that a typical laptop might not manage. In this setup, the server
handles the work, and we act as the client.

However, since DuckDB is an OLAP database, we often don't need this server
because we are less concerned with heavy concurrency control. One thing to note
is that this also means DuckDB isn't primarily built for BIG data in the same
way because it doesn't use a server, it depends on the user's local environment.
To address this, DuckDB developers provide cool algorithms like Out-of-core
Processing and leverage MotherDuck, the cloud version of DuckDB. Of course, for
massive amounts of data, Apache Spark, Google BigQuery, or Snowflake are still
used for OLAP jobs. 

#### Convenient file process
My experience is heavily centered on OLTP, such as PostgreSQL. In that
environment, we usually had to load a CSV file into the database first and then
run SQL queries. However, with DuckDB, users can easily run SQL queries directly
on CSV files without moving them into the database.

---

*Next Steps*

- Execute simple queries over DuckDB in Python
- Deep dive into the core algorithms (e.g., Vectorized Execution, Out-of-core Processing)