# Music Segmentation Unsupervised Learning_Project

Collect and cluster top 100 hits from different music genres.

Traditionally songs are grouped together with other songs on the basis of genre. While this method of grouping is useful for identifying different styles, there may be other valuable ways to group songs together. The aim of this study is to apply clustering algorithms to an assorment of songs across generes and explore cluster centers to determine if the the algorithms grouped songs together on the basis of genre, or in another way that is or is not of value. 
 
<img src="Images/Spotify Logo.jpg" width="800" height="400"></img>

grouping songs of similar moods across genres i.e happy upbeat music, chill background music

# DATA:

The data for this project is sourced from Spotify
- Each playlist is created by Spotify, features the top 100 tracks for that genre, and is updated weekly

1) Top 100 Pop Tracks on Spotify
2) Top 100 Alternative Tracks on Spotify
3) Top 100 Rock Tracks on Spotify
4) Top 100 Country Tracks on Spotify
5) Top 100 Hip Hop Tracks on Spotify
6) Top 100 Indie Tracks on Spotify
7) Top 100 Electronic Tracks on Spotify

# DATA ANALYSIS:

# 1. Data Collection:
In this step I collect and concat all playlists

# 2. Exploratory Analysis:
In this step the relationships between each genre playlist amd the song metrics provided by Spotify.

# 3. Modeling Sales:
In this step I run clustering algorithms on the unique dataset I put together to see if songs are clustered along genre lines or clustered in novel way. 


-----------------------------------------------------------------------------------------------------------

# Data Collection 

**Step 1 : Selecting the data**
The following steps were preformed using via google searches and Spotipy 

- Identify 7 top tracks playlists for different genres created by Spotify 
- Pip install Spotipy- Spotify's lighweight Python library for the Spotify Web API
- Import tracks from each Spotify playlist with the free audio features provided by Spotify
- The free audio features are...
     1) Danceability- how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm          stability, beat strength, and overall regularity (1= most dancable)
     2) Energy- perceptual measure of intensity and activity (1= high energy)
     3) Accousticness- whether the track is acoustic (1= acoustic)
     4) Liveness- Detects the presence of an audience in the recording (1= live)
     5) Instrumentalness- Predicts whether a track contains no vocals (1= no vocals)
     6) Valence- describing the musical positiveness conveyed by a track (1= happy)
     7) Tempo- beats per minute (BPM)


**Step 2 : Aggregating the data**
The following steps were preformed using Python functionalities

- Scale tempo to be between 0-1 
- Add a genre column
- Concat all Spotify playlists 


- The df 

 <img src="Images/Spotify df.png" width="600" height="400"></img>
 
# Exploratory Analysis
- I divide the analysis into the following parts:

**A) Yearly Analysis**: Sales per category, sales per county, sales per bottle volume

**B) Monthly Analysis**: Total sales, sales per category

**C) Customer Analysis**: Analyzing relationship between population demographics and sales per county. 

**D) Predicting Sales**: Using demographic and sales data from 2017 to predict yearly sales per county for 2018.

# A) Yearly Analysis :
**Step 1 : Exploring the data**
The following steps are preformed using pandas functionalities

- Examine volume of liqour sold in gallons grouped by category
- Examine volume of liquor sold in gallons grouped by county
- Examine volume of liquor sold in gallons grouped by bottle size 

# A) Yearly Analysis :
**Step 2 : Visualizing the data**

In this step, I visualize the previous findings using plotly.express 

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/Gallons_per_Category.png"></img>

### Conclusion: American Vodkas account for nearly half of all sales

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/Gallons_per_County.png"></img>

### Conclusion: Ten out of ninety-nine counties account for over sixty percent of sales

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/Gallons_per_Bottle_Size.png"></img>

### Conclusion: 1750ml, 1000ml, and 750ml the dominate size of bottles sold

# B) Monthly Analysis :
**Step 1 : Exploring the data**

In this step, I preformed the following using pandas functionalities
- Examine total sales per month
- Examine total sales per month by category of alcohol 


# B) Monthly Analysis :
**Step 2 : Visualizing the data**

In this step, I visualized the previous findings using seaborn

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/2017_Sales_Over_Time.png" width="600" height="300"></img>

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/2018_Sales_Over_Time.png" width="600" height="300"></img>

### Conclusion: Sales appear to spike in even numbered months and fall in odd numbered months.

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/2017_Category_Sales.png" width="740" height="300"></img>

<img src="https://github.com/hobediente/Liquor_Sales_Supervised_Learning_Project/blob/master/Images/2018_Category_Sales.png" width="740" height="300"></img>

### Conclusion: Certain categories of alcohol appear to be seasonaly ordered i.e. mixto tequila, while others show more consistency. 

# C) Customer Analysis :
**Step 1 : Exploring the data**
In this step, I preformed the following using pandas functionalities

- Group DataFrame by county, summing for the total amount of liquor sold in gallons, and taking the mode for relevant population statics
- Examine the relationship between population demographics per county and sales

# C) Customer Analysis :
**Step 2 : Visualizing the data**

In this step, I visualized the previous findings using ploty.express

<img src="Images/Pop_Stats_and_Sales.png" width="600" height="600"></img>

### Conclusion: Sales are highly correlated to the percent of educated population under 25.


# Modeling Sales

**Step 1 : Selecting Model**
- Run random forest
- Run XGboost

**Step 2 : Tuning Models**
- Get feature importances
- Rerun models with only important features
- Run GridSearchCV to hypertune parameters
- Rerun models with hypertuned parameters

**Step 3 : Select Best Model**
- Compare goodness of model meterics and select best model
  * MAE, MSE, RMSE, MAPE
  
-----------------------------------------------------------------------------------------------------------

# Model Results :
- XGboost is the best preforming model 
- With input features of category, percent population with an education, and percent population under 25 the model achieved..
  * Training Score: 0.999, Test Score: 0.996
  * RMSE: 17357.78 (0.09% of total sales)
  
# Analysis Takeaways :
- Focus advertising resources on counties that bring in the most money
- Advertise for seasonal liquor at the beginning of their respective seasons
- Strengthen advertising to and around college campuses
