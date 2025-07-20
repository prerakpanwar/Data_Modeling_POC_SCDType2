# Data_Modeling_POC_SCDType2

## SCD Type 2 Implementation in PySpark

## Problem Statement
In data warehousing and analytics, tracking historical changes in dimension data is crucial for accurate reporting and analysis. Traditional approaches that simply overwrite existing records lose valuable historical context. We need a solution that:

-Preserves complete history of dimension changes
-Allows analysis of data "as of" any point in time
-Efficiently identifies changed records in large datasets
-Maintains referential integrity while updating dimensions

## Use Case
A organization maintains employee data in a data warehouse

Business needs require tracking all historical changes to employee records (salary changes, department transfers, etc.)

Current implementation overwrites records, losing historical context

Need to implement SCD Type 2 to preserve complete change history

## Task
Design and implement a PySpark-based SCD Type 2 solution that:

-Detects changes between source and target data
-Creates new versions for changed records
-Maintains validity time periods (valid_from/valid_to)
-Flags active records appropriately
-Handles new records and updates efficiently

## Action
Data Setup

-Created sample source and target DataFrames with employee data
-Established proper date formatting for validity tracking

Change Detection
-Implemented xxhash64 hashing for efficient record comparison
-Used left anti joins to identify new/changed records

Version Management
-Applied window functions (row_number, lag) for version tracking
-Developed logic to update validity windows and active flags
-Implemented proper merging of new and existing records

Validation (Verified correct handling of):
-New records (inserts)
-Changed records (updates with history preservation)
-Unchanged records (no action needed)

## Result

-Successful implementation of SCD Type 2 in PySpark
-Complete historical tracking of employee dimension changes
-Efficient processing through hash-based change detection
-Clear validity dating and active record identification
-Ready-to-use template for production implementation

# Solution Overview
This repository contains a proof-of-concept implementation of Slowly Changing Dimension (SCD) Type 2 using PySpark. SCD Type 2 is a data warehousing technique that tracks historical changes by creating new records for changed data while maintaining the previous versions.

# Key Features

-Demonstrates a complete SCD Type 2 pipeline from source to target
-Uses hash comparison (xxhash64) to efficiently detect changes
-Handles new records, updates, and maintains historical versions
-Implements proper validity dating (valid_from/valid_to) and active flags
-Uses window functions for efficient version management

