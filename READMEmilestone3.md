# It’s a beer’s, beer’s, beer’s world
## Abstract:
What if we re-arranged the world through beer taste? What would be the map resulting from it? What countries will be linked per their beer’s love? Can natural enemies become friends over a nice cold beverage? 

This project will have two phases: the first will be to find the best method to compute the favorite beer style per country, and the second to reassemble them according to the latter results.

For the first one, we will analyze several ways to find, and try to be as accurate as possible with the dataset given:  we plan to try various methods and libraries to generate the results, and compare the resultings insights we find, and hopefully tell an awesome, easy-to-follow story using a combination of maps and statistics.

Then, we will use those various methods to cluster the different countries, and observe the new world beer map!

## Research Questions:
1. What is the best method to find the favorite beer per country?
2. What happens if we draw the world’s boundaries using beer preferences?

## Proposed additional dataset:

[Dataset of the geographical coordinates of each country’s centroid](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv)
- Publicly available on the internet
- Used to help with creating data points for the maps

## How we intend to work towards answering the questions:

**What’s the best way to determine each country’s beer preferences?**
1. Work out the best parameters for cleaning and filtering the data
    - Two thresholds seem unskippable to make analysis over country : the number of users per country to have a sufficient sample, and the number of ratings per user to be a reliable source of information as citizen’s taste. 
    - Determine if thresholds should be set for filtering out beers which do not have enough reviews written for them or users who do not write enough reviews.
2. Identify each country’s favorite beer style:
    - For each set of beer reviews corresponding to users from one country, calculate the mean rating for each beer style and identify the beer style with the highest mean rating.
        - We will study the sensibility of the 2 thresholds onto the results and try to find a compromise : best reliable results will still have sufficient data to make the analysis.
        - Is every user’s rating “worth” the same? We will observe the results with weighted users based on their number and non-binarity (0 or 5 ratings)
3. Visualize these preferences on a map, likely using the Folium library:
    - For each country’s favorite beer style, we can utilize color coding to highlight countries which share the same preferences for particular beer styles, and examine if patterns arise from there.

**What happens if we draw the world’s boundaries using beer preferences?**
1. Clustering by favorite beer styles
    - We can join together the boundaries of adjacent countries which share the same favorite beer styles, thereby creating subregions/clusters.
    - If data sparsity is not an issue, we can try performing this visualization over different periods of time to understand how these clusters have been changing.
2. Clustering by average beer preferences
    - We can construct vectors for each country, where values represent the average ratings for each beer style, and cluster countries by either euclidean distance or cosine similarity.
    - We can simplify these vectors using scikit-learn’s PCA library to transform each vector into a two dimensional space, and plot the resulting clusters in a way that is easier to visualize.
3. Analysis of clusters
    - Depending on the results, we might be able to identify how clusters with similar beer preferences may share other similar characteristics (e.g. proximity to the coast, influence from particular countries through colonialism, climate etc.)

## Proposed timeline:
Here’s the dates we expect to complete our analysis for the different research questions:
- Research Question 1 by 10/12
- Research Question 2 by 17/12
- Data Story and Notebook by 21/12

## Organization within the team:
We decided to divide the work into two sub-teams, so that we can benefit from teamwork efficiency, and work on things in parallel. Each sub-team is responsible for doing its part, and we meet regularly with the entire group to share our advancement, methods and discuss the next steps to work on. This allows us to provide feedback to each other while working on the same topic.

## Question for the TA’ s

What is your favorite beer?
Which method are you recommending for clustering?
Which method do you think gives the more accurate result in your opinion?
