### the_future_is_now

<img src="https://github.com/Cabone01/the_future_is_now/blob/main/RawData/thefutureisnow.png" width="600">

## Contents
This repository contains the following files

- Raw Data Folder: This folder contains the Raw CSV files and the raw scraping from our two data sources
    -Scraping Website.ipynb: This our web scrape for data from Boxofficemojo.com
    -Box_office_mojo_movies.CSV: This is our CSV file of data from Boxofficemojo.com
    -themoviedb_api_pull.scifi.csv: This is our CSV file of data pulled from The Movie Database API

-MongoUpload.ipynb: This is the final Jupyter notebook of our combined above datasets that is uploaded to our Mongo Database

-themoviedb_api_pull.ipynb: This is the API pull from The Movie Database API

-config.py: This is where the API key is held for the above API

## Objective
A Hollywood producer came to our firm to find out if it was a worthwhile investment to make his Science Fiction Movie based on the recent worldwide top gross earnings report.

# Extraction of Data
First, we identified our data sets and sources that we wanted to use. We chose Box Office Mojo and The Movie Database in order to get comprehensive info.
    -Box Office Mojo: From Box Office Mojo we were able to get financial data for the Worldwide Box office which includes datapoints such as:
        -Worldwide Lifetime Gross Earnings
        -Domestic Lifetime Gross Earnings
        -Domestic Percentage of Earnings
        -Foreign Lifetime Gross Earnings
        -Foreign Percentage of Earnings
        -Year when movie was released

    -The Movie Database API:
        -Title of movie
        -Number of votes from users of The Movie Database API
        -Average score of total votes from users on a 0 to 10 scale with 0 representing 0% and 10 representing 100%
        -The Original Language the movie was filmed in
        -Genre ID for Science-Fiction movies (878)

Next, we created our Jupyter Notebooks in order to extract the above data into. The Box Office Mojo information was pulled in as a web scrape while the The Movie Database API was an API we were able to pull from.

# Transforming the Data
We then cleaned up our respective data sources before adding to a CSV
    - For the Box Office Mojo data we did the following:
        -Created a dictionary for the data
        -Removed all non-numerical values ($, <,>, -, %)
        -Set the Dollar values as type floats
        -Set the percentages as type floats
        -Changed the movie name field to match the Movie Database API field

    - For the Movie Database API we did the following:
        -Queried API to find ids for each genre in the API and pinpoint the ID tag for Science-Fiction movies
        -Created API for Science-Fiction movies only
        -Created a For loop to go through each page (1-775)
        -Created a nested For loop to get each movies field.
        
We then joined these two data sources together and merged by using the Title Field in both datasets. We then dropped any duplicates from our new data frame and reset the index because of the duplicates that we had removed. Finally, we aggregated the data into a new dictionary.

# Loading the Data
We inserted the final data set into our Mongo Production Database.

# Additional Work Done
Some examples of additional work that was done but not shown in our final production database
    -Brainstorming! firm name, objective, and the importance of data science to this industry
    -Pulled a public CSV file for DC and Marvel movies specifically
        -We chose not to use this because of how small the data set was.
    -Looked at other data sources such as Rotten Tomatoes, Meta Critic, IMDB, and OMDB API
    
