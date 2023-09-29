# Data-Driven Dancing: Understanding Listening Habits 🎵🎧
### Author: Dylan Viyar
### Last Updated: 2023-09-28

Fresh off of an absolutely stunning Coldplay concert, I was curious to determine if certain songs and/or particular types of music are more likely to be enjoyed by the public and have success on music streaming services.

# 1. Background Information

### 1.0 The Setting

In order to discover if certain genres and songs are generally more favorable, or if music is truly subjective, we can analyze a dataset that contains information about the top perfoming songs on the streaming service Spotify.

### 1.1 Guiding Questions 

1. What are some reoccuring characteristics of songs, such as the BPM, genre and key that are in the top 100?
2. How can understanding of these trends help aspiring musicians create music more likely to be well recepted by the public?

### Business Task

*Analyze data containing information on the top 100 songs of 2023 to understand listning preferences and provide artists with data-driven suggestions for music curation targeted for the general public*


# 2. The Data

### 2.0 Accessibility

The dataset is available to the public for download on Kaggle [here](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023)

### 2.1 Initial Impressions

Upon downloading and opening the dataset into Excel, we can see that the data looks like this:

![MusicAnalysisFirstLook](https://github.com/dylanviyar/Excel-Projects/assets/81194849/2e5fed14-cdd8-4a70-a227-6e76186bb400)

**Key Takeaways**
1. There are a total of 24 columns and 954 rows
2. Each row describes a song that was popular in the year 2023
3. Each column denotes different attributes of a particular song, including the presence and rank of the song on Spotify charts, BPM, Key and other metrics such as dancibility and energy percentage

### 2.2 Does the Data ROCC?

When evaluatiing the status of data to be used for analysis, a simple test is to see if the data you are using is 'ROCC' (Reliable, Original, Comprehensive, Current, Cited)

**R**eliable: -Yes- The data is made avaiable on Kaggle with a plethora of upvotes and positive feedback, suggesting that the data is valid and useful

**O**riginal: -Yes- This dataset contains unique metrics such as `danceability_%`, `valence_%` and `liveness_%` which provide original and new opportunities for insights

**C**omprehensive: -Somewhat- There are further attributes that are missing that could possibly be valuable for exploration such as Genre

**C**urrent: -Yes- This dataset is from the current calendar year of 2023, making it current and relevant

**C**ited: -Yes- Kaggle provides metadata about the top contributors to the dataset as well as other important information regarding the history of the data


Overall, our data does ROCC and we can be confident that we can create meaningful insights from the information found in the dataset!

# 3. Data Cleansing

### 3.1 Preparing our Data

Note: Before manipulating our data, it is good convention to copy the raw data into another sheet, so we maintain a copy of the original data while we clean our data. Accordingly, all the following steps are done in a copy of the original dataset

While getting our data ready for analysis, some **Key Steps** include:

- Removing duplicates
- Checking for data type errors (inconsistent/mismatched data types)
- Making the data more accessible
- Ensuring the data stays relevant to the business task
- Dealing with NULL or empty values


Using Excel's built-in remove duplicates functionality, we can see that there in fact no duplicate rows that we have to get rid of:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/7d49c198-01c1-45f0-aff6-8444c088c605" width="250">


