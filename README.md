## Abstract:
It is not impetuous to say that during his lifetime, the majority of the human beings on earth will have tasted the cold and sweet beverage that is called beer. Some may dislike it, some may love it a little bit too much, but the least to say is that every body has some word about it. 

Indeed, not only this drink is universal, but it's also widely diverse in taste, style, ingredients, ... . A real spectrum of variety across the different cultures of the world. Of course, with today mondialisation, every style is not confined to its region of origin anymore, it had the chance to spread across borders and oceans. That let people around the globe able to enjoy any kind they want.

This variety opened a endless debate : what is the best beer? The answer will always be impossible to find, as objectivity does not have its place here : the opinion of someone is greatly biaised by its taste, country of birth, social condition,... . Trying to make your voice heard may make tones and emotions rise and lead to severe tensions, which is the opposite of the desired atmosphere when filling the glasses.

However, another question can be answered : what is the preferred beer of all? Moreover, can people with very different origins find common ground around a full to the brim pint?






## Goal
What if we re-arranged the world through beer taste? What would be the map resulting from it? What countries will be linked per their beer’s love? Can natural enemies become friends over a nice cold beverage? 

This project will have two phases: the first will be to find the best method to compute the favorite beer style per country, and the second to reassemble them according to the latter results.

For the first one, we will analyze several ways to find, and try to be as accurate as possible with the dataset given:  we plan to try various methods and libraries to generate the results, and compare the resultings insights we find, and hopefully tell an awesome, easy-to-follow story using a combination of maps and statistics.

Then, we will use those various methods to cluster the different countries, and observe the new world beer map!




## 1. What is the favorite beer per country?

First of all let's talk about the data used for our analysis.

<img align="left" width="200" height="200" src="images\ratebeer.png">

All come from the american website [RateBeer](https://www.ratebeer.com/), which is, according to it : *widely recognized as the most in-depth, accurate, and one of the most-visited source for beer information. RateBeer is a world site for craft beer enthusiasts and is dedicated to serving the entire craft beer community through beer education, promotion and outreach. is a consumer-driven Web site and we strive to remain unbiased in our ratings and editorial content.*

On this website, users can rate beers on 4 aspects : appearance, aroma, palate and taste, and they can add a text review to comment their opinion. Each users can encode its country (we will assume that they entered their real one), which will be very useful here, and write as many ratings as he likes:


{% include ratings_per_user.html %} 


### Cut the weeds

As we can see, a large number of users only leave one or very few ratings. As our purpose is to compute the preferred style for the users, the one that leave almost no ratings are of very litte help to achieve it. So, as well as the website methods to compute the average score of a beer ([RateBeer Quality assurance](https://www.ratebeer.com/ratingsqa.asp)), we will need to take out users under a certain threshold of ratings.

Moreover, the same reasonning can be applied for the countries : if we do not have enough users for a certain country, does it make sens to compute its favorite style? Will it really be representative of its population?

Unfortunately we cannot only look at the precision and correctness of our result : indeed, what is the point of having expert users and countries ith thousands of reviewers if we end up with 2 countries only? We had to make a compromise between plentiness and quality of data: 

{% include Threshold.html %} 

Our choice is to keep users with at least 8 ratings, and country with at least 10 users.

Let's look at the remaining countries :

{% include users_per_location.html %}

Without surprise, we see that the main place represented is the USA, home of the website. Next we have Europe in second place, with each cardinal points more or less equal in number of users.

### Is it a democraty?

The answer is no. Not every user worth the same in term of opinion : we already took out the ones without a sufficient rating history.

In addition, some users can have binary rating (0 or 20) to favor their opinion in the overall site rating. Also, we could see the opinion of expert (people with a lot of rating), more representatif than some amateur. 

So we decided to apply a weight to all users, in the order to try to be as accurate as possible.

\
<span style="color:red;font-weight:700;font-size:20px">
    Warning :
</span>
<span style="color:red;font-weight:700;font-size:15px">
    This section will contain some math. If the reader has mathophobia, please skip to the next section. Reader discretion is advised
</span>

2 factors need to be taken into account : 

1. **Binarity** : 

![image](images\equ1.png)


The factor is always between 0.1 and 1. The factor 10 is arbitrary, but help to reduce the influence of those users while still keeping their rating into account, and avoid sparcity of the data.



2. **expertise** : 
$$weight_2 = \frac{log(number\space of\space rating)}{log(users\space threshold)}$$


This factor is equal to 1 at the minimum, and increase with the number of review.

The final weight will be the product of those 2 weigths.

$$Weight_{tot} = weight_1 \cdot weight_2$$


<span style="color:red;font-weight:700;font-size:20px">
    End of math
</span>


A the end, we see the repartition of the different users, with a spike around 1 : a grand proportion does not have a great number of ratings, but still are not binary reviewers.
{% include weight.html %}


### Old beer lovers
These data were collected at the Beer Rate site during the period 2001 to 2017. Although we have 18 years of data, our analysis will not focus on the first few years as there is not enough data to make an accurate analysis. As you know, the popularity of the internet continues to grow and therefore it is not surprising to see an increase in reviews over the years. It is also worth mentioning that Rate Beer is a website and at the beginning it is not easy to get users to review beers. These two factors explain why there has been an increase in users over the years. It is even noticeable that this site had a linear growth. 

However, in 2018 there has been a decrease in reviews, but this is completely logical as the data for the site was collected in the middle of the year. For this reason we will carry out our analysis up to 2017.
{% include ratings_over_time.html %} 

## 3. Redrawing borders using beer preferences

![Drawing boundaries](/assets/boundaries.jpg)

Several things unite people from all around the world together: watching football, listening to music and arguably, *drinking beer*. These universal interests allow us to enjoy shared moments and put aside whatever differences we have. 

We hypothesize that people aren't so different after all.

We may come from very different places, but we can redraw those borders by sharing in the same good 'ol beers 🥰

If we break down preferences for beer styles into just two axes, we can easily visualize similarities between different countries' preferences for beers. Not every country has rated every type of beer style, so we used item-based collaborative filtering to fill in the gaps.

The result, after decomposing high-dimension preference vectors into two axes is a map, where the size of the bubbles tell us how many reviews came from that country.

<iframe width="1200" height="800" src="https://datastudio.google.com/embed/reporting/e19fe6eb-0b94-4976-ac9f-4a45fa8dde40/page/218AD" frameborder="0" style="border:0" allowfullscreen></iframe>

It seems rather fitting that Tanzania, Kazakhstan and Namibia are some of the outliers in this graph. To be honest, we're not familiar with the beers that these countries enjoy, but maybe only those brave enough to travel there will ...

However, it can be hard to visualize patterns from a set of axes which we're unfamiliar with. We decided to draw out similarities by clustering them and coloring these clusters on a map of the world.

The resulting world map is plotted below.

<iframe width="1200" height="400" src="https://datastudio.google.com/embed/reporting/e19fe6eb-0b94-4976-ac9f-4a45fa8dde40/page/p_l0bphrvq1c" frameborder="0" style="border:0" allowfullscreen></iframe>

Surprisingly, beer preferences are much less region specific. While Argentina, Chile, Brazil and Uruguay sharing the similar beer preferences may not shock anyone, who would have thought Russia, Ukraine and the United States would share similar preferences? Or let alone Canada and China?




# Conclusion


test donglin

graph 1:

{% include top_three_beers_time.html %}

graph 2:

{% include top_3_country.html %}
