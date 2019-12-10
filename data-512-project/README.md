# FIFA Transfer Market Analysis of European Football Leagues
## Data 512 Project
## Tharun Sikhinam

## I. Introduction

Transfer windows are as busy a time as any other in the football world. The game attracts so much attention that even when the ball is not rolling, the eyes of the entire world are on football. Transfers occur all year round and in every corner of the globe, but activity on the transfer market is typically at its peak during the summer and winter season.

The purpose of this project is to study of the economics in play from 1990 - 2019 in the transfer market of the top european leagues. It would be interesting to know how the trends have changed over the years. And by looking closely at the data, one hopes to uncover any hidden trends and explain the rise of the elite clubs in the European continent. With each clubs bringing in vast amounts of money through TV rights and other sources, it would be interesting to know how the clubs have put this money to use.

Understanding these macroeconomics can help us build a fair game and find areas of improvement. Through this analysis we want to address the wealth inequality of the top elite european clubs and how football has almost become a ‘money-game’. 

## II. Background

The best resource for transfmer markets is the official FIFA TMS[1]. This link holds a summary reports for each transfer window in the european leagues dating back to 2013. The analysis concentrates on a particular transfer window and not the trends over the years. While the report talks about how each country is represented, the players are not classified on their Position (Striker, Midfield etc.,) Through this analysis we wish to answer questions such as "Which country produces the best strikers?"

KPMG also publishes reports on clubs valuations and their spendings[2]. These reports also serve as useful guidelines so that I don't replicate any existing work. Most of these papers focus on a short duration of time, and this motivated me to explore the trends dating back to 1990 and correlating some of the trends found to real-life events.

The wealth gap between the top clubs and lower level clubs has been evident for a while [3], but it would be intersting to know what the exact numbers are. And how this wealth gap has been changing over the years. This can inform football policy makers to design better laws to safeguard the values and spirit of the game.

## III. Data

All the rawData collected for the analysis is stored in [rawData](./rawData) folder

The cleanData is stored in [cleanData](./cleanData) folder

The data for this analysis is scraped off of transfermarkt.co.uk
The scraping was done in accordance with the Terms of Use in this link: https://www.transfermarkt.co.uk/intern/anb After reading the Terms of Use, it clearly states that

```4.8. With the transmission of Content, Transfermarkt grants you the irrevocable, temporally and spatially unlimited and transferable right to reproduce, distribute, publish, issue, make publicly accessible, modify, translate and store the Content. This includes the right to edit, design, adapt to the file formats required for use, and to change and / or improve the presentation quality.```

Furthermore looking at the https://www.transfermarkt.co.uk/robots.txt , the pages we want to scrap off of are not disallowed and are open to web crawlers and scrapers.

This dataset consists of all transfers in the European football market from 1991-2018. The data consists of a player name, club-out, club-in along with the transfer value grouped by different leagues. The dataset also consists of free transfers and loans as well. Most of the data is updated and contributed by the users of the website, and there might be few factual inaccuracies in the transfer figures stated.

<b>Ethical considerations:</b> Player names and ages have been removed from the dataset and will not be used as part of the analysis. This analysis doesn't aim to disrespect any player or country. The results of the analysis are aimed at the governing bodies of different leagues and sport lawmakers. Individual clubs are singled out over the analysis.

## IV. Research Questions

- <b>Q1. How has the transfer spending increased in the top 5 European Leagues?</b>
- <b>Q2. Which clubs spent the most and received the most transfer fee on players from 2010-2018?</b>
- <b> Q3. How have transfers fees moved betwen the leagues from 2010-2018? </b>
- <b> Q4. How has the wealth gap changed amongst the European elite? </b>
- <b> Q5. Investigating the spending trends of Manchester City, Chelsea and Paris Saint-Germain </b>
- <b> Q6. Which country produces the best footballing talent? </b>



