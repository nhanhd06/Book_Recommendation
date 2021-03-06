# Collaborative Filtering Based Book Recommendation System
## Group Team Members

Nhan Dao - Weifeng Ma - Duong Cao

Presentation Link - https://www.youtube.com/watch?v=zUswav06-eI

Slide Link - https://docs.google.com/presentation/d/1BNFwHiI29aaAL8YaXZ2y-hLKmPVpVymQ-cIQwXYT-F0/edit?usp=sharing

## Introduction

During the last few decades, with the rise of Youtube, Amazon, Netflix and many other such web services, recommendation systems have taken more and more place in our lives. From e-commerce to online advertisement, recommender systems are today unavoidable in our daily online journeys included provided video on demand, music streaming services, online shopping, and other various online entertainment forms. From communicating with old friends ot listening to songs while driving, recommendation system are everywhere.

In general way, it is form of algorithm aimed at suggesting relevant items to users like what kind of movies to watch, book to read, and products to buy.

Recommendation systems are really criticial in a lot of industries like Amazon and Netflix, where they don't have to use physical stores for customers to walk in and choose what they want. It is the other way around which there would a list of suggested items based on purschased history. Furthermore, it has already lead the world to the state which people could shop online simply by staying at home and clicked mouse to search. In fact, Amazon and Netflix are primary examples which doesn't reply a lot in physical locations but still provided best service and eventually generate a huge amount of revenue.

The primary goal of this project is to develop a book recommendation model using the Book-Crossing dataset, which includes book, user and ratings dataset.

## Collaborative Filtering
![image](https://user-images.githubusercontent.com/32551600/145658137-2a48ba82-ce45-43dd-a028-669ef594f519.png)<br />
In this project, the technique, collaborative filtering, is applied. In collaborative filtering, algorithms are used to make automatic predictions about a user's preferences by compiling preferences from other users.

## Dataset

"Kaggle Dataset Link - https://www.kaggle.com/saurabhbagchi/books-dataset"

1. books.csv
   This dataset contains books being identified by their ISBN Number. Book Information included Book-Title, Book-Author, Year-Of-Publication, and Publisher is given here. URLs    Linking which covers different book cover are also showned as well in small, medium, and large formats ('Image-URL-S', 'Image-URL-M', 'Image-URL-L').

2. ratings.csv
   This contains all of book rating reviews info included target associcated ISBN and reviewer User-ID too on a scale from 1 - 10 but not 0 = Not giving any review
   
3. users.csv
  This would act as all users information included an User-ID and some demographic data - Location and Age 

## Project Overview
![image](https://user-images.githubusercontent.com/32551600/145658323-67bc70e9-e109-47a2-92da-19d753b93505.png)<br />
We followed the steps from KDD model, knowlege discovery in databases. <br />

The project would be organized into following steps

> **1. Data Processing:** 

The first step in this process is to figure out the ways to input the datasets using either upload directly from laptop or download straight from Kaggle in Google Colab.
After that, we quickly inspect all three datasets and identify how they are connected to each other and then perform data cleaning - (identify duplicates, missing values, deleted null values, and even merge different datasets to extract meaning information), so we would have proper and clean dataset for Data Exploratory. For instance, ISBN Field is chosen as inner join between Books and Ratings Datasets due to ISBN is the primary source to identify which review is belong to for a particular book and User-ID Field would be used as a connection between Ratings and Users Datasets since it is the only choice to identify different user identities

> **2. Data Exploratory:** 

In this step, the goal was to explore the clean datasets and try to understand how various columns such as categories, author, year of publication would affect the rating of a book. Furthermore, it helps to check out other columns which could be considered as a performance metric for different books or authors included how many reviews a book received and how many books an author published and how their ratings compare).<br />
![image](https://user-images.githubusercontent.com/32551600/145658847-e648e420-6444-4567-aa42-677ad3689b26.png)<br />
Figure 1: Year and book released count <br />
![image](https://user-images.githubusercontent.com/32551600/145658895-e652f0b8-61d7-4ba3-9b26-2080a03bface.png)<br />
Figure 2: Book rating and count <br />
![image](https://user-images.githubusercontent.com/32551600/145659003-3b53e203-9be1-49b7-ae24-bd1797e41764.png)
Figure 3: Top 20 books(name) with highest book rating count <br />
![image](https://user-images.githubusercontent.com/32551600/145659049-cce75735-c663-4b9a-9d12-2b673a267723.png)
Figure 4: Average rating distribution for all books <br />
![image](https://user-images.githubusercontent.com/32551600/145659163-b08ff064-56ab-49cd-ac8e-ca7b67aa8261.png) <br />
Figure 5: Top 10 authors who been selected by users <br />
![image](https://user-images.githubusercontent.com/32551600/145659130-d13af279-39fa-4a65-91a8-0bef6a8cf3e3.png) <br />
Figure 6: Relation between Rating counts and year of publication <br />
(For more detail of graphs and visualization, please open and follow the Colab.) <br />

> **3. Data Training:** 

For data training, we would use Collaborative Filtering as training mode. If a system suggests items to user based on past interactions between users and items, that system is known as Collaborative Filtering System. In this type of recommendation algorithm, a user-item interactions matrix is created that every user and item pair each has a space in the matrix. That space is either filled with the user's rating of that item or is left blank. This could be implemented with matrix factorization which would show case when we develop our models. The important thing to remember with collaborative filtering is that user id, item id, and rating are the only fields required and split them into train data and test data

> **4. Data Evaluation:** 

In Data Evaluation, we would do an intuitive check on the recommendation algorithm included checking attributes of predict method or getting estimated rating for one particular ISBN from one random User-ID. We continue to evaluate its accuracy on the predict model and even try to get top 10 recommended books for one random User-ID in test set

## Algorithm Implementation

We will use the method of collaborative filtering to build the system. Collaborative Filtering is try to search for those viewers/readers who have similar preference like you and offer products based on what his/her lookalike has chosen. To make that approch, we will use a method to find the distance between data points, in this case, are the book title, ratings, and other features <br />

Before delving into the implementation of the model, it is convenient to have a subtle understanding of vectorization is. The vectorization algorithm used for recommendations works by decomposing the user-item interaction matrix into the product of two low-dimensional rectangular matrices. The figure below illustrates this idea at a high level:
![image](https://user-images.githubusercontent.com/32551600/145659467-b3d7c8a9-66ae-4ef1-b69e-d830f0428f59.png) <br />
by definition, Cosine similarity measures the similarity between two vectors by calculating the cosine of the angle between them. <br />
![image](https://user-images.githubusercontent.com/32551600/145659479-d4446e72-e2d1-4307-8d8b-a1ab658b1593.png) <br />
<pre>
from sklearn.neighbors import NearestNeighbors


model_knn = NearestNeighbors(metric = 'cosine', algorithm = 'brute')
model_knn.fit(us_canada_user_rating_matrix)
</pre>
We used the distance metric from KNN, to find the closest data points.
<br />

Conclusion: The one used Cosine similarity provided the better result. The reason is that Eucdiean distance and L1 distance both do not take angle. If the data objects are far apart, they could still have a smaller angle between them. When we try to find the similar target(books), it all depends on angle of data objects. Smaller the angle, higher the similarity. <br />
<br />
## Reference  
Image: 
https://towardsdatascience.com/brief-on-recommender-systems-b86a1068a4dd <br />
https://akoios.medium.com/building-a-movie-recommender-system-e2384328a134 <br />
https://medium.com/@mark.rethana/building-a-song-recommendation-system-using-cosine-similarity-and-euclidian-distance-748fdfc832fd <br />
