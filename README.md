# Data Engineering YouTube Trending Video Data

## Overview
This project involes the storage, cleaning, and management of data regarding trending Yourtube videos from various countries including view counts, like counts, categories, region, etc.
After performing various operations on the data, we make a dashboard helping us visualize and make inferences from the data.

## Project Goals
1. Data Ingestion — Build a mechanism to store data from different sources
2. ETL System — Transforming and performing operations on raw data
3. Data lake — Storing data from multiple sources in a centralized location
4. Scalability — Designing our system to remain functional as more or less data is added or removed
5. Cloud — Using AWS cloud storage systems to store large amounts of data we couldn't on our local computer
6. Reporting — Design a dashboard to answer particular questions about the data

## Technologies Used
1. Amazon S3: Scalable storage infrastructure offered by AWS prioritizing data availability, security, and performance
2. AWS IAM: Identity and Access Management which enables us to manage access to AWS services and resources securely
3. Amazon QuickSight: Scalable, cloud-based, machine learning-powered business intelligence service
4. AWS Glue: Serverless data integration service that allows us to discover and transform data for analytics, machine learning, and application development
5. AWS Lambda: Allows programmers to run code on stored data without creating or managing servers
6. AWS Athena: Interactive query service for S3 data

## Dataset Used
Dataset contains CSV files with statistics on trending YouTube videos over the course of many months. There are up to 200 trending videos published every day for many locations. The data for each region is in its own file. The video title, channel title, publication time, tags, views, likes and dislikes, description, and comment count are among the items included in the data. A category_id field, which differs by area, is also included in the JSON file linked to the region.

https://www.kaggle.com/datasets/datasnaek/youtube-new

## Architecture Diagram
Step by Step Overview:
1. Store imported dataset into S3 buckets
2. Build Glue Crawler to create data schema (metadata) for use in future operations
3. Create ETL Job, Lambda Function to clean data and deposit data in another S3 bucket
4. Build Glue Crawler to created schema for cleaned data
5. Build ETL Job to convert cleaned csv data to parquet files
6. Write Lambda function to clean and convert any new data added to the S3 buckets
7. Build final ETL Job to join cleaned data and store in a final S3 bucket
8. Create dashboards with Amazon Quicksight using data generated from last step

<img src="architecture.jpeg">

## Dashboard
Questions/considerations when making the dashboard:
- What are the most important categorical and numerical data we should consider?
- How much does each region view, like, and comment on trending videos of various categories?
- Which trending video categories have the highest views, likes, dislikes, and comments across multiple regions?
- What correlation might data like like counts and comment counts have per category of video?
