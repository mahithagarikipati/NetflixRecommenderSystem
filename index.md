## ITCS-6190 Group-3 Netflix Recommender System
#### Mahitha Garikipati - mgarikip@uncc.edu
#### Navya Gunti - ngunti@uncc.edu

- [X] 1. Created web page for course project report. One report per team. Prefer UNCC hosted web 
page, but GitHub or similar sites are ok. Please do not share code on your web page. 
- [X] 2. Project title and names of team members. 
- [X] 3. Overview of project, tasks involved and approach, steps implemented, and final products and 
results.  
- [X] 4. Context and motivation for project, stating what is interesting/important/useful/fun about it. 
- [X] 5. Data set(s) used for project and how they were obtained, size of data, and features used. 
- [X] 6. What algorithms and techniques were implemented, and frameworks (e.g., Hadoop, Spark) 
used. 
- [X] 7. Please state any other (external) tools or software packages you used. 
- [ ] 8. Illustrative results and examples. 
- [ ] 9. Performance evaluation, preferably quantitative. 
- [X] 10.  What aspects of the (a) definitely will do, (b) likely will do, and (c) would ideally like to do items 
did you accomplish? 
- [X] 11.  Any additional comments and observations (e.g., challenges, surprises, cool enhancements, 
things you learnt,...) 
- [X] 12.  Work division among team members. 
- [ ] 13.  Any important references that you used. 
- [ ] 14.  Documented and commented code, and README with the information we need to know to run 
your code. (Do not post code publicly, although you can include snippets in your report if you 
think that will be helpful.) Submitted on Canvas. 
- [ ] 15.  Sent email to instructor and TA with link to project report. 
- [ ] 16.  Signed up for project demo slot (to be decided). 
### Overview
The purpose of this project is to implement Netflix Recommender System by using cloud computing concepts.

The concepts implemented are - Person Correlation Coefficient, Cosine Similarity algorithms, and Alternating Least squares to find RMSE

These algorithms made use of pySpark framework for implementing the collaborative filtering to recommend movies to given user.

This project made use of dsba-hadoop cluster provided by the university for storing the data and to deploy the code.

### Tasks Involved and approach
- Fetching Netflix movie datasets
- Understanding of Algorithms to implement
- Analyzing the datasets
- Cleaning the dataset
- Configuring GoogleColab Notebook with spark
- Implementing Pearson Correlation Coefficient Algorithm
- Implementing Cosine similarity
- Implementing Alternating Least Squares
- Configuring in dsba-hadoop.uncc.edu to store required datas file and code
- Running the code on dsba-hadoop.uncc.edu
- Testing the algorithm for different users, to get movie recommendations
- Creating Course Project web page

### Context & Motivation
The context for this project is to implement a recommender system that predicts movies for Netflix platform. 

In today’s world, it is important to recommend items based on users preference due to many competitors in the world’s market. 

With the global pandemic taking a toll, the number of people who subscribed for Netflix and other streaming platforms rose as it became the prime means of entertainment. 

Netflix, itself started publishing new content everyday along with other competitors and as a result, users often get confused and frustrated with the huge ocean of available content. 

This makes the project really important, since it recommends movies based on user’s preference which is the most leading factor amongst many streaming competitors and helps us to learn about algorithm implementations more in detail. 

### Steps Implemented

### Datasets

The dataset that is to be implemented in this project will be MovieLens 20M dataset provided by Kaggle. 

