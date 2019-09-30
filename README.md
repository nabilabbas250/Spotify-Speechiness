# Spotify-Speechiness
Is a hop hop song speechy or not?

## Goals

Create a machine learning model to classify a hip hop track as "speechy" or "musical".  **Speechiness** is a feature in Spotify's API that "detects the presence of spoken words in a track." 

*"The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. **Values between 0.33 and 0.66 describe tracks that may contain both music and speech**, either in sections or layered, including such cases as rap music. **Values below 0.33 most likely represent music and other non-speech-like tracks.**"*

![](speechiness.png)


## Strategy

Create a playlist of approximately 1400 hip hop tracks.  Parse through spotify's API to obtain the track's features.  These features and their values will be used as predictors to train over several machine learning models.  The most accurate machine learning model will be the final model for future predictions.

**Features:** 
'acousticness',
 'danceability',
 'duration_ms',
 'energy',
 'instrumentalness',
 'liveness',
 'loudness',
 'tempo',
 'valence',
 'key',
 'mode',
 'time_signature'
 
 The features definitions relevent to spotify's API can be found at the following hyperlink: 
 
 https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/

## Parameters

- Create a playlist of ~1400 hip hop tracks.  
- Categorize the tracks as "speechy" and "musical", where musical data points contain have a speechiness value betwen 0 and 0.33, and speechy data points contain values greater than 0.33.  
- Because the dataset is unbalanced SMOTE the data set to create balance between "speechy" and "musical" data points.
- Use GridSearchCV and RandomizedSearchCV to optimize hyper parameters of the models being trained.

## Hypotheses

It was difficult to draw a hypothesis on which features would be relevent because of my initial limited knowledge on musical features.  My blind guess hypothesis was that **tempo** would be a good indicator of a "speechy".  The logic for that was that I was expecting the more "speechy" songs would be contain more lay overs of real life speeches **or** the artist speaking on the track at a slower pace.  These moments of slower pace and audio layovers gave me the impression that a tracks with lower **tempo** would help indicate a track's "speechiness" parameter.

## Results and Insights

### Model
What models were tested?
Dummy Model
![](dummy.png)

Which models performed the best?
![](random_forest.png)
![](xg_boost.png)

Model Visualization (if available)
![](ROC.png)
![](confusion_matrix.png)

### Feature Analysis
Feature Importance

![](feature_importance.png)

#### Valence

![](kde.png)

#### Time Signature 5

![](time_sig_5.png)

#### Feature 3
#### Feature 4

## Going Forward and Future Analysis

I plan to revisit this project with better EDA strategies in mind.  

- Research and understand the features and how they work in actual music.

- Listen to "speechy" classified songs to understand the style of music being classified.

- Avoid SMOTING data so that I have a more naturally balanced dataset. Having a more naturally balanced dataset will lower the dummy accuracy score to beat.  

- Reapply GridSearchCV and RandomizedSearchCV w/ more varying hyperparameters.

- Revisualize time signatures to lay out distribution of all 5 time signatures

- Test another Feature Importance visualization function.

- Engineer additional features from Audio Analysis data in Spotify's API.
