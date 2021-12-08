## ITCS-6190 Group-3 Netflix Recommender System
#### Mahitha Garikipati - mgarikip@uncc.edu
#### Navya Gunti - ngunti@uncc.edu

### Overview
The purpose of this project is to implement Netflix Recommender System by using cloud computing concepts.

The concepts implemented are - Person Correlation Coefficient, Alternating Least squares using Cosine Similarity algorithms

These algorithms made use of pySpark framework for implementing the collaborative filtering to recommend movies to given user.

This project made use of dsba-hadoop cluster provided by the university for storing the data and to deploy the code.

### Tasks Involved and approach
- Fetching Netflix movie datasets
- Understanding of Algorithms to implement
- Analyzing the datasets
- Cleaning the dataset
- Configuring GoogleColab Notebook with spark
- Implementing Pearson Correlation Coefficient Algorithm
- Implementing Alternating Least Squares using Cosine similarity
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

#### Datasets

The dataset that is to be implemented in this project will be MovieLens 20M dataset provided by Kaggle. 

The link to this dataset can be found [here](https://www.kaggle.com/grouplens/movielens-20m-dataset)

The size of the data is around 693 MB and contains details about the user id, movie id, ratings, timestamp, movie title, year of movie release, genres. 

This dataset contains around 20 Million ratings on 27 thousand movies which are given by 138 thousand users. 

###  About our modified dataset:

Due to the difficulty in computing the ( 20 Million ratings * 27 thousand movies) using dsba-hadoop cluster, the amount of data is reduced

The number of movies originally contains data from (1995 - 2015). 

However, for this project, only 3 year movies are considered (2013 - 2015) and their corresponding users and ratings.

Total number of movies = 1878

Total number of ratings = 5112

A total of 397 users are considered for this Netflix Recommender System

SInce, the name of the user is not available in the dataset, user id is considered. The set of user id are as follows: 

[31,71,96,107,133,136,162,176,208,213,215,248,260,271,279,284,285,318,342,370,398,425,455,459,466,520,521,540,551,572,577,586,596,614,631,637,692,707,710,713,729,735,768,770,786,804,808,828,829,843,851,858,866,887,891,898,910,964,969,975,979,1048,1108,1141,1217,1228,1239,1244,1246,1257,1268,1271,1274,1277,1319,1331,1339,1341,1344,1433,1468,1518,1520,1527,1551,1559,1588,1602,1629,1644,1678,1703,1705,1721,1734,1741,1755,1761,1775,1837,1848,1853,1877,1948,1958,1968,1979,1996,2047,2068,2084,2093,2095,2138,2161,2188,2189,2208,2219,2269,2270,2287,2295,2298,2301,2310,2333,2367,2368,2414,2421,2423,2425,2449,2460,2515,2517,2535,2544,2568,2586,2606,2650,2657,2669,2702,2713,2742,2751,2813,2835,2874,2908,2928,2930,2959,2974,2988,3004,3020,3029,3031,3038,3070,3127,3149,3156,3163,3181,3205,3240,3251,3257,3267,3268,3282,3289,3326,3358,3364,3386,3397,3409,3413,3419,3429,3446,3448,3453,3456,3487,3490,3523,3529,3563,3589,3618,3634,3640,3660,3668,3676,3683,3693,3751,3797,3845,3846,3858,3867,3878,3884,3896,3990,4026,4039,4055,4063,4066,4087,4089,4165,4181,4222,4223,4257,4270,4274,4279,4281,4305,4347,4380,4405,4430,4450,4464,4468,4472,4488,4515,4537,4541,4550,4563,4571,4575,4587,4590,4596,4605,4627,4629,4635,4658,4660,4709,4745,4752,4759,4780,4793,4812,4813,4822,4829,4851,4855,4877,4910,4957,4965,4967,4968,5002,5004,5036,5037,5050,5058,5077,5080,5107,5125,5130,5138,5160,5181,5192,5208,5219,5242,5259,5264,5279,5288,5298,5309,5315,5337,5347,5352,5353,5359,5378,5417,5423,5440,5442,5443,5446,5457,5475,5489,5495,5514,5517,5529,5540,5550,5622,5643,5665,5718,5731,5763,5792,5800,5810,5823,5832,5840,5857,5871,5911,5928,5930,5952,5954,5973,5980,6039,6088,6112,6125,6148,6166,6171,6175,6184,6233,6236,6268,6308,6310,6325,6339,6340,6390,6412,6429,6441,6455,6472,6507,6524,6554,6632,6637,6646,6702,6721,6723,6750,6788,6832,6838,6881,6894,6899,6915,6939,6961,6970,6995,7007,7016,7027,7036,7038,7042,7047,7064,7066,7074,7086,7090] 

Any of these user id's can be selected inorder to get recommendations based on other users ratings.


### Pearson Correlation Coefficient Algorithm
The algorithm is tested to check the efficiency for some users which are listed above

1) For user id = 31, the ratings of the movies are as follows
  ![image](https://user-images.githubusercontent.com/20443793/145141226-d5a0b0d6-9e54-4fd1-aa9e-9031e0915c21.png)
  
   The top 15 recommendations obtained for this user 31 are 
   
    'Penguins of Madagascar ', 'Frank ', "Internet's Own Boy: The Story of Aaron Swartz, The ", 'Bridegroom ', 'Great Beauty, The (Grande Bellezza, La) ', 'Sound City ', 'Louis C.K.: Oh My God ', 'Citizenfour ', 'Leviathan ', 'Jackass Presents: Bad Grandpa .5 ', 'Horns ', 'Coherence ', 'Proxy ', 'Sacrament, The ', 'Raze '

    
2) For user id = 540,
   ![image](https://user-images.githubusercontent.com/20443793/145141388-4ffcac6e-3be0-4a28-acef-1686a6956c5d.png)
   The top 15 recommendations obtained for this user 540 are 

3) For user id = 979,
   ![image](https://user-images.githubusercontent.com/20443793/145141737-1708a8f6-08aa-4548-87a0-a65a7386ffe2.png)
   The top 15 recommendations obtained for this user 979 are 

4) For user id = 1588,
   ![image](https://user-images.githubusercontent.com/20443793/145141938-3eba587f-6a37-4171-bc83-ea8aa4c58ad7.png)
   The top 15 recommendations obtained for this user 1588 are 

5) For user id = 2460
   ![image](https://user-images.githubusercontent.com/20443793/145142114-160c7ca2-876e-41d3-b4bb-4648e78e5e01.png)
   The top 15 recommendations obtained for this user 2460 are 

6) For user id = 3251
   ![image](https://user-images.githubusercontent.com/20443793/145142198-209d3ec3-a823-456d-848e-e27e056df426.png)
   The top 15 recommendations obtained for this user 3251 are 
   
7) For user id = 3845
   ![image](https://user-images.githubusercontent.com/20443793/145142295-447045ef-cf22-44eb-bcc2-02ebb735d36b.png)
   The top 15 recommendations obtained for this user 3845 are 

8) For user id = 4541
   ![image](https://user-images.githubusercontent.com/20443793/145142501-2f1ffade-ca77-4907-a4ce-9fda48beb2e6.png)
   The top 15 recommendations obtained for this user 4541 are 

9) For user id = 6175
   ![image](https://user-images.githubusercontent.com/20443793/145142906-26b59fe6-e358-4c87-a643-e90b54582782.png)
   The top 15 recommendations obtained for this user 6175 are 

11) For user id = 7027
   ![image](https://user-images.githubusercontent.com/20443793/145142652-ef53a263-4e91-4767-9b78-aa6f87b98a6b.png)
   The top 15 recommendations obtained for this user 7027 are 


### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mahithagarikipati/NetflixRecommenderSystem/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
