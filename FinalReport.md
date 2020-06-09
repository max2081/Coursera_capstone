# Coursera_capstone

1. INTRODUCTION

1.1 Background
Tourism is one of the biggest industries in the world. As of 2018, the United States of America makes approximately £299 billion per year from tourism. 20-29 year olds make up a large percentage of leisure travel. According to Condor Ferries 
“The younger Gen Z’s and Millennials are the highest spenders when they travel. Calling themselves 'flashpackers' they spend around about $3,500 per trip and $60 a day.”
This demographic is potentially highly lucrative, and unique marketing tactics need to be employed in order to obtain their custom. This demographic is also strongly connected to the internet and therefore current data is imperative when engaging trading dialogue (US travel companies spent $12.97 billion on digital marketing in 2020).
	Probably the most common query is the social aspect of each destination, but this research can be time consuming.
Consequently having access to the destinations with the most highly rated bars, which can be updated at any time, is one of the best ways in which we can provide the most contemporary information, as well as potentially encourage purchase to destinations less commonly frequented.

1.2 The Problem
The proposal is to find out the state capitals with the best bars in the USA.
Ideally the information and rating of every bar in America would be used in to create a dataframe, from which we could average those ratings and rank every city in every state. But without access to full, limitless use of the foursquare API, we will be looking at 5 random bars in the state capitals of each state.

1.3 Interest
Travel companies are the primary target of this information, for the utilisation of selling travel. It can also be used by tourist departments of individual city in order to better boost their tourism industries or encourage investment.

2 DATA ACQUISITION

2.1 Data Sources
A base dataframe with the name, latitude and longitude of the capital cities of each state must first be established. We can apply this information to foursquare in order to retrieve a list of bars, and then to retrieve their rating.
	Wikipedia’s ‘List of State Capitals’ will be scraped using beautifulsoup to create the foundational dataframe, and geopy will obtain latitudes and longitudes.

2.2 Data Cleaning
The list of capital cities was scraped from Wikipedia into a dataframe. This dataframe, due to the scraping of the entire table from Wikipedia’s ‘https://en.wikipedia.org/wiki/List_of_capitals_in_the_United_States', contained the headers: State Name; State Abbreviation; Year Statehood was Established; Capital Name; Area (mi^2); City Population; Metropolitan Population; City Population Rank in State; City Population Rank in US; Notes.
I removed all rankings, notes, changed the area to km^2 ( as it is more compatible with foursquare), change columns to the correct type, rearrange the columns to lead with Capital Name, and sorted by km^2.
The reason I sorted by km^2 is because I wanted to have an idea of the capital sizes, when requesting to foursquare, as radius is one of the conditions. 
Similar cleaning was required after running through foursquare, which we will discuss later.

3 METHODOLOGY

3.1 Geopy
After the foundational dataframe had been created, we then then ran ‘Capital Names’ through geopy to get their coordinates. 
3.2 Folium
The coordinates were then plotted through python’s folium library to visualise the capital locations. This also acted as a simple check to ensure no problems had arisen at this point.
3.3 Foursquare Venue Details
I then created a loop which used the coordinates of each individual capital to query foursquare for a list of thirty bars within a certain radius. This was the first time I found the 404 error for too many requests to foursquare. 50 states x 30 bars = 1,500 requests. The number of bars was reduced to 2 for training, but this sample size could not contain enough points for any statistical analysis. 5 became the final test size.

3.4 Foursquare Ratings and Tables Merge
Another loop was then created to run the ‘id’’s of the bars though foursquare again to obtain their ratings. This also caused 404 error, the option available are to either wait 24 hours for the request limit to reset, or create separate accounts for each separate section of request code.
Once the ratings were obtained, some cleaning was needed in order for the data to be manipulated. The ratings were changed to float, all NaN data was changed to 0.0, and the table was grouped by state and the ratings summed. The the dataframe and the foundational dataframe were both sorted by ‘Capital Name’ and finally merged to create the ranking of state capitals.

4 RESULTS

In order to best view these results I overlaid a Choropleth heat map on the original map of state capitals.
From this map we can see the highest and lowest rated state capitals by the darkness of the green, with Austin, Texas and Sacramento, California being clearly visible. 

Providence, Rhode Island is less visible due to its small size, respectively, but can be viewed upon zooming.

5 DISCUSSION

As stated at the beginning of this report, the data is incomplete. With limited access of foursquare’s API I am able to create the code in test form. This small sample size means that the random bars which fall into our collection are not a fair representation of the bars across each city, with some bars having low ratings or even no rating at all.

This test form shows the capabilities of the code and that it works. At this point it is potentially still saleable with the caveat of access to the full platform upon purchase.

6 CONCLUSION

The potential of this code, with full limitless access to foursquare’s API, is the creation of a full, comprehensive list of all the bars in America and their ratings, from which we could create different comparisons depending on the information that we need. Such as ranking of all the cities in the USA, all the states in the USA or every bar in the USA. Or, with a small amount of tweaking, we could create a ranking of every city in the entire world. 
With this information we can create something which is immensely useful for marketing travel across the globe.
