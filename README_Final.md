# Netflix-Project-1
Project 1 - EDA for Netlfix

Team Members:
Madelyn Baker
Madison Henry
Jaipal Narang
Turhonda Williams

Our analysis attempts to determine if Netflix-produced content performed better than non-Netflix produced content. We used a dataset of movies and TV series available on Netflix from kaggle and IMBd's API. 

# Actors, Writers, and Directors
One of our goals for this project was to discover if Netflix reuses actors, directors and writers more frequently than non-Netflix productions. We split our Netflix CSV into two data frames depending on whether the content was Netflix produced or produced elsewhere. Once this was done, we looked at the amount of times each actor, writer and director worked on a movie or series.
We found that, for both Netflix and non-Netflix productions, the majority of these people only worked on one production. But, for the ones who did work on multiple productions, non-Netflix content reused these people more frequently. In fact, non-Netflix content reused actors, producers and writers about three times more often than Netflix.

# Distribution of IMDb Scores by Content Producer
We decided to take a further look into the type of content produced, whether it was a Movie or TV series and compare it to the IMDb scores. The frequencies of movies and series were plotted in histograms. We performed a minor statistical analysis by calculating the mean IMDb score for movies and series in both Netflix and non-Netflix content. The majority value (mode) which is demonstrated at the peaks of the histograms were evaluated in both TV series and movies. Non-Netflix content (both tv series and movies) had more content as well as a higher ratings scores above an IMDb score of an 8.

# IMDb API
The kaggle dataset contained the IMBd link to the content item in IMDb, and the last portion of this URL contained the IMBd ID (e.g., tt1234567). The ID was parsed from from the URL into a separate column.

The IMDb API subscription has a call limit of 5,000 calls per day, and the total kaggle dataset contained 15,000+ records. Consequently, the API was called in batches from lists created off the kaggle dataset. However, in the course of creating these API calls, there were numerous errors (one or two infinite loops...) and eventually 8 lists for appx. 7,500 records from the kaggle were queried in the API. The 7,500 records from the the kaggle set are those with an award nomination or win indicated in the dataset. API calls that did not result in errors were saved to a CSV file, which was used to construct the remainder of the awards analysis. 

For the purpose of this analysis, "award" refers to either a win or a nomination. The API call successfully returned nearly 2,500 award records for almost 1,300 content items. While the imbalance between Netflix and Non-Netflix items was consistent in the IMDb dataset, the portion of records with awards was similar for both groups: 
9.13% of Netflix content items in the kaggle dataset had awards records returned by the IMDb API calls
9.56% of non-Netflic content items in the kaggle dataset had award records returned by the IMDb API calls.

Percentages were used to account for the differences in the dataset size. Netflix awards are framed in context of total Netflix items, as opposed to the entire kaggle dataset, and the same for non-Netflix items. These percentages were used to inform the scatter plot and bar chart comparisons. This portion of the analysis ultimately concluded that IMDb Score was not a reliable indicator of award nominations and wins and instead supports the null hypothesis. 


# Genre Analysis
For analyzing genres, there were a few important steps.
The first step was the same for all of us, differentiating by netflix and non-netflix content. This was done by matching the title release date and the time Netflix released it, when it was the same, we categorized that as Netflix content, and when it was different, it was non-Netflix content.
The second step for me was separating the genre strings. For example, for a movie, in the genre column it may be listed as “Romance, Drama, Action.” I used a str function that would separate the first Genre from the other two based on a comma delimiter, and would place that first genre into a new column title genre 1. So  “Romance, Drama, Action” became just “Romance” for simplicity's sake.
Then creating unique counts for each genre, I calculated average ratings for each genre for netflix and non-Netflix content for all four rating metrics. After compiling that data, I was able to create bar plots with average scores for each genre, per netflix and non-netflix data.

# Assumptions and Limitations
A key assumption in the analysis is that when the Release Date and the Netflix Release Date are identical, it always means that the item was produced by Netflix
Population size: About 10x more films/movies for Non-Netflix vs Netflix productions
Only primary actors, writers, directors (least impacted) appeared in the dataset for a given movie. For the purpose of this analysis, these individuals are assumed to have starred/been a primary writer (etc.) in the films, and they may be unnamed in movies or TV series where they had a lesser role. 
The distribution of production houses includes only those named, and the dataset contained numerous nulls for this field. 
API 
The API calls used to populate the csv with the IMDb awards data raised a substantial number of errors, which were passed on in order to create the csv dataset. These errors are not fully understood and, if resolved, could impact the analysis. 
To pull data within the API subscription limits, only IMDb IDs were queried where they had an award notation in the kaggle dataset. Items without the award notation in the kaggle set were not called in the API and could contain additional award information that may alter the analysis. 
