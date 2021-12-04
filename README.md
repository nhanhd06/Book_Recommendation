# Collaborative Filtering Based Book Recommendation System
## Introduction

During the last few decades, with the rise of Youtube, Amazon, Netflix and many other such web services, recommendation systems have taken more and more place in our lives. From e-commerce to online advertisement, recommender systems are today unavoidable in our daily online journeys included provided video on demand, music streaming services, online shopping, and other various online entertainment forms. From communicating with old friends ot listening to songs while driving, recommendation system are everywhere.

In general way, it is form of algorithm aimed at suggesting relevant items to users like what kind of movies to watch, book to read, and products to buy.

Recommendation systems are really criticial in a lot of industries like Amazon and Netflix, where they don't have to use physical stores for customers to walk in and choose what they want. It is the other way around which there would a list of suggested items based on purschased history. Furthermore, it has already lead the world to the state which people could shop online simply by staying at home and clicked mouse to search. In fact, Amazon and Netflix are primary examples which doesn't reply a lot in physical locations but still provided best service and eventually generate a huge amount of revenue.

The primary goal of this project is to develop a book recommendation model using Kaggle Datasets that could suggest readers what books to read next

## Dataset

"Kaggle Dataset Link - https://www.kaggle.com/saurabhbagchi/books-dataset"
- books.csv - has metadata for each book (book-id, book-title, book-author, year-of-publication and publisher). The raw dataset has 8 columns and 271379 values
- ratings.csv - contains various user review ratings included user_id, book_id and ratings. It has 1149779 values
- users.csv - contains user common informatio primary like user-id, location and age. It has 244148 values

## Solution Phrase

The project would be organized into following steps

> **1. Data Processing:** 

The first step in this process is to figure out the ways to input the datasets using either upload directly from laptop or download straight from Kaggle in Google Colab.
After that, we quickly inspect all three datasets and identify how they are connected to each other and then perform data cleaning - (identify duplicates, missing values, deleted null values, and even merge different datasets to extract meaning information), so we would have proper and clean dataset for Data Exploratory. For instance, ISBN Field is chosen as inner join between Books and Ratings Datasets due to ISBN is the primary source to identify which review is belong to for a particular book and User-ID Field would be used as a connection between Ratings and Users Datasets since it is the only choice to identify different user identities

> **2. Data Exploratory:** 

In this step, the goal was to explore the clean datasets and try to understand how various columns such as categories, author, year of publication would affect the rating of a book. Furthermore, it helps to check out other columns which could be considered as a performance metric for different books or authors included how many reviews a book received and how many books an author published and how their ratings compare).

> **3. Data Training:** 

For data training, we would use Collaborative Filtering as training mode. If a system suggests items to user based on past interactions between users and items, that system is known as Collaborative Filtering System. In this type of recommendation algorithm, a user-item interactions matrix is created that every user and item pair each has a space in the matrix. That space is either filled with the user's rating of that item or is left blank. This could be implemented with matrix factorization which would show case when we develop our models. The important thing to remember with collaborative filtering is that user id, item id, and rating are the only fields required and split them into train data and test data

> **4. Data Evaluation:** 

In Data Evaluation, we would do an intuitive check on the recommendation algorithm included checking attributes of predict method or getting estimated rating for one particular ISBN from one random User-ID. We continue to evaluate its accuracy on the predict model and even try to get top 10 recommended books for one random User-ID in test set
