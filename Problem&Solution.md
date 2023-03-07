# SDV-Recvommendation-Engine

Problem:

Instant delivery firm X's front-end is displaying by restaurant level. 
Each of restaurant has unique primary cuisine and multiple secondary cuisines. 
The platform wants to create a recommendation lane to customers top 3 cuisines they are likelihood to choose but have never ordered before. 
Please advise at one model for recommending top 3 cuisines which customers are likelihood to choose but have never ordered before. 

Solution:

Recommendation Engine for New Cuisines:	 
  	 
First, I reshaped the original dataset into a 100x37 matrix which has users as an index, cuisines as columns, and purchase amounts as values. 	 
  	 
I considered "purchasing amounts" as the ranking variable for each cuisine. 
I normalized the number of orders between 0 and 10, as everybody has a different amount of orders.	 
  	 
Despite the general practice would suggest rating "not rated cuisines" as zero, 
it also causes labeling a cuisine as ‘not liked’ in that rating 
so I shift the rate values for each user in the way that the average will be shifted to 0 and the algorithm treats never tried cuisines as “neutral”.	 
  	 
After I split data to test and train as 20:80, 
I used the SVD algorithm on the training data to create “concepts” between cuisines and conduct similarity analysis. 
I assumed that the first 18 concepts include 95 of the information and made a prediction on their rating for users in test data.	 
  	 
Then I checked the results by calculating the MSE of my prediction with actual rankings as what I predict is numbers, 
however, I also made a sanity check with random users if recommendations make sense in general, 
for example suggesting fish to somebody who loves sushi.
