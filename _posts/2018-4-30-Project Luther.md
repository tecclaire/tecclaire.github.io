---
layout: post
title: What Rates A Good Book?
---

For my second project at metis, I got to use Selenium and BeatifulSoup for web scraping, and to apply linear regression to make predictions. It's challenging but I'm happy to have this exprience in accomplishing a complete circuit of a data science project.

## Question:
Goodreads is an unique website. It's like the IMDB for books, and the users are like your book lover friends who are passionate about sharing their favorite books with you. Fun fact -- 19 percent of Americans do 79 percent of all our (non-required) book reading, and 11 percent of book buyers make about 46 percent of recommendations. That's why Goodreads is important -- it reflects the tastes and likings of the most active book buyers. Therefore, I would like to look into what factors contribute to high ratings of books on Goodreads and what the readers like/dislike.

## Data:
I collect information of 1000 books from the [Best Books Ever](https://www.goodreads.com/list/show/1.Best_Books_Ever?order=d&page=1) list on Goodreads. Each book obtains numerical features such as number of ratings, reviews, awards, and pages etc., as well as categorcial features like author and genres. My goal is to use the numerical and categorical features in a linear agression model, and to see which features play a major role in deciding a book's rating.



## Analysis:
My first step is to plot ratings against other indepent variables using Seaborn. Seen in the image below, the ratings look noramlly distributed, but for most other variables the graph is skewed to the right. 

![_config.yml]({{ site.baseurl }}/images/project2-images/ORating.png)


Next, I would like to use Patsy to perform a linear regression analysis over the variables. To take consideration of the skewed images, I ran two linear regressions, one with the original variables and one with logged variables.

![_config.yml]({{ site.baseurl }}/images/project2-images/patsy.png)

For Rating ~ all variables, our R^2 is very high at 0.91. I took out all the author categories and ran patsy again, and R^2 drops to be around 0.5. Author definitely plays an important role in the ratings here. However, our modeling can't stop here. I ran a train and test over this model and our data is definitely overfit, with R^2 drops to 0.25. so I use Ridge and Lasso for regularization and hope they can help me pick the most efficient coefficients. 

![_config.yml]({{ site.baseurl }}/images/project2-images/ridge.png)

With ridge, our R^2 climbs to be 0.37. 

![_config.yml]({{ site.baseurl }}/images/project2-images/lasso.png)

The lasso R^2 is 0.31, which is still an improvement. The linear model using the given features can only explain a moderate portion of the  factors for rating, which seems reasonable. It's so hard to "explain" and "predict" creative products...

## Conclusions:
I let lasso pick the leading coefficients for Rating ~ all variables as in the table below.

| Postive Coefs |  | Negative Coeffs | |
| --- |---| --- | --- |
| NPages | 0.074 | School | -0.039|
| Sarah J. Maas | 0.031 | Dan Brown | -0.036 |
| Karen Marie Moning | 0.025 | Stephenie Meyer | -0.029 | 
| Ki Longfellow | 0.025 | Fiction | -0.025 |
| Graphic Novels | 0.025 | Alyson Noel | -0.023 |
| Brandon Sanderson | 0.022 | T.Elizabeth Gilbert | -0.022 |
| J.K. Rowling | 0.021 | Gregory Maguire | -0.021 |
| 20th Century | 0.021 | Literature | -0.019 |
| PubYear | 0.021 | James Joyce | -0.019 |
| Jorge Luis Borges | 0.021 | James Frey | -0.018 |

Our model shows author matters to ratings - readers show postive or negative preferences of authors. It's interesting to see such a negative downgrade of school-related readings. Longer books, graphic novels, and more recent books (PubYear) can enhance ratings, too. 


---

_To view the presentation of this project, please click [here](https://docs.google.com/presentation/d/1JXcYnJz5_Oo0HUx2ZKmj6m6YP0HZ-3CSD0XGxaFK6Ks/edit?usp=sharing)._
