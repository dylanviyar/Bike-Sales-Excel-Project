# Data-Driven Dancing: Understanding Listening Habits 🎵🎧
### Author: Dylan Viyar
### Last Updated: 2023-09-28

Fresh off of an absolutely stunning Coldplay concert, I was curious to determine if certain songs and/or particular types of music are more likely to be enjoyed by the public and have success on music streaming services.

# 1. Background Information

### 1.0 The Setting

In order to discover if certain genres and songs are generally more favorable, or if music is truly subjective, we can analyze a dataset that contains information about the top perfoming songs on the streaming service Spotify.

### 1.1 Guiding Questions 

1. What are some reoccuring characteristics of songs, such as the BPM, genre and key that are in the most popular songs?
2. How can understanding of these trends help aspiring musicians create music more likely to be well recepted by the public?

### Business Task

*Analyze data containing information on the top performing songs of 2023 to understand listening preferences and provide artists with data-driven suggestions for music curation targeted for the general public*


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

We can now cleanse our data column by column to get a more meticulous understanding of our data and possible areas needing manipulation:

`track_name`: 

- Sorting the column by ascending values, we can see that there are rows with numeric track names. I searched my Spotify application to see if I could find these songs or if it was a data entry error, and all the songs checked out!

- Some song titles contain foreign characters such as "½ï¿", possibly due to an incapibilty for Excel to process accents and other non-English characters. Using `=MAX(UNICODE(MID(A491,ROW(INDIRECT("1:"&LEN(A491))),1)))>127` we can determine which cells contain such characters, and a total of 71 songs have these characters, removing these songs is unlikely to change the trends we discover so we remove said rows.

`artist(s)_name`:

- Using the same function for the artist(s)_name as we did with track_name, we can see that there are 39 rows with cells that contain foreign characters. However, there are reoccuring artists that, if removed, can possibly have an effect on the trends that we find. We can use find and replace to replace the common artists. Particularly, we change "Beyoncï¿" to "Beyonce", "Mï¿½ï¿½ne" to "Maneskin" and "Tiï¿½ï¿" to "Tiesto". We delete the remaing 28 songs.

`artist_count`:

- All values are numerical and we have no NULL or blank values thus no further manipulation is necessary.

`released_year`, `released_month`, `released_day`:

- All these columns and their respective values are ready for analysis, however we can combine all these values into one column labeled `released_date` to make it easier to keep track.

- To understand monthly trends, we can also create another column named `released_month_name` to allow for more intuitive visualizations.

`in_spotify_playlists` and `in_spotify_charts`:

- All data types and values are consistent to the task and they do not need further cleansing

`streams`: 

- There is a data entry error for the song "Love Grows (Where My Rosemary Goes)", after further research I manually inputted the correct amount of Spotify streams

`in_apple_playlists`, `in_apple_charts`, `in_deezer_playlists`, `in_deezer_charts`, `in_shazam_charts`:

- As we are focused on analyzing trends for only the music streaming service Spotify, we can delete these columns

`bpm`:

- All values are numerical and relevant (no NULL or blank values) thus no cleansing required

- In order to make bpm easier to visualize and work with, we can create a new column titled: `bpm_range` to allow for more accessible analysis with this formula : `=IF(L5>=160,"160+",IF(L5>130,"Between 131 and 160", IF(L5>110,"Between 111 and 130", IF(L5>80,"Between 81 and 110",IF(L5<=80,"Less than or equal 80")))))`

`key`:

- There are 90 rows with a blank value as a key. We can use Find and Replace to replace the blank cells with the value `Unknown Key`

`mode`: 

- For the songs that have the value `Unknown Key`, we can replace the mode to `Unknown Mode`

`danceability %`, `valence %`, `energy %`, `acousticness %`, `instrumentalness %`, `liveness %`, and `speechiness %`:

- All values are the correct data type and are as expected, no further manipulation necessary


After data cleansing, our dataset (sorted descending by number of Spotify streams) looks like this:

![CleanMusicAnalysisDataset](https://github.com/dylanviyar/Excel-Projects/assets/81194849/01db5cf8-bcc1-4162-b897-5c9efc49cfab)

We are ready for analysis.

# 4. Analysis

### 4.1 Pivot Tables

Using pivot tables we can look for trends and relationships within our dataset:

Top Performing Artists of 2023:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/9499a485-b148-4c3d-a4dd-65344fd31efb" width = "200">

Relationship between BPM and Song Characteristics:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/6211b31b-e5d8-4529-87aa-685bb17015fb" width = "350">

Frequency of Song Releases:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/7a2b3e46-d8a5-41f5-be95-c0ebbad0456c" width="200">

Relationship between BPM and Amount of Streams:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/55fd17e9-116e-4e79-b5dd-3d98f991fcbf" width ="200">

### 4.2 Key Takeaways

1. The Weeknd has the most amount of Spotify streams
2. A BPM (beats per minute) between 80 and 110 has the highest values of `valence_%`, `instrumentalness_%`, `dancibility_%` and `energy_%`
3. January is the most popular time to release a song, whereas Feburary is the least popular
4. Songs in the BPM range of 80 to 110 are the most popular, receiving the most amount of streams

# 5. Data Visualization

### 5.1 Dashboard

![MusicAnalysisDashboardUpdated](https://github.com/dylanviyar/Excel-Projects/assets/81194849/96b9aa2f-c0e2-4443-9c59-90ba2e0debdf)

*Note: We provide two additional slicers: `mode` and `key` for two more filters that allow for on-demand analysis*

### 5.2 Visualization Insights

1. The most popular songs are in the 80 to 100 BPM range, and songs in this range tend to have high valence, energy and dancibility percentages while not having a particular emphasis on the intrumentalness percentage
2. Songs released in January, May and November have the highest number of streams
3. Taylor Swift is the artist with the most streams for songs in the Major mode while Ed Sheeran has the most streams for songs exclusively in the Minor mode
4. Certain keys of songs have faster and slower most popular BPM, with the key of A being the most popular key for songs in the 160+ BPM and interestingly, also the key most popular for songs in the 80 or below range
5. The key with the most streams is C#

# 6. Conclusion

### 6.0 Recall our Guiding Questions

1. What are some reoccuring characteristics of songs, such as the BPM, genre and key that are in the top 100?
2. How can understanding of these trends help aspiring musicians create music more likely to be well recepted by the public?


### Reoccuring Trends in the Most Successful Songs

- Most popular songs are in the key of C#
- 80 to 110 BPM seems to be the home of happy, dancing music, a very popular type of music
- Certain attributes are higher valued than others to the public when deciding if they want to stream the song
- The Weeknd is constantly high performing, having the top spot in streams overall

### Data-Driven Suggestions for Musicians

1. Know when to drop your music! January, May and November are when the public seems to be the most receptive to streaming new music, possibly because of the new year, start of summer and Christmas, respectfully, so make sure to release new content during these months
2. Focus on the vibe not technicalities. Listeners are less motivated to listen to songs with high instrumental presence, rather they enjoy streaming uplifting, energetic and happy music
3. BPM BPM BPM! Clearly the top perfoming BPM range is between 80 and 110 so keeping music in this range can ensure that people are familiar with the cadence and are more likely to enjoy it
4. Key of C#. This key is a very popular attribute of high-streaming songs, possibly because of how bright and positive this key sounds. Making music in this key can also possibly supplement streams and listener interest.
