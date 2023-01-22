<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/decorations/Analysing_Successful_Artists_on_Spotify_%F0%9F%8E%A7_.png" width="900">
</p>

# Spotify_PredictingLeadingArtists

## Introduction
This project aims to leverage data to predict artist success on Spotify, understand the factors that contribute to it, and understand how Spotify playlists play a part in it. Spotify has changed the music landscape recently, and provides a platform for new artists to showcase their work and introduce themselves to the world. As a musician myself, ABRSM educated in theory and piano, I was very excited to do this analysis. 

## Acknowledgements
The opportunity to do this analysis was provided by UCL, as this rich dataset of 50 billion rows was given as a part of my MSc in Business Analytics. My analysis was particularly inspired by a dissertation whose author was made anonymous. The work investigates the role of Spotify playlists and makes use of Network Analysis as well. However, my work investigates the role of playlists and other factors by considering the aggregated audio and lyrical content of all the songs of the artist. 

## Background
According to a UCL dissertation that used the same dataset, artists that initially appear in 4 specific Spotify playlists end up falling into the top Spotify playlists. These playlists are:
  1. Hot Hits UK
  2. Massive Dance Hits
  3. Indie List
  4. New Music Friday
Similarly, if a song of an artist is featured in any of the above playlists, I will also consider the artist as successful. This synthetic metric will serve as a foundation to my article. 

## Dataset
The dataset covers songs played on Spotify by a particular user, where each row represents a song played for more than 30 seconds. As the dataset is very large, we have considered a sample of 3 million rows, due to constrained resources and time. 
<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.51.43.png" width="900">
</p>
As the aim of the article is to determine whether an artist is successful or not, a lot of feature engineering was needed and the dataset had to be aggregated so that the rows are organised on an artist level. The outcome variable is binary, where 1 represents success and 0 represents no success. 

Additional data, such as audio features and song lyrics, were scraped using the Spotify and Genius APIs. Then they were also aggregated across all the songs by artist level, paired with dimensionality reduction. Audio features look into loudness, beats, etc., and assigns a value to them. The lyrical components were embedded into 512 dimensions using a BERT encoder. 

Much attention was placed on ensuring there is little data leakage. For example, songs that were featured early in the top Spotify playlists and the playlists that indicate "success" were dropped. Only songs that have just entered the Spotify universe were counted.

## Exploratory Data Analysis

Here are some quick snapshots of the data. Understandably, there is a right skew in the distribution of listens across listener age. Higher frequencies occur around the mid-late twenties brackets.
<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.52.31.png" width="900">
</p>
Targetting these age groups may yield better results for an artist, and it would be important to consider an aggregation of ages as a factor to artist success. 

Among all unique listeners, the distribution of male to female is almost 1:1, however, the distributions differ when looking at successful and unsuccessful artists. 
<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.52.43.png" width="900">
</p>
We can see that for more successful artists, there is a significantly larger female to male ratio, whereas it remains close to 50:50 for unsuccessful artists. Hence, this ratio would serve as an important feature for our problem. 

One last thing we look at is the distribution of audio features. For most of the features, we do not see a difference between successful and unsuccessful artists. 
<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.52.54.png" width="900">
</p>
Looking at the interquartile range, we see that only 2 audio features can come across as different. Successful artists have a higher IQR for Loudness, and a slightly lower and smaller IQR for speechiness. At a glance, it would seem build-up and lyrical content, rather than more words, is associated it more successful artists. Hence, we will consider Loudness and Speechiness as features for the models in this article. 

## Feature Engineering

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.53.18.png" width="900">
</p>

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.53.08.png" width="900">
</p>

## Modelling

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.53.35.png" width="900">
</p>

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.54.23.png" width="900">
</p>

## Results and Findings

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.54.32.png" width="900">
</p>

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.54.56.png" width="900">
</p>

<p align="center">
  <img src="https://github.com/sharafmomen/Spotify_PredictingLeadingArtists/blob/main/images/analysis/Screenshot%202023-01-12%20at%2017.55.05.png" width="900">
</p>

## Limitations
1. We only have 600 artists, and the data is heavily outdated. A larger, balanced, and recent dataset could improve our model and recommendations.
Interpretations of the significant PCA were sacrificed heavily. 
2. Dimensionality reduction was at the price of guaranteed interpretability of important components from lyrics, region, playlists, and audio features. A statistical analysis on the highlighted PCA components could be explored, to see what exact factors are important. Determining the weights of different features on these PCA components would bring more focused and refined recommendations.
3. More effort could be placed into limiting data leakage. For example, I could omit a couple more of months of listens for a particular artist prior to becoming successful. 

