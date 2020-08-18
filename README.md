# Coursera_Capstone
# Introduction

When moving to a new city, it is difficult to identify which neighborhood suits our needs without already having spent some time in the city.

Therefore, I want to create a tool that will allow users to identify what they like in their current neighborhood and find similar neighborhoods in an other city of their choice.

Typical factors will be amount of: Arts & Entertainment, Food shop, Shop and Service, Outdoor & Recreation & Nightlife Spot. (Those categories are Foursquare top-level categories)

This idea is based on my dream to one day move from where I live to another city and be able to find a neighborhood that match my lifestyle.

# Data

For this study, I am comparing Montreal and Vancouver, two canadian cities.

I use the following sources to gather data:  

- Several internet pages regarding neighbordhood description
  - Montreal: https://habitermontreal.com/en/discover-the-neighbourhoods
  - Vancouver: https://www.tourismvancouver.com/vancouver/neighbourhoods/
  
- Foursquare data regarding venues of each neighborhoods :
  - https://developer.foursquare.com/docs/api-reference/venues/search/
  - https://developer.foursquare.com/docs/build-with-foursquare/categories/


Starting with the neighborhoods names, I find their latitude and longitude using the Nominatim geolocator API.
I then plot the neighborhoods on maps using Folium to ensure the accuracy of their position. I correct several neighborhoods center position manually in my dataset. 
For each neighboroods, I then acquire all venues within a 500 meters radius of their center using the Foursquare Search Venues API. I finally change each venue category to fit within the five top categories defined by Foursquare: Arts & Entertainment, Food shop, Shop and Service, Outdoor & Recreation & Nightlife Spot.

# Methodology

I want the user to identify the neighborhoods they enjoy the most in Montreal and present choices of similar neighborhoods in Vancouver. To do that, I use two methods to come up with recommendations: a K-means clustering algorithm and a Content-based recommendation algorithm.

K-Means clustering:

This Machine Learning method is unsupervised and meant to cluster data. In this method, the user decides on the number of clusters to divide the data into. The algorithm then assigns cluster centroids randomly and assign each data entry to a cluster. Calculating the distance between each point of a given cluster and the centroid of the cluster, the algorithm then moves the centroid. The algorithm loops until the centroids do not move.

For each neighborhoods, I used the numbers of venues in each of the five venues categories to do the clustering excercice. It is interesting to understant that I decided to trim down the number of categories from approximately two hundred to five because the K-means algorithm was not able to produce clusters that objectively makes sens from my opinion, given the fact that I know Montreal and Vancouver quite well. With only five venue categories, I am asking the algorithm work with a five dimensions matrix, much easier than with two hundred dimension matrix.

Another interesting point is the K, or number of clusters, that I decided to use. I played with several numbers, ranging between four and twelve. Ultimatatly, I settled for a K of 8. To do so, I looked at tables of each cluster with each tables showing the most common venues by order. I also looked at spider plots showing for each cluster the average number of venues by category. The spider plots were especially useful because they would show the distribution amongst each categories but also the density of each venues. I also made sure that each cluster had roughly a 50/50 distribution in terms of Montreal and Vancouver neighborhoods.


Content-based recommender:

This algorithm is meant to present the user "more of the same what I've liked before", which is exactly what I want to do in this project. 

To do so, I start by asking the user in which Montreal neighbordhoods he would live, in which he is ambivalent and in which he would not live. He needs to assign a number of either 2, 1 or 0 respectively. I chose a neighborhood by cluster (defined above) to ensure a  

# Results

# Discussion

# Conclusion
