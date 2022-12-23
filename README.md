{% include rating_per_user.html %}
{% include Treshold.html %}
{% include rating_per_location.html %}
## Redrawing borders using beer preferences

Several things unite people from all around the world together: watching football, listening to music and arguably, *drinking beer*.

These universal interests allow us to enjoy shared moments and put aside whatever differences we have. 

We hypothesize that people aren't so different after all.

We may come from very different places, but we can redraw those borders by sharing in the same good 'ol beers 🥰

![Drawing boundaries](/assets/boundaries.jpg)

If we break down preferences for beer styles into just two axes, we can easily visualize similarities between different countries' preferences for beers. 

Not every country has rated every type of beer style, so we used item-based collaborative filtering to fill in the gaps.

The result, after decomposing high-dimension preference vectors into two axes is a map, where the size of the bubbles tell us how many reviews came from that country.

/ insert graph here

It can be hard to visualize patterns from a set of axes which we're unfamiliar with. Instead, we decided to draw out similarities by clustering them and coloring these clusters on a map of the world.

The resulting world map is plotted below. Clicking on a country in the map brings the previous chart to focus on that country's preference vectors.