The link to this dataset can be found [here](https://www.kaggle.com/grouplens/movielens-20m-dataset)

The size of the data is around 693 MB and contains details about the user id, movie id, ratings, timestamp, movie title, year of movie release, genres. 

This dataset contains around 20 Million ratings on 27 thousand movies which are given by 138 thousand users. 

### Understanding of Algorithms:

#### Recommender Systems

The main role of Recommender Systems is to recommend items to the user. 

The items recommended can be based on the previous items liked by the user or based on other users with similar preferences.

This classifies the recommnder systems into 2 types - Collaborative Recommender Systems & Content Based Recommender Systems.

#### Collaborative Recommender Systems:

In this type of Recommender Systems, recommendations are made to user by collecting the data of users having similar preferences and taste.

When applied to this project, it recommends movies to a user based on the ratings of other users with similar preference.

In this project we use Pearson Correlation to recommend top 15 movies to the given user.

#### Content Recommender Systems:

In this type of Recommender Systems, recommendations are made to the user based on the user's preferences in the past.

#### Pearson Correlation Coefficient:

The extent to which two sets of data are related is measured by correlation. 
The most common measure of correlation in statistics is the Pearson Correlation. 
The Pearson Product Moment Correlation is its full name (PPMC). It shows the relationship between two sets of data in a linear way.

![image](https://user-images.githubusercontent.com/95369639/145697582-5ee562d1-9a42-4303-a1ca-d6e3a4e1b6af.png)

We calculated the Pearson Correlation Coefficient and therefore similarity among users based on the movies they saw and provided similar ratings to reach at movie recommendation as an outcomes.

##### Interpreting Pearson Correlation
1.-1 indicates that two users are behaving in radically opposing ways.
2.There is no relationship between 0 and 1.
3.1 indicates that two users have identical behaviors.

The Pearson Correlation Coefficient between two variables can be found by dividing the covariance of the variables by the product of their standard deviations in statistics.

#### Alternating Least Squares
The Alternating Least Square (ALS) algorithm is a matrix factorization approach which runs in parallel. 
ALS is built for large-scale collaborative filtering tasks and is implemented in Apache Spark ML. 
ALS does a decent job of dealing with the Ratings data's scalability and sparseness, and it's simple and scales well to very big datasets.
We use Matrix Factorization to deconstruct the user-item matrix into a lower-dimensional matrix comprising user factors and item factors.

##### Our work flow is following:
1. When a new user enters their favourite movies, the system generates new user-movie interaction samples for the model.
2. With the new inputs, the system retrains the ALS model on data.
3. For inference, the system generates movie data (in our case,  we sample all movies from the data)
4. According to the ranking of movie rating predictions, the system generates the top N movie recommendations for that user.

By minimizing the cost function, these smaller dimension matrices are used to estimate the ratings.
Ratings are predicted and given as results after numerous iterations of lowering the Root Mean Square Error at the convergence point.

#### Cosine Similarity:
The cosine of the angle between two vectors projected into multidimensional space is used to compute cosine similarity between two vectors. 
That can be used on items in a dataset to determine how similar they are to one another utilizing keywords or other criteria. 
The dot product of two vectors (A and B) is divided by the reported to be significantly to calculate the similarity between them, as indicated in the equation below. 
Simply put, as the angle between two vectors lowers, the CS score of the two vectors increases.
![image](https://user-images.githubusercontent.com/95369639/145727646-964b7350-c73b-4349-b1b5-7565d4a7ae0c.png)


###  About our modified dataset:

Due to the difficulty in computing the ( 20 Million ratings * 27 thousand movies) using dsba-hadoop cluster, the amount of data is reduced

The number of movies originally contains data from (1995 - 2015). 

However, for this project, only 3 year movies are considered (2013 - 2015) and their corresponding users and ratings.

Total number of movies = 1878

Total number of ratings = 5112

A total of 397 users are considered for this Netflix Recommender System

SInce, the name of the user is not available in the dataset, user id is considered. The set of user id are as follows: 

<details>
  <summary markdown="span"> <u>View available <b>user id:</b></u>
  </summary>
  <p>31,71,96,107,133,136,162,176,208,213,215,248,260,271,279,284,285,318,342,370,398,425,455,459,466,520,521,540,551,572,577,586,596,614,631,637,692,707,710,713,729,735,768,770,786,804,808,828,829,843,851,858,866,887,891,898,910,964,969,975,979,1048,1108,1141,1217,1228,1239,1244,1246,1257,1268,1271,1274,1277,1319,1331,1339,1341,1344,1433,1468,1518,1520,1527,1551,1559,1588,1602,1629,1644,1678,1703,1705,1721,1734,1741,1755,1761,1775,1837,1848,1853,1877,1948,1958,1968,1979,1996,2047,2068,2084,2093,2095,2138,2161,2188,2189,2208,2219,2269,2270,2287,2295,2298,2301,2310,2333,2367,2368,2414,2421,2423,2425,2449,2460,2515,2517,2535,2544,2568,2586,2606,2650,2657,2669,2702,2713,2742,2751,2813,2835,2874,2908,2928,2930,2959,2974,2988,3004,3020,3029,3031,3038,3070,3127,3149,3156,3163,3181,3205,3240,3251,3257,3267,3268,3282,3289,3326,3358,3364,3386,3397,3409,3413,3419,3429,3446,3448,3453,3456,3487,3490,3523,3529,3563,3589,3618,3634,3640,3660,3668,3676,3683,3693,3751,3797,3845,3846,3858,3867,3878,3884,3896,3990,4026,4039,4055,4063,4066,4087,4089,4165,4181,4222,4223,4257,4270,4274,4279,4281,4305,4347,4380,4405,4430,4450,4464,4468,4472,4488,4515,4537,4541,4550,4563,4571,4575,4587,4590,4596,4605,4627,4629,4635,4658,4660,4709,4745,4752,4759,4780,4793,4812,4813,4822,4829,4851,4855,4877,4910,4957,4965,4967,4968,5002,5004,5036,5037,5050,5058,5077,5080,5107,5125,5130,5138,5160,5181,5192,5208,5219,5242,5259,5264,5279,5288,5298,5309,5315,5337,5347,5352,5353,5359,5378,5417,5423,5440,5442,5443,5446,5457,5475,5489,5495,5514,5517,5529,5540,5550,5622,5643,5665,5718,5731,5763,5792,5800,5810,5823,5832,5840,5857,5871,5911,5928,5930,5952,5954,5973,5980,6039,6088,6112,6125,6148,6166,6171,6175,6184,6233,6236,6268,6308,6310,6325,6339,6340,6390,6412,6429,6441,6455,6472,6507,6524,6554,6632,6637,6646,6702,6721,6723,6750,6788,6832,6838,6881,6894,6899,6915,6939,6961,6970,6995,7007,7016,7027,7036,7038,7042,7047,7064,7066,7074,7086,7090
 </p>
</details>


Any of these user id's can be selected inorder to get recommendations based on other users ratings.


### Algorithms and techniques implemented, frameworks used, External Tools
 
 Implemented Pearson correlation coefficient, Cosine Similarity , Alternating Least squares. Spark framework is used for the algorithm implementations.
 
 We made use of Google Colab and Jupiter notebook for compiling the code and dsba-hadoop cluster for deployment.

### Pearson Correlation Coefficient  & Cosine Similarity Algorithm Results
The algorithm is tested to check the efficiency for some users which are listed above

### Pearson Correlation Coefficient 

1) For user id = 31, the ratings of the movies are as follows
  ![image](https://user-images.githubusercontent.com/20443793/145141226-d5a0b0d6-9e54-4fd1-aa9e-9031e0915c21.png)
  
   The top 15 recommendations obtained for this user 31 are 

        'Penguins of Madagascar ', 'Frank ', 'Internet's Own Boy: The Story of Aaron Swartz' , 'The Bridegroom ', 'Great Beauty, The (Grande Bellezza La)', 'Sound City ', 'Louis C.K.: Oh My God ', 'Citizenfour ', 'Leviathan ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Coherence ', 'Proxy ', 'Sacrament, The ', 'Raze '
    

2) For user id = 540,
   ![image](https://user-images.githubusercontent.com/20443793/145141388-4ffcac6e-3be0-4a28-acef-1686a6956c5d.png)
   
   The top 15 recommendations obtained for this user 540 are 

        'Adventurer: The Curse of the Midas Box, The ', 'Frank ', 'Double, The ', 'Lee Daniels The Butler ', 'Louis C.K.: Oh My God ', 'All Cheerleaders Die ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Raze ', 'Jim Gaffigan: Obsessed ', 'Big Bad Wolves ', 'Six by Sondheim ', 'Toy Story of Terror '
     


3) For user id = 979,
   ![image](https://user-images.githubusercontent.com/20443793/145141737-1708a8f6-08aa-4548-87a0-a65a7386ffe2.png)
   The top 15 recommendations obtained for this user 979 are 
   
       'Penguins of Madagascar ', 'Foxcatcher ', 'American Sniper ', 'Coherence ', 'Justice League: War ', 'Sound City ', 'Warm Bodies ', 'Wind Rises, The (Kaze tachinu) ', 'Delivery Man ', 'Wish I Was Here ', 'Insidious: Chapter 2 ', 'The Fault in Our Stars ', 'Citizenfour ', 'Bad Words ', 'Big Bad Wolves '
     

4) For user id = 1588,
   ![image](https://user-images.githubusercontent.com/20443793/145141938-3eba587f-6a37-4171-bc83-ea8aa4c58ad7.png)
   The top 15 recommendations obtained for this user 1588 are    
    
        'Foxcatcher ', 'Bridegroom ', 'Double, The ', 'Whiplash ', 'Raze ', 'Pride ', 'American Sniper ', 'All Cheerleaders Die ', 'Olive Kitteridge ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Jersey Boys ', 'Normal Heart, The ', 'Jim Gaffigan: Obsessed '


5) For user id = 2460
   ![image](https://user-images.githubusercontent.com/20443793/145142114-160c7ca2-876e-41d3-b4bb-4648e78e5e01.png)
   The top 15 recommendations obtained for this user 2460 are 
   
        'Adventurer: The Curse of the Midas Box, The ', 'Pride ', 'Trip to Italy, The ', 'Frank ', 'Internet's Own Boy: The Story of Aaron Swartz, The ', 'Double, The ', 'Batman: The Dark Knight Returns, Part 2 ', 'Nightcrawler ', 'All Cheerleaders Die ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Most Wanted Man, A ', 'Raze '


6) For user id = 3251
   ![image](https://user-images.githubusercontent.com/20443793/145142198-209d3ec3-a823-456d-848e-e27e056df426.png)
   The top 15 recommendations obtained for this user 3251 are 
   
          'Hard to Be a God ', 'Batman: Assault on Arkham ', 'Felony ', 'Lilting ', 'Stranger by the Lake (L'inconnu du lac) ', 'Justice League: War ', 'Adventurer: The Curse of the Midas Box, The ', 'American Sniper ', 'Raze ', 'Bridegroom ', 'Batman: The Dark Knight Returns, Part 2 ', 'National Gallery ', 'Ascension ', 'All Cheerleaders Die ', 'Horns '

7) For user id = 3845
   ![image](https://user-images.githubusercontent.com/20443793/145142295-447045ef-cf22-44eb-bcc2-02ebb735d36b.png)
   The top 15 recommendations obtained for this user 3845 are 
   
        'Citizenfour ', 'Coherence ', 'Whiplash ', 'Raze ', 'Lilting ', 'Locke ', 'Starred Up ', 'Better Living Through Chemistry ', 'Blue Is the Warmest Color (La vie d'Adèle) ', 'Insidious: Chapter 2 ', 'About Time ', 'Kick-Ass 2 ', 'Great Gatsby, The ', 'Pain & Gain ', 'East, The '
   

8) For user id = 4541
   ![image](https://user-images.githubusercontent.com/20443793/145142501-2f1ffade-ca77-4907-a4ce-9fda48beb2e6.png)
   The top 15 recommendations obtained for this user 4541 are 
   
        'Pride ', 'Felony ', 'Hard to Be a God ', 'Internet's Own Boy: The Story of Aaron Swartz, The ', 'Raze ', 'East, The ', 'All Cheerleaders Die ', 'Olive Kitteridge ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Trip to Italy, The ', 'Jim Gaffigan: Obsessed ', 'Bad Words '


9) For user id = 6175
   ![image](https://user-images.githubusercontent.com/20443793/145142906-26b59fe6-e358-4c87-a643-e90b54582782.png)
   The top 15 recommendations obtained for this user 6175 are 
   
        'Justice League: War ', 'Whiplash ', 'Ascension ', 'Olive Kitteridge ', 'Blind ', 'American Sniper ', 'This Is Where I Leave You ', 'Wish I Was Here ', 'Under the Skin ', 'Grand Piano ', 'Big Bad Wolves ', 'Me, Myself and Mum (Les garçons et Guillaume, à table!) ', 'Armstrong Lie, The ', 'Fifth Estate, The ', 'Inequality for All '
   

10) For user id = 7027
   ![image](https://user-images.githubusercontent.com/20443793/145142652-ef53a263-4e91-4767-9b78-aa6f87b98a6b.png)
   The top 15 recommendations obtained for this user 7027 are 
   
        'Adventurer: The Curse of the Midas Box, The ', 'Citizenfour ', 'American Sniper ', 'Jim Gaffigan: Obsessed ', 'Louis C.K.: Oh My God ', 'Nightcrawler ', 'Birdman ', 'Gone Girl ', 'Grand Budapest Hotel, The ', 'Big Hero 6 ', 'Batman: The Dark Knight Returns, Part 2 ', 'X-Men: Days of Future Past ', 'Guardians of the Galaxy ', "Bill Burr: I'm Sorry You Feel That Way ", 'What We Do in the Shadows '
   
   
### Cosine Similarity

1) For user id = 31,
  ![image](https://user-images.githubusercontent.com/20443793/145141226-d5a0b0d6-9e54-4fd1-aa9e-9031e0915c21.png)
  
   The top 15 recommendations obtained for this user 31 are 

        'Batman: Assault on Arkham ', 'Hard to Be a God ', 'Felony ', 'Lilting ', 'Justice League: War ', 'Wish I Was Here ', 'Raze ', 'Trip to Italy, The ', 'In Your Eyes ', 'Jersey Boys ', 'The Last Five Years ', 'Ascension ', 'Free Fall ', 'Olive Kitteridge ', 'Blind '
        
2) For user id = 540,
   ![image](https://user-images.githubusercontent.com/20443793/145141388-4ffcac6e-3be0-4a28-acef-1686a6956c5d.png)
   
   The top 15 recommendations obtained for this user 540 are 

       "Stranger by the Lake (L'inconnu du lac) ", 'Raze ', 'Ascension ', 'All Cheerleaders Die ', 'Free Fall ', 'Olive Kitteridge ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Frequencies ', 'Normal Heart, The ', 'Jim Gaffigan: Obsessed ', 'Big Bad Wolves ', 'Me, Myself and Mum (Les garçons et Guillaume, à table!) '

3) For user id = 979,
   ![image](https://user-images.githubusercontent.com/20443793/145141737-1708a8f6-08aa-4548-87a0-a65a7386ffe2.png)
   The top 15 recommendations obtained for this user 979 are 
   
       'Hard to Be a God ', 'Batman: Assault on Arkham ', 'Lilting ', 'Justice League: War ', 'Felony ', 'Raze ', 'Wish I Was Here ', 'In Your Eyes ', 'Jersey Boys ', 'The Last Five Years ', 'Love Steaks ', 'Ascension ', 'Free Fall ', 'Olive Kitteridge ', 'Horns '
     
 
 4) For user id = 1588,
   ![image](https://user-images.githubusercontent.com/20443793/145141938-3eba587f-6a37-4171-bc83-ea8aa4c58ad7.png)
   The top 15 recommendations obtained for this  user 1588 are  
       
          'Hard to Be a God ', 'Raze ', 'In Your Eyes ', 'Big Bad Wolves ', 'Ascension ', 'Free Fall ', 'Olive Kitteridge ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Trip to Italy, The ', 'Wish I Was Here ', 'Normal Heart, The ', 'Jim Gaffigan: Obsessed ', 'Venus in Fur (La Vénus à la fourrure) '
    
 5) For user id = 2460
   ![image](https://user-images.githubusercontent.com/20443793/145142114-160c7ca2-876e-41d3-b4bb-4648e78e5e01.png)
   The top 15 recommendations obtained for this user 2460 are 
    
          'Hard to Be a God ', 'Batman: Assault on Arkham ', 'Felony ', 'Lilting ', 'Internet's Own Boy: The Story of Aaron Swartz, The ', 'Raze ', 'Trip to Italy, The ', 'In Your Eyes ', 'The Last Five Years ', 'Ascension ', 'All Cheerleaders Die ', 'Olive Kitteridge ', 'Blind ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns '

6) For user id = 3251
   ![image](https://user-images.githubusercontent.com/20443793/145142198-209d3ec3-a823-456d-848e-e27e056df426.png)
   The top 15 recommendations obtained for this user 3251 are 
   
          'Hard to Be a God ', 'Felony ', 'Justice League: War ', 'Lilting ', 'Wish I Was Here ', 'Raze ', 'Bridegroom ', 'Boxtrolls, The ', 'The Last Five Years ', 'Love Steaks ', 'National Gallery ', 'Ascension ', 'Olive Kitteridge ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns '

7) For user id = 3845
   ![image](https://user-images.githubusercontent.com/20443793/145142295-447045ef-cf22-44eb-bcc2-02ebb735d36b.png)
   The top 15 recommendations obtained for this user 3845 are 
   
          'Hard to Be a God ', 'Batman: Assault on Arkham ', 'Felony ', 'Lilting ', "Internet's Own Boy: The Story of Aaron Swartz, The ", 'Wish I Was Here ', 'Raze ', 'The Last Five Years ', 'Love Steaks ', 'National Gallery ', 'Ascension ', 'All Cheerleaders Die ', 'Free Fall ', 'Olive Kitteridge ', 'Horns '
   

8) For user id = 4541
   ![image](https://user-images.githubusercontent.com/20443793/145142501-2f1ffade-ca77-4907-a4ce-9fda48beb2e6.png)
   The top 15 recommendations obtained for this user 4541 are 
   
        'Hard to Be a God ', 'Felony ', 'Lilting ', 'Wish I Was Here ', 'Raze ', 'In Your Eyes ', 'Jersey Boys ', 'The Last Five Years ', 'Love Steaks ', 'National Gallery ', 'Ascension ', 'Free Fall ', 'Olive Kitteridge ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns '

9) For user id = 6175
   ![image](https://user-images.githubusercontent.com/20443793/145142906-26b59fe6-e358-4c87-a643-e90b54582782.png)
   The top 15 recommendations obtained for this user 6175 are 
   
        'Batman: Assault on Arkham ', 'Trip to Italy, The ', 'They Came Together ', 'Justice League: War ', 'Raze ', 'Wish I Was Here ', 'In Your Eyes ', 'Ascension ', 'Free Fall ', 'Olive Kitteridge ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Perfect Sisters '
   

10) For user id = 7027
   ![image](https://user-images.githubusercontent.com/20443793/145142652-ef53a263-4e91-4767-9b78-aa6f87b98a6b.png)
   The top 15 recommendations obtained for this user 7027 are 
   
        'Trip to Italy, The ', 'They Came Together ', 'Bridegroom ', 'Raze ', 'Boxtrolls, The ', 'Ascension ', 'All Cheerleaders Die ', 'Olive Kitteridge ', 'Blind ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Wish I Was Here ', 'Normal Heart, The '
       
  ### ALS
  
  Run the ALS on input data and to reccomand the movies for user 
 1) If train=70% and Test=30%, then the root mean square error is :

