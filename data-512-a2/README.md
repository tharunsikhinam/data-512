## A2: Bias in Data

The goal of this assignment is to undestand the concepts of bias by exploring data on Wikipedia articles. We are going to be particularly looking at articles on polictal figures from various countries. This is combined with the dataset of country populations and a machine learning service ORES to used to estimate the quality of the article.

With this combined data, we conduct the following analysis
- Find countries with the greatest and least coverage of politicians on Wikipedia compared to population
- countries with highest and lowest proportion of high quality articles
- rank geographic regions by articles per person and proportion of high quality articles

Data acquisition, processing and analysis steps are all recorded in this [IPython Notebook](./hcds-a2-bias.ipynb)

## Directory Structure

```
.
├── README.md
├── clean
│   ├── articles_no_ratings.csv
│   ├── wp_wpds_countries-no_match.csv
│   └── wp_wpds_politicians_by_country.csv
├── hcds-a2-bias.ipynb
└── raw
    ├── WPDS_2018_data.csv
    ├── WPDS_2018_data_continents.csv
    ├── ores_data.csv
    └── page_data.csv
```


## Data

The data is obtained from multiple sources as listed below.

1. Wikipedia politicians by country dataset is stored at [raw/page_data.csv](./raw/page_data.csv)

Wikipedia articles data is found at this https://figshare.com/articles/Untitled_Item/5513449. The data contains articles of political figures by country. It is titled page_data.csv. The data is licensed under CC-BY 4.0 license.  
  
  | Column  | Description  
|--------------|------------- 
| page | Title of the wikipedia article
| country | country of origin
| rev_id | revision id of the article

2. Population data is stored at [raw/WPDS_2018_data.csv](./raw/WPDS_2018_data.csv)

The population data contains world populations for 207 countries as of 2018. The data was provided to us as part of the assignment. This data is obtained form the world population datasheet published by the Population Reference bureau. There is no License attributed to this data, by default all rights are reserved to the owners of this data.

  | Column  | Description  
|--------------|------------- 
| Geography | Country or region
| Population mid-2018 (millions) | population in millions


3. Population data with continents  [raw/WPDS_2018_data_continents.csv](./raw/WPDS_2018_data_continents.csv)

This dataset is an extension of the previous one, a new column continent is added and this is tagging is done manually on Excel

  | Column  | Description  
|--------------|------------- 
| Geography | Country or region
| Population mid-2018 (millions) | population in millions
| continent | region the country belongs to


4. ORES ratings  

Objective Revision Evaluation Service is used to estimate the quality of an article. The documentation for ORES API can be found at https://www.mediawiki.org/wiki/ORES.  We make RESTful API calls to this service to find out the quality of Wikipedia articles and store this data in [raw/ores_data.csv](./raw/ores_data.csv)

  | Column  | Description  
|--------------|------------- 
| rev_id | rev_id of the wikipedia article
| ratings | ratings as defined below

The ratings of the articles are classified below from high quality to low

FA - Featured article

GA - Good article

B - B-class article

C - C-class article

Start - Start-class article

Stub - Stub-class article

## Data Processing

As part of the data processing step we perform the following operations

1. Merge ores ratings and wikipedia articles dataset
2. Combine wiki ratings and country data
3. Clean up the merged data

The final data is stored as 

### Final Dataset

The final dataset is found at [here](./clean/wp_wpds_politicians_by_country.csv)

| Column          | Description                                     |
| --------------- | ----------------------------------------------- |
| country         | country name                       |
| article_name    | article name                |
| revision_id     | revision id of the article                  |
| article_quality | quality score obtained from ORES API |
| population      | The population of the country.                  |
|                 |                                                 |

## Data Analysis

We perform the following analysis and report the results:

1. Top 10 countries by coverage: 10 highest-ranked countries in terms of number of politician articles as a proportion of country population

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>population</th>
      <th>total_articles</th>
      <th>coverage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>166</th>
      <td>tuvalu</td>
      <td>10000</td>
      <td>54</td>
      <td>0.540000</td>
    </tr>
    <tr>
      <th>115</th>
      <td>nauru</td>
      <td>10000</td>
      <td>52</td>
      <td>0.520000</td>
    </tr>
    <tr>
      <th>135</th>
      <td>san marino</td>
      <td>30000</td>
      <td>81</td>
      <td>0.270000</td>
    </tr>
    <tr>
      <th>108</th>
      <td>monaco</td>
      <td>40000</td>
      <td>40</td>
      <td>0.100000</td>
    </tr>
    <tr>
      <th>93</th>
      <td>liechtenstein</td>
      <td>40000</td>
      <td>28</td>
      <td>0.070000</td>
    </tr>
    <tr>
      <th>161</th>
      <td>tonga</td>
      <td>100000</td>
      <td>63</td>
      <td>0.063000</td>
    </tr>
    <tr>
      <th>103</th>
      <td>marshall islands</td>
      <td>60000</td>
      <td>37</td>
      <td>0.061667</td>
    </tr>
    <tr>
      <th>68</th>
      <td>iceland</td>
      <td>400000</td>
      <td>201</td>
      <td>0.050250</td>
    </tr>
    <tr>
      <th>3</th>
      <td>andorra</td>
      <td>80000</td>
      <td>34</td>
      <td>0.042500</td>
    </tr>
    <tr>
      <th>61</th>
      <td>grenada</td>
      <td>100000</td>
      <td>36</td>
      <td>0.036000</td>
    </tr>
  </tbody>
</table>

2. Bottom 10 countries by coverage: 10 lowest-ranked countries in terms of number of politician articles as a proportion of country population

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>population</th>
      <th>total_articles</th>
      <th>coverage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>69</th>
      <td>india</td>
      <td>1371300000</td>
      <td>978</td>
      <td>0.000071</td>
    </tr>
    <tr>
      <th>70</th>
      <td>indonesia</td>
      <td>265200000</td>
      <td>209</td>
      <td>0.000079</td>
    </tr>
    <tr>
      <th>34</th>
      <td>china</td>
      <td>1393800000</td>
      <td>1126</td>
      <td>0.000081</td>
    </tr>
    <tr>
      <th>173</th>
      <td>uzbekistan</td>
      <td>32900000</td>
      <td>28</td>
      <td>0.000085</td>
    </tr>
    <tr>
      <th>51</th>
      <td>ethiopia</td>
      <td>107500000</td>
      <td>101</td>
      <td>0.000094</td>
    </tr>
    <tr>
      <th>82</th>
      <td>korea, north</td>
      <td>25600000</td>
      <td>35</td>
      <td>0.000137</td>
    </tr>
    <tr>
      <th>178</th>
      <td>zambia</td>
      <td>17700000</td>
      <td>25</td>
      <td>0.000141</td>
    </tr>
    <tr>
      <th>159</th>
      <td>thailand</td>
      <td>66200000</td>
      <td>112</td>
      <td>0.000169</td>
    </tr>
    <tr>
      <th>112</th>
      <td>mozambique</td>
      <td>30500000</td>
      <td>58</td>
      <td>0.000190</td>
    </tr>
    <tr>
      <th>13</th>
      <td>bangladesh</td>
      <td>166400000</td>
      <td>319</td>
      <td>0.000192</td>
    </tr>
  </tbody>
</table>

3. Top 10 countries by relative quality: 10 highest-ranked countries in terms of the relative proportion of politician articles that are of GA and FA-quality

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>total_articles</th>
      <th>high_quality_articles</th>
      <th>ratio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>82</th>
      <td>korea, north</td>
      <td>35</td>
      <td>6</td>
      <td>17.142857</td>
    </tr>
    <tr>
      <th>104</th>
      <td>mauritania</td>
      <td>48</td>
      <td>6</td>
      <td>12.500000</td>
    </tr>
    <tr>
      <th>31</th>
      <td>central african republic</td>
      <td>66</td>
      <td>8</td>
      <td>12.121212</td>
    </tr>
    <tr>
      <th>132</th>
      <td>romania</td>
      <td>336</td>
      <td>39</td>
      <td>11.607143</td>
    </tr>
    <tr>
      <th>137</th>
      <td>saudi arabia</td>
      <td>116</td>
      <td>13</td>
      <td>11.206897</td>
    </tr>
    <tr>
      <th>166</th>
      <td>tuvalu</td>
      <td>54</td>
      <td>5</td>
      <td>9.259259</td>
    </tr>
    <tr>
      <th>19</th>
      <td>bhutan</td>
      <td>33</td>
      <td>3</td>
      <td>9.090909</td>
    </tr>
    <tr>
      <th>44</th>
      <td>dominica</td>
      <td>12</td>
      <td>1</td>
      <td>8.333333</td>
    </tr>
    <tr>
      <th>155</th>
      <td>syria</td>
      <td>128</td>
      <td>10</td>
      <td>7.812500</td>
    </tr>
    <tr>
      <th>18</th>
      <td>benin</td>
      <td>91</td>
      <td>7</td>
      <td>7.692308</td>
    </tr>
  </tbody>
</table>

4. Bottom 10 countries by relative quality: 10 lowest-ranked countries in terms of the relative proportion of politician articles that are of GA and FA-quality

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>total_articles</th>
      <th>high_quality_articles</th>
      <th>ratio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>143</th>
      <td>slovakia</td>
      <td>116</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>30</th>
      <td>cape verde</td>
      <td>37</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>112</th>
      <td>mozambique</td>
      <td>58</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>38</th>
      <td>costa rica</td>
      <td>147</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>108</th>
      <td>monaco</td>
      <td>40</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>43</th>
      <td>djibouti</td>
      <td>37</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>107</th>
      <td>moldova</td>
      <td>423</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>167</th>
      <td>uganda</td>
      <td>184</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>eritrea</td>
      <td>16</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>50</th>
      <td>estonia</td>
      <td>149</td>
      <td>0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>



5. Geographic regions by coverage: Ranking of geographic regions (in descending order) in terms of the total count of politician articles from countries in each region as a proportion of total regional population

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_articles</th>
      <th>population</th>
      <th>coverage</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>OCEANIA</th>
      <td>3119</td>
      <td>3.978000e+07</td>
      <td>0.000078</td>
    </tr>
    <tr>
      <th>EUROPE</th>
      <td>15829</td>
      <td>7.345900e+08</td>
      <td>0.000022</td>
    </tr>
    <tr>
      <th>LATIN AMERICA AND THE CARIBBEAN</th>
      <td>5166</td>
      <td>6.282700e+08</td>
      <td>0.000008</td>
    </tr>
    <tr>
      <th>AFRICA</th>
      <td>6839</td>
      <td>1.172400e+09</td>
      <td>0.000006</td>
    </tr>
    <tr>
      <th>NORTHERN AMERICA</th>
      <td>1913</td>
      <td>3.652000e+08</td>
      <td>0.000005</td>
    </tr>
    <tr>
      <th>ASIA</th>
      <td>11506</td>
      <td>4.513100e+09</td>
      <td>0.000003</td>
    </tr>
  </tbody>
</table>

6. Geographic regions by coverage: Ranking of geographic regions (in descending order) in terms of the relative proportion of politician articles from countries in each region that are of GA and FA-quality

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>high_quality_articles</th>
      <th>total_articles</th>
      <th>ratio</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NORTHERN AMERICA</th>
      <td>99</td>
      <td>1913</td>
      <td>0.051751</td>
    </tr>
    <tr>
      <th>ASIA</th>
      <td>305</td>
      <td>11506</td>
      <td>0.026508</td>
    </tr>
    <tr>
      <th>OCEANIA</th>
      <td>64</td>
      <td>3119</td>
      <td>0.020519</td>
    </tr>
    <tr>
      <th>EUROPE</th>
      <td>316</td>
      <td>15829</td>
      <td>0.019963</td>
    </tr>
    <tr>
      <th>AFRICA</th>
      <td>124</td>
      <td>6839</td>
      <td>0.018131</td>
    </tr>
    <tr>
      <th>LATIN AMERICA AND THE CARIBBEAN</th>
      <td>69</td>
      <td>5166</td>
      <td>0.013357</td>
    </tr>
  </tbody>
</table>

To perform the above steps the following Python libraries were used
1) [requests](https://pypi.org/project/requests/2.7.0/) - To perform API requests
2) [pandas](https://pandas.pydata.org/) - Python data processing library
3) [numpy](https://numpy.org/) - scientific computing package


#### Reflection

#### 1.  What biases did you expect to find in the data, and why? 

Since the analysis is performed on English Wikipedia articles, there is bias in this analysis. The articles would  be of high-quality from English speaking countries since English is their first language. The articles written in non-English speaking countries, might find their politician articles to be of higher quality in their native language.

By looking at the data some of the titles are not Politican Names but the designation of the post such as "Information Minister of the Palestinian Nation" , "Finance Minister of", "List of politicians in Poland". This can affect downstream analysis. This makes me wonder what is the criteria for choosing an article as a politican article. 

I also  expected to find more number of English Wikipedia articles from English Speaking countries compared to the rest of the world. Since certain language articles are not accounted for as part of our analysis, we can't judge the quality of articles from just the English Wikipedia subset. If these languages are not supported by Wiki/ORES you would find those countries to have poorer quality of articles regardless of other factors.

#### 2. What potential sources of bias did you discover in the course of your data processing and analysis?

By looking at the Top 10 countries by relative quality. We observe North Korea and Saudi Arabia at the top of the list. This result is quite suspect, since North Korea and Saudia Arabia have quite a bad rep in the public media and their goverments are generally oppresive. It is also not surprising to see countries with the lowest populations have the highest coverage. Since they would have the best high quality articles proportion. 

This leads me to think, if the metric for coverage was the right one? Populations might not be a good measure for calculating coverage. If the population increases x2 it doesn't correlate to twice the number of politicians or twice the number of English Wikipedia articles. Also, the scale at which populations work (millions and billions) is not comparable to the number of high quality articles (hundreds and thousands). 

By looking at the documentation for ORES API we find that the service ranks articles not on the English or the grammar but on the structure of the page. This might not be the best indicator for quality of politican articles. 

#### 3. How might a researched supplement or transform this dataset to potentially correct for the limitations/biases you created?

The data in the analysis can be enriched by adding more context to each article, such as who is the author and where does the author reside? It might be helpful to know if the person writing the article actually is a citizen of the country. Additionally, I am not entirely confident that page_data.csv contains all the politician related articles in Wikipedia. More articles are added by the day, and it would be interesting to know what are the data collection methods used to fetch this data


#### References

[Assignment Intructions](https://wiki.communitydata.science/Human_Centered_Data_Science_(Fall_2019)/Assignments#A2:_Bias_in_data)
Citation: Keyes, Os (2017): Politicians by Country from the English-language Wikipedia. figshare. Dataset.

[MIT License](../LICENSE)
