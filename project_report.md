
# First Impression Counts!!
## Finding Ideal First Date Location to blow your Partner's Mind and woo their Heart.

 # Problem Description
 ### First Dates are everything when it comes to make a new relationships. What if there was an ideal way to set a perfect date by studying various locations and venues available there. To identify best location for a Date, First we'll have to define an ideal date.
  ![alt text](http://res.freestockphotos.biz/pictures/7/7613-illustration-of-a-couple-on-a-date-pv.png)

 (Now this part is created on my personnel opinion and may or may not be correct)
 ### An ideal Date can be broken down into Three Parts: 
 ### 1. _Food_:
 #### Food is an essential part of an outing, good food can brighten any dull evening and is great to get conversation started. Thus, we need to choose a location that can offer us great quality and variety of food.
 ### 2. _Activity_:
 #### There is nothing better than a shared activity to bring kindered spirits together than sharing a Activity, watching a movie, a match or visiting a museum... Sharing an activity will bring you closer to your partner and lift up your spirits.
 ### 3. _Drinks_:
 #### After such an amazing evening, it is time to relax with couple of drinks, so it will be great if we could find a great bar or pub nearby. A perfect end to a great evening. 
 
 ----
 ### Now that we have defined an ideal date, we need to find a location that can cater to all our needs so that we don't have to travel unnecessarily.
 ### Thus, It will be very helpful, If some smart programmer can work out locations that are ideal for our dream date.  
 ### Therefore we'll create a notebook that gives us list of locations in Toronto and give us an idea whether they are ideal for us or not. From the list of locations returned we can choose our choice and get ready for an awesome date.
   

# Data We Need
### 1- We will need geo-locational information about that specific borough and the neighborhoods in that borough. We specifically and technically mean the latitude and longitude numbers of that borough. The Postal Codes that fall into Toronto would also be sufficient for us. In fact we will first find neighbourhoods inside Toronto by their corresponding Postal Codes.

### 2- We will need data about different venues in different neighborhoods of that specific borough. In order to gain that information we will use "Foursquare" locational information. By locational information for each venue we mean basic and advanced information about that venue. For example there is a venue in one of the neighborhoods. As basic information, we can obtain its precise latitude and longitude and also its distance from the center of the neighborhood. But we are looking for advanced information such as the category of that venue and whether this venue is a popular one in its category or maybe the average price of the services of this venue. A typical request from Foursquare will provide us with  the following information:
#### [Postal Code]\t[Neighborhood(s)]\t[Neighborhood Latitude]\t[Neighborhood Longitude]\t[Venue]\t[Venue Summary]\t[Venue Category]\t[Distance (meter)]
#### [M1L]\t[Clairlea, Golden Mile, Oakridge]\t[43.711112]\t[-79.284577]\t[Tim Hortons]\t[This spot is popular]\t[Coffee Shop]\t[592]"


# Methodology
## Part 1: Identifying Neighborhoods 
### We will use Postal Codes of different regions inside Toronto to find the list of neighborhoods. We will essentially obtain our information from <https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M> and then process the table inside this site. Images from dataframes and also from maps will be provided in the presentation. Here we only present our strategy and how we got the mission accomplished. 


## Part 2: Connecting to Foursquare and Retrieving Locational Data for Each Venue in Every Neighborhood
   ### After finding the list of neighborhoods, we then connect to the Foursquare API to gather information about venues inside each and every neighborhood. For each neighborhood, we have chosen the radius to be 1000 meter. It means that we have asked Foursquare to find venues that are at most 1000 meter far from the center of the neighborhood. (I think distance is measured by latitude and longitude of venues and neighborhoods, and it is not the walking distance for venues.)"
   

## Part 3: Processing the Retrieved Data and Creating a DataFrame for All the Venues 
### When the data is completely gathered, we will perform processing on that raw data to find our desirable features for each venue. Our main feature is the category of that venue. After this stage, the column \"Venue's Category\" will be One-hot encoded and different venues will have different feature-columns. After On-hot encoding we will integrate all eateries as *"Total Food Places"*, all bars and clubs as *"Total Bars"* and all fun activities as *"Total Activities"* 
### Now, the dataset is fully ready to be used for machine learning (and statistical analysis) purposes.


## Part 4: Applying one of Machine Learning Techniques (K-Means Clustering)
### Here we cluster neighborhoods via K-means clustering method. We think that "5" clusters is enough and can cover the complexity of our problem. After clustering we will update our dataset and create a column representing the group for each neighborhood. 
   

# Decision Making and Reporting Results
   ### Now, we focus on the centers of clusters and compare them for their "Total Food Places" "Total Bars" "Total Activities". The group which its center has the highest "Total Fun Score" will be our best recommendation for a Date. However we recommend users to view results and decide best cluster for themselves as each cluster is unique in its own way 
   
###   {Note: "Total Fun Score" = "Total Food Places" + "Total Bars" + "Total Activities"} This algorithm although is pretty straightforward yet is strongly powerful. 
 # Results:
 
## The best Neighbourhoods were in Cluster 5, these neighbourhoods had Ideal balance of Food Places, Activities and Bars:  
 
### Neighbourhood        :       Adelaide,Richmond,King
### Neighbourhood Latitude                    43.6506
### Neighbourhood Longitude                  -79.3846
---
### Neighbourhood        :      Berczy Park
### Neighbourhood Latitude         43.6448
### Neighbourhood Longitude       -79.3733
---
### Neighbourhood         :     Central Bay Street
### Neighbourhood Latitude                 43.658
### Neighbourhood Longitude              -79.3874
---
### Neighbourhood          :    Christie
### Neighbourhood Latitude      43.6695
### Neighbourhood Longitude    -79.4226
---
### Neighbourhood           :   Church and Wellesley
### Neighbourhood Latitude                  43.6659
### Neighbourhood Longitude                -79.3832
---
### Neighbourhood            :  Commerce Court,Victoria Hotel
### Neighbourhood Latitude                           43.6482
### Neighbourhood Longitude                         -79.3798
---
### Neighbourhood             : Design Exchange,Toronto Dominion Centre
### Neighbourhood Latitude                                     43.6472
### Neighbourhood Longitude                                   -79.3816
---
### Neighbourhood              :Dovercourt Village,Dufferin
### Neighbourhood Latitude                          43.669
### Neighbourhood Longitude                       -79.4423
---
### Neighbourhood            :  Harbourfront East,Toronto Islands,Union Station
### Neighbourhood Latitude                                             43.6408
### Neighbourhood Longitude                                           -79.3818
---
### Neighbourhood             : Harbourfront,Regent Park
### Neighbourhood Latitude                      43.6543
### Neighbourhood Longitude                    -79.3606
---
### Neighbourhood              :High Park,The Junction South
### Neighbourhood Latitude                          43.6616
### Neighbourhood Longitude                        -79.4648
---
### Neighbourhood             : Parkdale,Roncesvalles
### Neighbourhood Latitude                    43.649
### Neighbourhood Longitude                 -79.4563
---
### Neighbourhood              :Ryerson,Garden District
### Neighbourhood Latitude                     43.6572
### Neighbourhood Longitude                   -79.3789
---
### Neighbourhood             : St. James Town
### Neighbourhood Latitude            43.6515
### Neighbourhood Longitude          -79.3754
---
### Neighbourhood             : St. James Town,Cabbagetown
### Neighbourhood Latitude                         43.668
### Neighbourhood Longitude                      -79.3677
---
### Neighbourhood              :Stn A PO Boxes 25 The Esplanade
### Neighbourhood Latitude                             43.6464
### Neighbourhood Longitude                           -79.3748
---
### Neighbourhood             : Summerhill East,Moore Park
### Neighbourhood Latitude                        43.6896
### Neighbourhood Longitude                      -79.3832
---
### Neighbourhood              :The Beaches
### Neighbourhood Latitude         43.6764
### Neighbourhood Longitude        -79.293
---
### Neighbourhood             : The Beaches West,India Bazaar
### Neighbourhood Latitude                            43.669
### Neighbourhood Longitude                         -79.3156
---
### Neighbourhood              :Underground city,First Canadian Place
### Neighbourhood Latitude                                   43.6484
### Neighbourhood Longitude                                 -79.3823
---

## So hop on to any of theabove neighbourhoods and have time of your life. :-)

# Additional Comments:
### It is observed that in various clusters there are vrious range of venues, thus if you want to use this notebook for events other that a Romantic Dates
### It can also be used to lock on locations for all sorts of events like Birthday Parties etc.

# Conclusion
### As we can see, in today's world Data is power and by carefully manipulating data we can find solutions to various complex human problem (like finding an Ideal Romantic Date location) 
## Thank You So Much for Your Time 
    
  ## ----------------------------------------------------------------
  ### Parth Tripathi   - parth.tripathi17@yahoo.com
## ----------------------------------------------------------------



```python

```
