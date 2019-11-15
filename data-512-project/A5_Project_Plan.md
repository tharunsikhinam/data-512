# A5: Project Plan
## Tharun Sikhinam

## Introduction: 

Transfer windows are as busy a time as any other in the football world. The game attracts so much attention that even when the ball is not rolling, the eyes of the entire world are on football. Transfers occur all year round and in every corner of the globe, but activity on the transfer market is typically at its peak during the summer and winter season. 

The purpose of this project is to study of the economics in play from 1990 - 2019 in the transfer market of the top 5 european leagues. It would be interesting to know how the trends have changed over the years. And by looking closely at the data, one hopes to uncover any hidden trends and explain the rise of the elite clubs in the European continent. With each clubs bringing in vast amounts of money through TV rights and other sources, it would be interesting to know how the clubs have put this money to use. 

## Research Questions and/or hypotheses:

Some of the research questions that the project hopes to answer are:

Q1: Players from which country are the most valued by year ? 

It would be interesting to identify players of which country are the most valued by year. From this analysis dating back to 1990, we could identify the countries that output the best footballing talent and categorize them by different positions on the pitch (Midfielder, Striker, Defender). This would help us answer questions such as "Which country produces the best defenders?"

As a result of this analysis, we can test the following hypothesis:

H1: Country winning the world cup is associated with an increase in transfers/value of players from that country in the subsequent years

As an example, the hypothesis is that players from Germany are more valued after their world cup win in 2014 compared to the previous four years.

Q2: How has the spending in the top 5 soccer leagues increased over the years ? 

New transfer records are broken and each club is spending more every year. By doing an exploratory analysis on the transfer spendings of the top 5 European leagues, we can identify some of the top spenders by year and decade. 

Over the recent years, there has been a massive influx of foreign investment into European soccer clubs. Some of these clubs include Manchester City, Chelsea and Paris Saint-Germain. It would be intresting to know how the spending patterns have changed over the years for these three clubs in particular.

Q3: Has the spending gap grown between the top tier and lower league teams ?

As television rights and alternate sources of income increase for the big clubs, we observe the clubs in the lower tiers struggling to stay afloat. With the mega rich clubs spending more each year, we plan to investigate the gap in spending between the top tier leagues and lower leagues from 1990-2019 for the top 5 european soccer leagues

H2: The introduction of the UEFA Financial Fair Play Regulations caused a significant drop in spending from the top European clubs

The Financial Fair Play Regulartions (FFP) was introduced to prevent the mega rich clubs from spending increasing amounts of money and to prevent the poorer clubs from going bankrupt. Football clubs spent exorbant amounts of money in pursuit of the European Cup. By analyzing the transfer market, we aim to see if the FFP had a significant impact on the transfer spendings.

### Background and/or Related Work: 

