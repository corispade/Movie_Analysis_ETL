# Movies_ETL

# Overview

Amazing Prime loves the dataset and wants to keep it updated on a daily basis. Britta needs your help to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables. You’ll need to refactor the code from this module to create one function that takes in the three files—Wikipedia data, Kaggle metadata, and the MovieLens rating data—and performs the ETL process by adding the data to a PostgreSQL database.

## Process:

### Deliverable 1: Write an ETL Function to Read Three Data Files
* Write an ETL function that reads in the three data files 
* Function converts Wiki JSON file to a Pandas DataFrame
* Function converts Kaggle metadata file to a Pandas DataFrame
* Function converts MovieLens ratings data file to a Pandas DataFrame

### Deliverable 2: Extract and Transform the Wikipedia Data
* Add a "clean_movie" function that cleans the column names and merges duplicate columns
* Add a "extract_transform_load" function that cleans the wikipedia data set
 - Read in the data
 - Filter out the TV shows
 - Call the clean_movie function on each movie
 - Read in the cleaned movies
 - Create DataFrame from the cleaned movies
 - Write try/except block to extract IMDB ID to strings, drop duplicates, and run an except statement to skip errors
 - Keep columns that don't have null values in the DataFrame
 - Clean "box office" column: Convert to strings, write a parse_dollars function to match strings otherwise return nan
 - Clean "budget" column: Convert to strings, use regular expression to match common budget forms, extract those values
 - Clean "release date" column: Convert to strings, use regular expression to match common date forms, use datetime function to parse the dates, extract the dates.
 - Clean "running time" column: Convert to strings, extract the values, convert strings to numeric values, apply a function that converts hour and minute capture groups
 - Review the cleaned DataFrame

### Deliverable 3: Extract and Transform the Kaggle data
* Add a "clean_movie" function that cleans the column names and merges duplicate columns
* Add a "extract_transform_load" function that cleans the wikipedia data set, kaggle metadata and ratings data set
 - Wikipedia data set cleaned in deliverable 2
 - Clean Kaggle metadata
 - Merge Kaggle metadata and Wikipedia data into one DataFrame
 - Clean merged dataframe by filling in missing values and dropping duplicate columns
 - Rename and reorder columns to clean the look
 - Transform the ratings data
 - Merge ratings data with the combined Kaggle and Wikipedia DataFrame
 - Fill in all missing values with "0"

### Deliverable 4: Create the Movie Database

## Resources:
Sources: wikipedia-movies.json, movies_metadata.csv, ratings.csv

Software: Python 3.7.6, Conda 4.10.1

Environment: Jupyter Notebook

Dependencies: json, pandas, numpy, re, sqlalchemy, psychopg2, time


# Results:



# Summary:
