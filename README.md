# Generalized Additive Models for IMDB Movie Ratings

IMDb is an online database of information related to films, television programs, and video games. It also provides average ratings voted by users. In this project, I conducted an exploratory data analysis to examine the relationship between the runtime, release year, and average ratings of movies, using data obtained from two datasets available on https://datasets.imdbws.com: title.ratings.tsv.gz and title.basics.tsv.gz.

## Generalized Additive Models

In linear regression models, linearity refers to its property of summarizing the relationship between a feature and prediction by a single number. It means that regardless of the value an instance has in a particular feature, increasing the value by one unit alwasy has the same effect on the predicted outcome. While this property provides clear explanation on how predicted value changes depending only on the feature of interests, the linearity often has limited ability to illustrate the true relationships observed in the real world.

For example, let's say that we have a data of the number of rental bikes and the temperature. Intuitively, one expects that increasing the temperature from 10 to 11 degrees Celsius has a positive effect on bicycle rentals and from 40 to 41 a negative effect, which is also the case. The temperature has a linear, positive effect on the number of rental bikes, but at some point it flattens out and even has a negative effect at high temperatures. 

Generalized Additive Models (GAMs) is a one possible solution to model nonlinear relationships. 
