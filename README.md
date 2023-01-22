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

## 
