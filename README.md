# YouTube Trends Analysis ETL using AWS

> In this project, I evaluated and prepared Kaggle's Trending YouTube Video Statistics data for use.

## 📕 Table Of Contents
* [Introduction](#-introduction)
* [Project Datasets](#-project-datasets)
* [Project Files](#-project-files)
* [Project Steps](#-project-steps)
* [Tools and Technologies](#-tools-and-technologies)
* [Resources](#-resources)  
---

## 🪄 Introduction

Many problems exist when deploying or transferring analytics to the cloud. Differences in features between on-premises and cloud data platforms, security, and governance are all technical concerns. The danger of moving on-premises data into the cloud has prompted organizations to limit cloud analytics initiatives, especially in regulated industries where data protection is crucial. 
This project aims to securely manage, streamline, and perform analysis on the structured and semi-structured YouTube videos data based on the video categories and the trending metrics.

> Data Flow Architecture
<p align="center">
  <img width=100% height=100%" src="/imgs/Data-Flow-Architecture.png">

---

## 💿 Project Datasets:

* [Trending YouTube Video Statistics](https://www.kaggle.com/datasets/datasnaek/youtube-new)

---


## ⚡ Project Steps

- 1 - Uploading data from a local machine to an S3 bucket using AWS CLI commands while attempting to keep file organization. Separate folders were created for the JSON and CSV files.
> s3_cli_commands.sh
- 2 - Using AWS Glue Catalog to crawl data from raw bucket JSON and CSV files, which will be stored in a separate database.
- 3 - If problems arise as a result of data in JSON format, write a Python function using AWS Lambda to clean them up and convert them to parquet format.
> lambda_function.py
- 4 - Adding a trigger to this Lambda function to run whenever new data is added to the S3 bucket, and the output was saved in a new database in Athena.
- 5 - Using AWS Glue ETL, I converted the CSV files to parquet format as well.
> ETL_clean_data.py
<p align="center">
  <img width=40% height=40%" src="/imgs/ETL-Cleaning.png">

- 6 - Creating a new Glue Crawler to crawl the clean data into the database.
- 7 - After all of the clean data from the parquet files (converted from CSV and JSON files) is in the same database, create an ETL job in AWS Glue Studio to join both tables and store it in a separate S3 bucket for BI purposes.
> ETL_joining_data.py
<p align="center">
  <img width=40% height=40%" src="/imgs/ETL-Joining_Data.png">

- 8 - The data is now ready to be used for building dashboards out of it.

---

## 📚 Project Files:

- ```s3_cli_command.sh``` AWS cli commands to upload the raw data into S3 Bucket
- ```lambda_function.py```AWS lambda function to convert JSON into PARQUET format
- ```ETL_clean_data.py``` ETL script to clean data and apply mapping transformation into them
- ```ETL_joining_data.py``` ETL script to join both tables and storing it in a separate S3 bucket

---

## 🔧 Tools and Technologies:
- Python 3.
- SQL.
- AWS S3, AWS Glue, QuickSight, AWS Lambda, AWS Athena, AWS IAM

----

## 📜 Resources
* [Kaggle Dataset](https://www.kaggle.com/datasets/datasnaek/youtube-new)
* [YouTube Data Analysis | END TO END DATA ENGINEERING PROJECT](https://www.youtube.com/watch?v=yZKJFKu49Dk&list=PLBJe2dFI4sguF2nU6Z3Od7BX8eALZN3mU&ab_channel=DarshilParmar)

---
## ✨ Contribution

Contributions, issues, and feature requests are welcome!

To contribute to this project, see the GitHub documentation on **[creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)**.

---

## 👏 Support

Give a ⭐️ if you like this project!
___________________________________

<p>&copy; 2022 Ahmed Ashraf</p>