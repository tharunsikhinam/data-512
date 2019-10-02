## A1: Data Curation

The goal of this project is to construct, analyze and publish a dataset of monthly traffic on Wikipedia from January 1st 2008 to August 30 2019. 
The project aims to follow the best practices for conducting open scientific research focussing on repoducibility.

The project documents the following steps
1) Data Acquisition
2) Data Processing
3) Data Analysis

The above three steps can be found in this [IPython notebook](./data-512-a1/hcds-a1-data-curation.ipynb) 
Running the above notebook 

### Folder Structure

```
```

All the raw data is stored under data/raw and the cleaned data in stored under data/clean
Analysis is done in data-512-a1/hcds-a1-data-curation.ipynb notebook

### Data

#### Source
The data is collected from Wikimedia REST API's. 
1) The Legacy Pagecounts API (documentation, endpoint) provides access to desktop and mobile traffic data from December 2007 through July 2016.
2) The Pageviews API (documentation, endpoint) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

### License and Terms of Use

### Data Decription

The final cleaned data is stored in data/clean/<filename>
The columns in the file represent the following

### Methodology

#### Data Acquisition
Data is collected by making API requests to Wikimedia endpoints and storing this JSON information files. Data is collected separately for desktop and mobile views

#### Data Processing
As part of the processing steps the desktop and mobile views are combined to get the total number of views for both Pagecounts and Pageviews. Data is merged from all the sources and combined into a final file as described above

#### Data Analysis
To analyse the data, we are plotting a line graph from January 1st 2008 to August 30 2019 with different lines and colors representing the number of views

<attach figure here>
  
To perform the above steps the following Python libraries were used
1) requests - To perform API requests
2) pandas - Python data processing library
3) matplotlib - Data plotting tool 


### Data Caveats

The legacy API doesn't differentiate between organic traffic and others (web crawlers). The number of pageviews may be inflated.