The best resource for transfmer markets is the official FIFA TMS[[1]](https://www.fifatms.com/data-reports/reports/). This link holds a summary reports for each transfer window in the european leagues dating back to 2013. The analysis concentrates on a particular transfer window and not the trends over the years. While the report talks about how each country is represented, the players are not classified on their Position (Striker, Midfield etc.,) Through this analysis we wish to answer questions such as "Which country produces the best strikers?"

KPMG also publishes reports on clubs valuations and their spendings[[2]](https://www.footballbenchmark.com/documents/files/public/KPMG%20Football%20Clubs%20Valuation%20The%20European%20Elite%202018%20web.pdf). These reports also serve as useful guidelines so that I don't replicate any existing work. Most of these papers focus on a short duration of time, and this motivated me to explore the trends dating back to 1990 and correlating some of the trends found to real-life events. 

The wealth gap between the top clubs and lower level clubs has been evident for a while [[3]](https://www.usatoday.com/story/sports/soccer/2018/01/16/uefa-warns-of-growing-wealth-gap-in-top-clubs-finance-study/109521284/), but it would be intersting to know what the exact numbers are. And how this wealth gap has been changing over the years. This can inform football policy makers to design better laws to safeguard the values and spirit of the game. 

### Methodology:

#### Data Gathering
The data gathering process starts by scraping of trsansfermarket.co.uk website and extracting relevant information foreach transfer window for the top 5 European leagues. 

The data is scraped and stored yearly and categorized into different leagues. 
For each league the data is stored in the following format

**club\_name**|**player\_name**|**age**|**position**|**club\_involved\_name**|**fee**|**transfer\_movement**|**fee\_cleaned**|**league\_name**|**year**|**season**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
Arsenal FC|Eddie McGoldrick|28|Central Midfield|Crystal Palace|£1.15m|in|1.15|Premier League|1993|1993/1994
Arsenal FC|Paul Dickov|21|Centre-Forward|Luton Town|"End of loanDec 1| 1993"|in|0|Premier League|1993
Arsenal FC|Adrian Clarke|18|Midfielder|Arsenal Res.|-|in|0|Premier League|1993|1993/1994

#### Data Processing and Analysis
As part of the data processing step, the data is combined across multiple years for each of the leagues
This data will be stored as a pandas dataset and queried on to answer question 1. Grouping this dataset by country and position would allow us to know which countries produces which kind of footballing talent. 

To test our Hypothesis 1, if world cup winning countries have higher transfer values in the subsequent years, we use the world cup winning list from https://en.wikipedia.org/wiki/List_of_FIFA_World_Cup_finals . Using this list of world cup winners we compare the transfer market value for a countries' players four years before and after they have won the worldcup. To prove statistical siginificance a students t-test will be used. This test is chosen since the number of samples are particularly less and we have only 6 world cups worth of data to analyze from (1994,1998,2002,2006,2010,2014)

To answer question 2, we use the same dataset we used to answer question 1, and sum the transfer spendings by league across different years. These transfer earning will be adjusted to inflation to compare historical and current data poitns. 

To specifically analyze the clubs of interest Manchester City, Chelsea and Paris Saint-Germain, we perform a t-test to see if the spending increased significantly before and after they were bought by foreign owners. Students t-test is used since the number of samples is low and we are comparing means of two groups. As a follow-up, I plan to report the amount of transfer spending from each of these clubs before they won their first European Cup/League Title.

To answer question 3, we perform an analysis for only the English Football League. Transfer spendings are compared between the Tier-1 and Tier-2 levels of the English Football League and plotted over the years. The spendings will be adjusted for inflation.

To test Hypothesis 2, we compare the spending before and after the UEFA FFP rules were introduced. 2 seasons of data before and after are taken for each of the leagues and a students t-test is used to check if there was a significant decrease/increase in spending after the rules were introduced. This analysis will be performed on a per league basis to check if the rules were implemented fairly for all the clubs. 

#### Data Results Presentation

The project uses tables and visualizations to explain the results from the analysis. 

For question 1, we show which country had the highest value in transfers and rank the top 5 countries yearly. 

|country|year|transfer_spendings|
|-------|----|------------------|
|Spain  |2002|34.5              |

We then group these results by position and rank countries by each position, presenting results in the following format

|Position|Country|Number_of_players|Average Player Value|
|--------|-------|-----------------|--------------------|
|        |       |                 |                    |

For question 2, a line graph is plotted over the years showing the trend in transfer spendings. Different line graphs are plotted for each league, with color differentiating the different leagues

For question 3, a line graph is plotted between the transfer spendings between Tier-1 and Tier-2 levels of English Football Leagues. 

The results of the students t-test are presented as tables with explanations for the choice of p-value and clearly phrased hypothesis and conclusions.


## References

1) https://www.fifatms.com/data-reports/reports/

2) https://www.footballbenchmark.com/documents/files/public/KPMG%20Football%20Clubs%20Valuation%20The%20European%20Elite%202018%20web.pdf

3) https://www.usatoday.com/story/sports/soccer/2018/01/16/uefa-warns-of-growing-wealth-gap-in-top-clubs-finance-study/109521284/


