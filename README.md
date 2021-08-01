##### Submit links:
- Blog: https://www.kaggle.com/dovannhan/udacity-nhandv6/data
- Github: https://github.com/Nhan121/Udacity_stage1_Due_02_Aug

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
- The average reservation_days in `Seattle` is higher than in `Boston`, considered on the top 20 listing_ids

- The majority of listings is concentrated around 50 - 150 USD in Seattle and about 50-250 $ in Boston

### Question 3. Try to understand if there is anything about the properties that helps you predict price, based on the 2 datasets: boston_listings and seattle_listings.
#### Analytics
When forecasting the price of house, we have seen that these feature can be strongly affect to the price are

- Numeric features: 'bathrooms', 'beds', 'square_feet', 'availability_30', 'availability_365', 'availability_60', 'availability_90', 'number_of_reviews', 'accommodates', 'review_scores_rating', review_scores_location' and 'host_listings_count'

- Category features: 'bed_type', 'smart_location', 'property_type', 'room_type' and may be 'neighbourhood_group_cleansed'

Check again which features in the numeric_features can be influenced the prices. To solve this, I will use the heatmap on the correlation matrix.

- In the column bed_type, the value Real_bed has the highest average_price at both cities, while the Airbed is lowest in Boston and Couch is lowest in Seattle.

- In the column room_type, the value Entire home/apt has the highest average_price at both cities, and obviously the shared_room is lowest.

- In the column property_type, the value Guesthouse has the highest average_price in Boston while in Seattle is Boat, the lowest average_price in Boston is Bed & breakfast while Cabin is the lowest in Seattle.

Finally, we apply the Machine Learning models to forecast the average_price based on the features in the listings_dataframes.

- These scores indicated that the model make overfitting, we must remove some features is not related / not correlated the price.
- Moreover, to find the best r2_score, we can use grid_search CV / hyper-tuning parameters to solve this.

### Question 4. Can you find negative and positive reviews based on text?
##### Answers.
- Firstly, viewing each comment line by line is impossible, read my source_code and its output to examine what I meant. We saw that the keywords in the first 10 comments is
"Perfect", "great", "beautiful", "well", "hola", "pleasant" etc... to describe the positive
"issue", "terrible", "stupid".... for negative
- But I want to look over them, so I will use N-grams analytics on the top 100 of uni-grams, bi-grams and tri-grams to solve this!
>- First is the Uni-gram, from the charts below, we have seen that

>>> The words great is appeared almost in the comments_review in both cities;

>>> The second and the third popular words is stay and place in both cities

>>> But the next 4th popular word is us in Seattle while in Boston was apartment

>>> etc.

>- How about the Bi-grams of the comments

>>> Wow, the most 4 popular bi-grams in both cities is the same : definitely stay, highly recommended, walking distance and stay again

>>> Almost the top 75-bigrams reflect the positive comments with the words like: highly recommended, great location, great place, great host, great location, clean well.

==> From this, we can examine easier which words meant positve and negative in the `comments_reviews`.

### Question 5. Make 2 time-series model to forecasting the difference of the reservation_prices between 2 cities.
Our dataset is in 1 year only, we can make a ARIMA, SARIMA, SARIMAX model or something like this.

But here, in this case, we can use a assumption of Markov properties: the price of present is depended on the avg_price of the previous 3 days or 1 week and I will use another Machine Learning models like Random Forest regressor and Gradient Boosting

- Step 1. Making a rolling-window! Here, I let the `window_size = 3`.
- Step 2. Making a shifted-datetime
For a fixed window_size = 3, I will establish a model that based on the 3 previous days for predicting the average_price today, so we must shift the rolling_window by 1 steps! Look at the following output
- Step 3. Replacing the missing_values by its averages.
- Step 4. Choosing an algorithm or implement Hypertuning parameters to improve your forecasted_scores.


# Summary.
- I haven't used the Grid-search CV / Hyper tuning parameters to improve the forecasting model in Question 3 and Question 5.

- My solution at question 3 is also not good at all, there is an overfiting problem here!

- The model selection was not optimized since I haven't droped the weak-corelated features in Question 3.
