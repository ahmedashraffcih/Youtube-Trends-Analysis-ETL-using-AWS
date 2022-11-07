# YouTube Trends Analysis ETL using AWS
> This repository contains all of my code for Sparkify - Data Modeling with Postgres project (Udacity Data Engineering Expert Track)
>
> In this project, I created a Postgres database with fact and dimension tables for a star schema for a specific analytic focus, which is to analyse Sparkify's collected data on songs and user activity on their new music streaming app. Then, using Python and SQL, I created an ETL pipeline that transfers data from JSON files in two local directories into these tables in Postgres.

## 📕 Table Of Contents
* [Introduction](#-introduction)
* [Project Description](#-project-description)
* [Project Datasets](#-project-datasets)
* [Database Schema](#-database-schema)
* [Prerequisites](#-prerequisites)
* [Project Files](#-project-files)
* [Project Steps](#-project-steps)
* [Tools and Technologies](#-tools-and-technologies)
* [Resources](#-resources)  
---

## 🪄 Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

---

## 📝 Project Description

In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

---

## 💿 Project Datasets:

- https://www.kaggle.com/datasets/datasnaek/youtube-new

![log-data](https://user-images.githubusercontent.com/46838441/191114096-960d74b7-2745-4006-bef7-b5f616e1113f.png)

---

## 🗺️ Database Schema

After examining the Log and Song JSON files, I created a Star schema (shown below) that include one Fact table (songplays) and 4 Dimension tables.

- Fact Table
  - ```songplays``` records in log data associated with song plays i.e. records with page 'NextSong'
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent.
- Dimension Tables
  - ```users``` users in the app
    - user_id, first_name, last_name, gender, level
  - ```songs``` songs in music database
    - song_id, title, artist_id, year, duration
  - ```artists``` artists in music database
    - artist_id, name, location, latitude, longitude
  - ```time``` timestamps of records in songplays broken down into specific units
    - start_time, hour, day, week, month, year, weekday

<img src="erd-diagram.png" alt="ERD Diagram" width="800"/>

---

## 🚧 Prerequisites

This project makes the folowing assumptions:

* Python 3 is available
* `pandas` and `psycopg2` are available
* A PosgreSQL database is available on localhost

---

## 📚 Project Files:

- ```test.ipynb``` displays the first few rows of each table to check the database.
- ```create_tables.py```drops and creates the database and its tables.
- ```etl.ipynb``` reads and processes a single file from song_data and log_data and loads the data the tables.
- ```etl.py``` reads and processes files from song_data and log_data and loads them into the tables.
- ```sql_queries.py``` contains all sql queries.

---

## ⚡ Project Steps
> NOTE: You will not be able to run test.ipynb, etl.ipynb, or etl.py until you have run create_tables.py at least once to create the sparkifydb database, which these other files connect to.

- 1 - Create database star schema optimized for queries on song play analysis.
- 2 - Prepare the SQL queries: create, drop, and select statements that you will use.
> sql_queries.py
- 3 - Create the Postgres database.
> Remember that you have to change connection credentials in project files (change user and password).
```
conn = psycopg2.connect("host=127.0.0.1 dbname=sparkifydb user=postgres password=123456")
```
- 4- Develop the ETL process.
> etl.ipynb
- 5- Build ETL Pipeline.
> Use what you've completed in `etl.ipynb` to complete `etl.py`
>
> Remember to run `create_tables.py` before running `etl.py` to reset your tables
- 6- Test the results.
> test.ipynb

---
## 🔧 Tools and Technologies:
- Python 3.
- PostgreSQL server.
- SQL.
- Jupyter Notebook.
- Pandas, NumPy, Psycopg2 Python Libraries.

----

## 📜 Resources
* [data-modeling-with-postgres](https://github.com/christophersmith/data-modeling-with-postgres)
* [Sparkify---Data-Modeling-with-Postgres](https://github.com/Dina-Hosny/Sparkify---Data-Modeling-with-Postgres)

---
## ✨ Contribution

Contributions, issues, and feature requests are welcome!

To contribute to this project, see the GitHub documentation on **[creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)**.

---

## 👏 Support

Give a ⭐️ if you like this project!
___________________________________

<p>&copy; 2022 Ahmed Ashraf</p>