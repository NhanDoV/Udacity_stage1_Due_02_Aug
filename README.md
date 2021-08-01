# Introduction
This topic is my practices on the Learning path of Udacity

The source dataset is taken from Seattle Airbnb and Boston Airbnb

According to the requirement "pose at least three questions related to business or real-world applications of how the data could be used" of Udacity, I had figured out 5 questions in this topic

1) Try to understand how much AirBNB homes are earning in certain time frames and areas/ cities.

2) Examine the Total_price by top20 listing_id at each city and its reservation days.

3) Try to understand if there is anything about the properties that helps you predict price, based on the 2 datasets: boston_listings and seattle_listings.

4) Can you find negative and positive reviews based on text?

5) Make 2 time-series model to forecasting the difference of the reservation_prices between 2 cities.

Follow that, we can understand the difference between 2 cities by looking at these question, doing EDA and also comparing the Machine Learning models. Moreover, these 5 questions is applied many problems:

Time-series forecasting in Question 5

Regression in Question 3

Ngrams-analytics (a part of NLP) in Question 4.

Name: Do Van Nhan

Account: NhanDV6

Now, we must import the necessary libraries then load our dataset

# Coding.
https://github.com/Nhan121/Udacity_stage1_Due_02_Aug/blob/main/udacity-nhandv6_stage1.ipynb

# Conclusion on each question
### Question 1. Try to understand how much AirBNB homes are earning in certain time frames and areas/ cities.
#### Answers
The daily average price between 2 cities.
- "The average price in Seattle is lower than in Boston", but the total_revenue at Seattle is nearly approximate at in Boston. The second chart show that there are more reservations in Seattle than in Boston.
- Moreover, loot at the average_price, we have seen that the listing prices raise significantly in summer at Seattle and in autumn at Boston, probably, because of the fact that there are less listings available for reservation. There is also a raise in December at Seattle and in May at Boston. This tells us that summer and winter holidays should be the busiest times to visit Seattle, also autumn to visit Boston.
- At Boston, Jan2017 - Mar2017 is the time that the average price is lowest
- At Seattle, Jan2016 - Mar2016 is the time that the average price is lowest
- 1st quarter is the quarter that the average prices is lowest in both Seattle (125 at Q1-2016 and 136 at Q1-2017) and Boston (181 at Q1-2017).
- 3rd quarter is the quarter that the average prices is highest in both Seattle (148 at Q3-2016) and Boston (252 at Q1-2017).

>> So which certained time that the time-series attain highest and lowest in each charts?

- The avg_price is lowest in 01, Apr 2016 at Seattle and in 06 Sep 2016 at Boston

- The avg_price is highest in 02, Jan 2017 at Seattle and in 05 Sep 2017 at Boston

### Question 2. Examine the Total_price by top20 listing_id at each city and its reservation days.
#### Answers
