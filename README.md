# Overview

If you're an artist, producer, or music enthusiast, knowing how a song will perform ahead of time would be priceless. In this article, I explain the steps involved in building a predictive model that can forecast a track’s popularity on Spotify.

## Collecting the Data

The quality of data is crucial for building a reliable model. The dataset was chosen from Kaggle's [Spotify Tracks Dataset](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset), containing Spotify tracks over a range of 125 different genres obtained from the Spotify API. The data was released by Spotify on October 22, 2022. The resulting data was 15 columns and 112,059 rows with 1,680,885 samples.

## Strategies for Data Cleaning

"Garbage in, garbage out" – the quality of a model depends on the quality of the data it uses. Techniques, including machine learning-based methods, were applied to ensure clean data and avoid bias in the results.

### Data Cleaning Methods

- No duplicates or missing data was found.
- Features deemed irrelevant to building a song popularity model were removed: 'Unnamed 0', 'track_id', 'artists', 'album_name', and 'track_name'.
- Non-music tracks were filtered out using a 'speechiness' score threshold of 0.7.
- 'mode', 'key', and 'time_signature' features were label encoded and treated as categorical.
- Values less than 3 in 'time_signature' were filtered out.
- Entries of 'duration_ms' equal to 0 were dropped.
- Outliers were determined using a z-score with a threshold of 3 and visualized with boxplots.
- 'duration_ms', 'liveness', and 'loudness' were transformed using the Yeo-Johnson method.
- Numerical feature distribution was evaluated, and none were found to be normally distributed.

## Selecting the Right Features

### Audio Features

Spotify provides audio features such as tempo, key, and loudness. These were leveraged to determine how they affect a song's popularity.

### Features Analysis

Relevant features were chosen, and some potentially biased features were eliminated. The target variable and independent variables were selected.

##### Continuous Features

None of the continuous features had a strong correlation with the target variable. 'loudness' and 'energy' showed multicollinearity at 0.77; 'energy' was dropped.

##### Categorical Features

Categorical features revealed insights such as explicit songs and songs in minor keys having a higher mean popularity score. '4/4' time signature scored highest in mean popularity.

## Selection and Evaluation of the Model

The Random Forest Regressor performed the best with an R² of 0.40. Models were evaluated based on MAE, MSE, RMSE, R², RMSLE, and MAPE. The Pycaret package was used for model evaluation.

## Challenges

- Data availability can limit model creation and refinement.
- Improving model interpretability enhances understanding and identifies areas of improvement.
- Building a reliable model requires significant computational power and resources.

## Conclusion

Even with data from a streaming service, predicting song popularity with certainty remains challenging. The mystery of predicting success in the art of music endures.
