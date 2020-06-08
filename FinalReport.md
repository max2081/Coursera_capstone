# Coursera_capstone

INTRODUCTION/BUSINESS PROBLEM

For my final project, I will be looking to find the capital cities with the best bars in America.
I will be creating a comparable list of the bars in the capital cities of each state of America, 
and ranking them by rating. We can then find which capital cities have the best bars in America.

The reason I chose this project is because I wanted to look at the saleable aspects of foursquare’s data. 
What makes most sense to me is its usage by travel companies to make recommendation to their clients. 
This comparable list would mean that travel companies in my country would be able to recommend the 
best cities for travel to young adults who are interested in the more social aspects of their potential destinations.
This appears, to me, to be useful knowledge for a travel company to have in order to perform specific 
marketing to increases sales to particular destinations. 

DATA

I will be scraping the wikipedia list of state capitals in order to create a useable dataframe. 
I will also be using geopy to add lat and lon to be compatible with foursquare. 
I will then be utilising foursquare to retrieve the bars, then again to retrieve the ratings.
I will mainly be creating dataframes from a source which I will then manipulate so that they are then 
usable with the next data source.
The main difficult is that the amount of values passing though the APIs will be high. 
For example, 50 state capitals and 30 bars is 1,500 calls for venue details, then 1,500 more calls for ratings.
