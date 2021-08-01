# Extract, Transform and Load

# Overview

Developing an algorithm for Amazing Prime to predict which low budget movies being release will become popular so that they can buy the streaming rights at a bargain. We refactored code to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables. We created one function that takes in three files (Wikipedia data, Kaggle metadata, and the MovieLens rating data) and performs the ETL process by adding the data to a PostgreSQL database.

## Process:

### Deliverable 1: Write an ETL Function to Read Three Data Files
Find code [here](https://github.com/corispade/Movies_ETL/blob/main/ETL_function_test.ipynb).
* Write an ETL function that reads in the three data files 
* Function converts Wiki JSON file to a Pandas DataFrame
* Function converts Kaggle metadata file to a Pandas DataFrame
* Function converts MovieLens ratings data file to a Pandas DataFrame

### Deliverable 2: Extract and Transform the Wikipedia Data
Find code [here](https://github.com/corispade/Movies_ETL/blob/main/ETL_clean_wiki_movies.ipynb).
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
Find code [here](https://github.com/corispade/Movies_ETL/blob/main/ETL_clean_kaggle_data.ipynb)
* Add a "clean_movie" function from deliverable 2
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
Find code [here](https://github.com/corispade/Movies_ETL/blob/main/ETL_create_database.ipynb)
* Add a "clean_movie" function from deliverable 2
* Add a "extract_transform_load" function from deliverable 3
* Connect to postresql database
* Import movie_df to sql
* Import ratings data to sql by chunk size and indicating time elapsed for importing data
* Use PgAdmin to confirm data has been loaded to the database
  - [movies_query](https://github.com/corispade/Movies_ETL/blob/main/movies_query.png) count = 6,052
  - [ratings_query](https://github.com/corispade/Movies_ETL/blob/main/ratings_query.png) count = 26,024,289

## Resources:
Sources: wikipedia-movies.json, movies_metadata.csv, ratings.csv

Software: Python 3.7.6, Conda 4.10.1

Environment: Jupyter Notebook

Database System: Postgres Version 12.7
* Interface: PgAdmin Version 5.2
* Language: SQL