![image](https://user-images.githubusercontent.com/95369639/145729692-fa061601-ff92-4e30-9604-aacddbf073e8.png)

The recomendations for the users are:
![image](https://user-images.githubusercontent.com/95369639/145729702-c9d5e890-0d9a-43a4-9156-3b37fd184c06.png)


2) If train=85% and Tes=15%, then the root mean square error is :

![image](https://user-images.githubusercontent.com/95369639/145729645-f9eb2c21-c253-4e57-91c1-60b6894e9d78.png)

The reccomendations for the users are:
![image](https://user-images.githubusercontent.com/95369639/145729677-07d8fde8-c9b0-44df-93d3-c6ae9c0a3edf.png)


## Performance Evaluation

ALS, have been applied by splitting the data into 70-30% training and test data as well as 85-15% training and test data.

RMSE value, when considered 70,30 split percentage is 1.696 while for the 85,15 split is 1.656.

Clearly from the above outputs, the recommendations when made for each user, using pearson and cosine are only around 40% common.

Evaluating these results by considering the recommendations from ALS, Pearson correlation and cosine similarity for a random user among the above 10.

For user id = 2460
   ![image](https://user-images.githubusercontent.com/20443793/145142114-160c7ca2-876e-41d3-b4bb-4648e78e5e01.png)
   The top 15 recommendations obtained for this user 2460 are 
   
 
 Pearson Correlation ---> 'Adventurer: The Curse of the Midas Box, The ', 'Pride ', 'Trip to Italy, The ', 'Frank ', 'Internet's Own Boy: The Story of Aaron Swartz, The ', 'Double, The ', 'Batman: The Dark Knight Returns, Part 2 ', 'Nightcrawler ', 'All Cheerleaders Die ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Proxy ', 'Sacrament, The ', 'Most Wanted Man, A ', 'Raze '
 
 Cosine Similarity ----->  'Hard to Be a God ', 'Batman: Assault on Arkham ', 'Felony ', 'Lilting ', 'Internet's Own Boy: The Story of Aaron Swartz, The ', 'Raze ', 'Trip to Italy, The ', 'In Your Eyes ', 'The Last Five Years ', 'Ascension ', 'All Cheerleaders Die ', 'Olive Kitteridge ', 'Blind ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns '
  
 ALS using (70-30 ) -----> Nightcrawler , 42 , Frank, Edge of Tomorrow, Blue Jasmine , The Imitation Game, 'Grand Budapest Hotel, The ', 'Day of the Doctor, The ', Ender's Game , 'Great Gatsby, The'
 
 ALS using (85-15 ) -----> Big Bad Wolves , Short Term 12 , Begin Again ,All Cheerleaders Die  , Birdman , 'Double, The ', Edge of Tomorrow , Whiplash , About Time , Side Effects 


The top 10 ALS recommendations, have some recommendations common with Pearson correlation recommendations


## What we accomplished?

In our project proposal, we planned to develop a hybrid movie recommender system for Netflix platform based on the MovieLens 20M dataset, that can be implemented on distributed systems using spark.
- (a) definitely will do - Collaborative filtering using Pearson Correlation Algorithm
- (b) likely will do - Comparing the Pearson correlation result with cosine similarity 
- (c) would ideally like to do items - Content based filtering and Integrating the both filtering to make a hybrid recommendation system

We accomplished both (a) & (b). We implemented collaborative filtering using pearson correlation and compared with cosine similarity. 

Additionally we used ALS to train model and to calculate Root Mean Square Error value

## Comments & Observations

- Having never worked with spark, it was challange to learn how to integrate it with Google Colab platform.
- As the initial data is vast, when we tried running it on dsba-hadoop cluster, it took more than a day to run the pearson correlation, after which vpn connection got terminated.
- Reducing the dataset, has made the recommendations bit easier, however the cluster still took a little more than an hour to give recommendations. 
- Running the dsba-cluster for both pearson correlation and cosine similarity to test was a bit time consuming.
- We were surprised to find the recommendations made by both pearson and cosine, have very less similarity. For the random users tested, to get top 15 recommendations, atmost only 6-7 recommendations are same.
- We got to know how to use spark in regular python code and how to use map, filter, show commands using spark
- Also, this project made it easier, when studying for final - Recommender systems & spark topic

## Work Division

### Mahitha Garikipati
- Data cleaning
- Pearson Correlation Algorithm implementation 
- Cluster/Deployment in spark
- Cosine Similarity implementation
- Project Report

### Navya Gunti
- Fetching the data
- Alternating Least Squares algorithm implementation
- Cluster/Deployment in spark
- Testing Cosine Similarity for random users to compare with Pearson
- Project Report

## References

