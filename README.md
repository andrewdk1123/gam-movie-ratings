# Generalized Additive Models for IMDB Movie Ratings

IMDb is an online database of information related to films, television programs, and video games. It also provides average ratings voted by users. In this project, I conducted an exploratory data analysis to examine the relationship between the runtime, release year, and average ratings of movies, using data obtained from two datasets available on https://datasets.imdbws.com: title.ratings.tsv.gz and title.basics.tsv.gz.

## Generalized Additive Models

In linear regression models, linearity refers to the property of summarizing the relationship between a feature and prediction by a single number. This means that the predicted outcome changes by the same amount for a one-unit increase in the feature throughout the entire values of the feature. While this property provides a straightforward and concise explanation of how predicted values change based on a feature of interest, it often has limited ability to capture the complex, nonlinear relationships observed in the real world.

For example, consider a dataset containing the number of rental bikes and the temperature. Intuitively, one would expect that increasing the temperature from 10 to 11 degrees in Celsius has a positive effect on bicycle rentals, while increasing it from 40 to 41 has a negative effect. The temperature has a linear, positive effect on the number of rental bikes, but it eventually flattens out and even has a negative effect at high temperatures.

Generalized Additive Models (GAMs) is a one possible solution to model such nonlinear relationships. GAMs relax the linearity assumption in linear models and allow for the outcome to be modeled as a sum of arbitrary functions of each feature, as shown below:

$$
g(E(y|X=x)) = \beta_0 + f_1(x_1) + f_2(x_2) + \cdots + f_p(x_p)
$$

In the above formula, we can see that the $\beta_ix_i$ terms in the linear regression model is replaced by $f_i(x_i)$, which is a more flexible approach that can capture nonlinear relationships. In the meantime, at its core, GAMs still represent predictions in the form of additive models. This additive property of GAMs allows us to decompose the predictions by each feature, so that we can explore the effects of features independently of the otehr features. Such an approach makes the results of the model easy to interpret and helps to identify which predictors are most important in explaining the response.
 
One big remaining question is how to learn nonlinear functions. To fit nonlinear relationships, GAMs use splines. Splines are functions that are built from simpler basis functions and can approximate complex functions. It is similar to constructing a more complicated Lego structure by stacking simpler blocks together. For example, a cubic function is a polynomial function of degree 3 and is of the form $f (x) = ax^3 + bx^2 + cx + d$, where $a$, $b$, $c$, and $d$ are real numbers and $a \neq 0$. A cubic spline is a spline that is made up of three basis functions: a linear function, a quadratic function, and a cubic function. The linear function allows for a straight line relationship, the quadratic function allows for a curved relationship, and the cubic function allows for a more complex curved relationship. These basis functions are combined in a way that allows them to approximate other, more complex functions.

To build intuition, let's consider a simple example where we have a single feature, $x$, and we want to model its relationship with the response, $y$. A linear model would represent this relationship as:

$$
y = \beta_0 + \beta_1 x + \varepsilon
$$

where $\beta_0$ and $\beta_1$ are the intercept and slope coefficients, respectively, and $\varepsilon$ is the error term. However, this model assumes a linear relationship between $x$ and $y$, which may not always be the case in practice. To model non-linear relationships, we can use a spline function to represent the effect of $x$ on $y$. A spline function is a piecewise polynomial function that is defined on intervals, where each interval has a different polynomial function. The idea is to estimate the coefficients of each polynomial function in a way that makes the spline function smooth and continuous across the intervals.

For example, suppose we want to model the relationship between temperature and bike rentals, where the relationship is expected to be non-linear. We could use a set of spline functions to represent the effect of temperature on bike rentals, where each spline function corresponds to a different interval of temperature values. The value of each spline function at a particular temperature value would depend on the coefficients estimated from the data for that interval.

Once the spline functions are defined, GAMs estimate the coefficients of each function using a form of regression analysis. The estimated coefficients represent the effect of each predictor variable on the response, taking into account any non-linearities in the data. The smoothness parameter, which controls the flexibility of the spline functions, is chosen using cross-validation to find the optimal balance between bias and variance.
