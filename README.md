# TidyTuesday260512
Python Exercise with Tidy Tuesday Data

## Overview
After my last Python exercise, I was looking for something that 1)Used Pandas and more data science-y data than my app, 2) Was a quicker turnaround than spending a month coding an app and 3) was a little more digestable to a non-mathematics crowd. I found the [Tidy Tuesday group](https://tidytues.day), and decided to start there. I'll admit that this was a little more algorithmic and less data crunchy than I was hoping for initially, but had a ton of fun working through an algorithm to create clusters based on city connections. Noticing that I really enjoy working on optimizing algorithms to run more quickly.

## Results Summary
This Tidy Tuesday's data set was primarily a list of pairs of cities, called [sister cities](https://en.wikipedia.org/wiki/Sister_city). These cities have legal and/or social agreements for promoting cultural and commercial ties. This dataset included ~10.6K pairs of sister ciites. A supplemental dataset included additional information about each city, including city names, locations, countries, and continents. This dataset had information on 5.5K cities

I knew that I wanted to do a cluster analysis, looking to see how many countries could be connected through only traveling through sister cities. The prompt suggested keeping this at a country level, but I was interested in doing this at a variety of levels (Are most cities sisters to only one other city? Or is it common to have several agreements with other cities?)

First, I took a look at how many sisters each city had. While the vast majority only have agreements with one other city ![Histogram of how many sister cities have "n" sisters. Chart looks similar to an exponential distribution](/images/hist_nb_sister_cities.png =250x250), there are cities that have many sister agreements. These cities tend to be large, international cities. I've shown the top 20 below: [Bar chart of top 20 cities that have the most sister agreements. St Petersburg is the most, with 96 sisters, followed by Rio de Janeiro with 94](/images/bar_most_sister_cities.png).

However, this  does not answer our questions about clustering. I found that all countries that are included in this data can be connected by sister cities, which was a pleasant surprise. So I focused mainly on analyzing city clusters. I found that of the 5.5K cities, there were (only?) 364 clusters, which was a much more manageable number of clusters than I was expecting. The largest cluster explained this - it included 4.5K of our cities. ![Bar Chart of cluster size. Most clusters are of size 2 (250 clusters)](/images/hist_cluster_sizes.png)

Because this largest cluster was so large, the visualization of it was pretty difficult to look at, even as an interactable map. Therefore, I'd like to highlight the 2nd and 3rd city clusters. 

![Map image of 2nd-largest cluster](/images/map_cluster79.png)

![Map image of 3rd-largest cluster](/images/map_cluster73.png)

These clusters show ties between European cities (with one west-coast US city involved!). These clusters are interesting, because they are isolated from the large-international clusters, but still show strong bonds between these cities. I was kind of expecting these clusters to be all connected to one city, like a spoke and wheel, but that's not really the case.


## Takeaways/Learnings
Lots of learning happening here! I implemented 3 different algorithms to create clusters. My final algorithm was using a Union Find algorithm that can work on a continent, country, or city basis. My first algorithm didn't work properly - it was based entirely in a set-notation theory and I think was on the right track but would have needed a while loop to continue the process and was already somewhat slow. My second algorithm was using a Union Find algorithm, but with sets rather than trees. This algorithm was running very slowly, which is why I pivoted to a more traditional tree-based algorithm with tree indexing. This version was also slow until I added the indexing, and while it probably won't work for non-transitive examples, it worked well for what I needed it to do.

Additionally, got to work with Seaborne to create mapping visuals, which is always a plus. It's very exciting to be able to create visuals with point-based mapping, but I'd love to do something with heat maps. I think there could be ways to extend this project - for example a heat map for how connected to the US each other country is through sister cities.

Third, actually got to stretch what I can communicate with GitHub. I'd seen people create more wiki-like ReadMe pages, and trying to emulate that here, as well as iterating through some of the actual Git functions to upload and delete files in this space.

Finally, the introduction to Tidy Tuesday was fantastic. I was able to find some other people who were working on this week's challenge and use their work as validation. Very inspired by what others are doing, and would love to treat this less as a technical exercise in the future and more of a business problem, but currently working on getting more comfortable with Python (which is still fussy, but getting easier!)

