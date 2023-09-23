# Bike Sales Data Exploratory Analysis: Understanding Consumers  
### Author: Dylan Viyar
### Last Updated: 2023-09-23

This project was motivated by the final Excel case study in Alex Freberg's Data Analysis bootcamp. We want to understand more about what motivates people to purchase a bike.

# 1. Background Information

### 1.0 The Setting

In an effort to understand the bike industry and market, we can look at a dataset that contains information on bike consumers and determine if there are any underlying trends to worth noting. We then can make marketing strategy suggestions to supplement sales growth.

### 1.1 Guiding Questions

1. What are some trends and patterns in bike consumers vs. non-consumers?
2. Are certain demographics or audiences more likely to purchase bikes?
3. How can understanding these trends influence marketing strategies for bike stores?


### 1.2 The Business Task

*Analyze bike consumer data to better understand the targeted audience and provide insightful marketing suggestions.*


# 2. The Data

### 2.0 Gathering the dataset

The data made publicly available [here](https://github.com/AlexTheAnalyst/Excel-Tutorial/blob/main/Excel%20Project%20Dataset.xlsx)

### 2.1 A Quick Glance

When opening the Excel file, we can see the data looks like this:

  ![Uncleaned Preview BikeSales](https://github.com/dylanviyar/Excel-Projects/assets/81194849/4b99ddb2-2cec-4145-9ebf-f2a0c0d61cfb)

Key Takeaways:
- There are 13 columns and 1027 rows in our dataset
- Each row is a description of a person, with the final column distinguishing if they ended up purchasing a bike
- Each column are different attributes of an individual, possibly certain attributes to motivate a bike purchase

### 2.2 Possible Limitations of the Dataset

1. We only have a limited amount of characteristics, we do not know if these are truly the most influencial aspects when deciding to purchase a bike
2. We are unaware of the collection method of the data, we do not know if there is bias in the data or data collection
3. We do not know if these trends that we discover are still relevant to the current audience

# 3. Data Preparation

### 3.1 Data Cleansing

*Note: Before manipulating our data, it is good convention to copy the raw data into another sheet, so we maintain a copy of the original data while we clean our data. Accordingly, all the following steps are done in a copy of the original dataset*

While getting our data ready for analysis,
some **Key Steps** include:
1. Removing duplicates
2. Checking for data type errors (inconsistent/mismatched data types)
3. Making the data more accessible
4. Ensuring the data stays relevant to the business task
5. Dealing with NULL or empty values

Using Conditional Formatting, I searched for duplicate IDS, as there is not supposed to be any duplicate values: 

![Duplicate IDS Bikesales](https://github.com/dylanviyar/Excel-Projects/assets/81194849/a11f3603-facd-44f6-b515-28793e00464f)

Here, we can see that despite the IDs being the same, the user information is different. This either means that the ID is not a unique identifier for the individual (unlikely) or there was an error in data collection. This is important to note. 

Regardless, completely duplicated rows are usually irrelevant in data analysis (as it is in our case) so we can use the "remove duplicates" in Excel to remove such values:

<img src="https://github.com/dylanviyar/Excel-Projects/assets/81194849/6ce1b825-4d80-4e29-abc2-8b1fd22f67e1" width="400">

We can see that our sheet had 26 duplicate rows and Excel successfully removed those rows.

For the rest of the data cleansing we can go column by column and determine if the particular data in the column needs adjusting.

- ID: 

