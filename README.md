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


{% include ratings_per_user.html %}
{% include Threshold.html %}
{% include users_per_location.html %}
{% include weight.html %}


## 1. What is the favorite beer per country?

First of all let's talk the data used for our analysis.

<img align="right" width="250" height="250" src="ratebeer.png">

All come from the website [RateBeer](https://www.ratebeer.com/), which is, according to them : *widely recognized as the most in-depth, accurate, and one of the most-visited source for beer information. [...] RateBeer is a consumer-driven Web site and we strive to remain unbiased in our ratings and editorial content.*

On this website, users can enter their country of origin


## 3. Redrawing borders using beer preferences

![Drawing boundaries](/assets/boundaries.jpg)

Several things unite people from all around the world together: watching football, listening to music and arguably, *drinking beer*. These universal interests allow us to enjoy shared moments and put aside whatever differences we have. 

We hypothesize that people aren't so different after all.

We may come from very different places, but we can redraw those borders by sharing in the same good 'ol beers 🥰

If we break down preferences for beer styles into just two axes, we can easily visualize similarities between different countries' preferences for beers. Not every country has rated every type of beer style, so we used item-based collaborative filtering to fill in the gaps.

The result, after decomposing high-dimension preference vectors into two axes is a map, where the size of the bubbles tell us how many reviews came from that country.

<iframe width="1200" height="800" src="https://datastudio.google.com/embed/reporting/e19fe6eb-0b94-4976-ac9f-4a45fa8dde40/page/218AD" frameborder="0" style="border:0" allowfullscreen></iframe>

It can be hard to visualize patterns from a set of axes which we're unfamiliar with. Instead, we decided to draw out similarities by clustering them and coloring these clusters on a map of the world.

The resulting world map is plotted below.

<iframe width="1200" height="400" src="https://datastudio.google.com/embed/reporting/e19fe6eb-0b94-4976-ac9f-4a45fa8dde40/page/p_l0bphrvq1c" frameborder="0" style="border:0" allowfullscreen></iframe>

Surprisingly, beer preferences are much less region specific. While Argentina, Chile, Brazil and Uruguay sharing the same 
# Conclusion


test donglin
{% include top_3_country_time.html %}
