## A2: Bias in Data

The goal of this assignment is to undestand the concepts of bias by exploring data on Wikipedia articles. We are going to be particularly looking at articles on polictal figures from various countries. This is combined with the dataset of country populations and a machine learning service ORES to used to estimate the quality of the article.

With this combined data, we conduct the following analysis
- Find countries with the greatest and least coverage of politicians on Wikipedia compared to population
- countries with highest and lowest proportion of high quality articles
- rank geographic regions by articles per person and proportion of high quality articles

Data acquisition, processing and analysis steps are all recorded in this IPython Notebook

## Data

The data is obtained from multiple sources as listed below.

Wikipedia politicians by country dataset - page_data.csv

  
  | Column  | Description  
|--------------|------------- 
| page | Title of the wikipedia article
| country | country of origin
| rev_id | revision id of the article

Population data - This data is obtained form the world population datasheet published by the Population Reference bureau WPDS_2018_data.csv


  | Column  | Description  
|--------------|------------- 
| Geography | Country or region
| Population mid-2018 (millions) | population in millions

ORES Objective Revision Evaluation Service is used to estimate theq uality of an article. We make RESTful API calls to this service to find out the quality of Wikipedia articles


  | Column  | Description  
|--------------|------------- 
| rev_id | rev_id of the wikipedia article
| ratings | ratings as defined below

## Data Processing

We obtain the population and wikipedia datasets from the links provided above.

To assign a quality score to each article we make API calls to ORES in Python

#### Combining datasets

Countries with no matching Wikipedia articles are stored in 
wp_wpds_Countries-no_match.csv

wp_wpds_policticans_by_country.csv

The csv schema is as follows

