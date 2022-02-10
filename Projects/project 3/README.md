# Project 3 : Urban Planning and Sustainabilty

### Description



For project 3, your goal is two-fold:
1. Using [Pushshift's](https://github.com/pushshift/api) API, you'll collect posts from two subreddits of the urban planning and sustainability.
2. You'll then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.


#### About the API

Pushshift's API is fairly straightforward. For example, if I want the posts from [`/r/boardgames`](https://www.reddit.com/r/boardgames), all I have to do is use the following url: https://api.pushshift.io/reddit/search/submission?subreddit=boardgames

To help you get started, we have a primer video on how to use the API: https://youtu.be/AcrjEWsMi_E

**NOTE:** Pushshift now limits you to 100 posts per request (no longer the 500 in the screencast).

---
 
As the world is developing  , where the population , the infrastructures are increasing , we are looking on new ways and better ways to improve our quality of life .There is a need to improve it  socially, economically and in regards of the environment.

This project is presented to the city officials and urban planners who are looking for a way to improve the sustainability of the cities.

Sustainability need to be a great key for a good urban plan.


## Problem statement
This project is aiming to help urban planners design and plan not only for this generation but also for the future  by understanding the area that need to be more focused on in order to achieve sustainability.


## Conclusion
My recommendation for the urban planners are to incorporate more elements regarding climate change , waste management and energy and and also non-motorized mode of transportation such as bike lanes. The best model to use also in this case will be Multinomial Naives Bayes model because even though it doesn’t have a highest accuracy score the f-1 score is high which is the mean between precision and recall.