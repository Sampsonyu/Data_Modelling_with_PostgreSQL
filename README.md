# Data-Modeling-with-Postgres

## Introduction
A startup called `Sparkify` wants to analyze the data they've been collecting on songs and user activity on their new `music streaming app`. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a **Postgres database** with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a **database schema** and **ETL pipeline** for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Project Description
In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. 
To complete the project, you will need to 
* Define fact and dimension tables for a star schema for a particular analytic focus
* Write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL

## File Overview
- `data/song_data/` - contains our song data in json format. files are partitioned by the first three letters of each song's track ID
- `data/log_data/` - contains our user activity logs in json format. files are partitioned by year and month
- `sql_queries.py` - states all of our SQL queries for: droping tables, creating tables, inserting rows, and a query for finding song_id, artist_id given a song name, artist name, and song duration
- `create_tables.py` - Python script that drops and then creates our tables.
- `etl.py` - Our ETL pipeline. Iterates through our song and log files and pipes the data into our database tables.
- `test.ipynb` - Runs SQL queries to check the first few values of each of our database tables.
- `etl.ipynb` - Exploratory work that can be used to look at our json files and test various etl approaches for getting data from the json files into our databases

Be sure to close all database connections and run `create_tables.py` before running `etl.py` or `etl.ipynb`. 

After Running either of those etl files, you can run `test.ipynb` to check the values of each of our database tables.

## The Data Model: Star Schema

![Star Schema](star_schema.png)

For the sake of our Data Scientists, we've decided to use a Star Schema data model. The Star Schema is a subset of the concept of "fact and dimension tables". In our case, the Fact Table is `songplays` and our Dimension Tables are `users`, `songs`, `artists`, and `time`. 
