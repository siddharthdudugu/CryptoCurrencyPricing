# CryptoCurrencyPricing

1) Introduction and Problem Statement:
Cryptocurrency has been increasingly important to businesses and financial market potential during the past ten years. Due to its highly volatile nature, accurate research can help investors make the best decisions for their portfolios and may even enhance earnings. Analysts and financial researchers can examine the market behaviour of cryptocurrencies by analysing and predicting their prices. Predicting the pricing of cryptocurrencies is thought to be a difficult task due to their complexity.

2) Data Sources and data preparation:
To solve this problem, the dataset we have chosen to work with is Kaggle's Cryptocurrency Prices Data. This is a dataset containing historical OHLC (Open High Low Close) data for over 50 Cryptocurrencies. On a daily basis, the date range is from May 2013 to October 2022. The prices are shown in USD or $. The file format is CSV, which is tabular and loads faster. Using automated scripts, the data was scraped and cleaned from the Coin Market Cap website.
The dataset consists of 9 attributes:
•	open: Opening price on that particular date (UTC time)
•	high: Highest price hit on that particular date (UTC time)
•	 low: Lowest price hit on that particular date (UTC time)
•	close: Closing price on that particular date (UTC time)
•	volume: Quantity of asset bought or sold, displayed in base currency
•	marketCap: The total value of all the coins that have been mined. It's calculated by multiplying the number of coins in circulation by the current market price of a single coin
•	timestamp: UTC timestamp of the day considered
•	crypto_name: Name of the cryptocurrency
•	date: timestamp converted to date

3) Data exploration, visualization, cleansing and transformation

•	Data Cleansing: 
Firstly, unwanted columns were dropped, in this case timestamp column since the column consisted of dates similar to that of in the date column and the time was the same throughout the dataset i.e (23:59:59.999). 
Then it was checked if there are any missing values or null values in the dataset, the outcome for which came out to be negative.
The ‘marketCap’ column in the dataset consisted of huge numbers due to which the data format for the particular column was in the exponential form, this was handled using the .format method. 
Then, 2 more columns were added i.e Year and Month, this was extracted using  the ‘Date’ column. 

•	Data Pre-processing: 
To start with the preprocessing, dataset had huge number of outliers that were checked using Box-Plot and Inter-Quartile Range method was also used on the ‘close’ column which indicates the closing rate of the crypto-currency. We only considered data that belonged within 40-60 percentile since not all of the outliers in the dataset could be eliminated because of their sheer number. This is owing to the possibility that the outliers were caused by actual events. Taking into account the fact that the market for cryptocurrencies is quite volatile and has wide swings. We only looked at data that fell between the 40th and 60th percentile.

•	Data Exploration:
To explore and study the data, mean, median, mode, standard deviation and variations were calculated.
To study where most of the information is lying two types of operations were performed.
1.	Skewness: Skewness gives the information about the symmetry of the distribution.
2.	Kurtosis: Kurtosis gives the information about the heaviness of tail of the distribution.

Two types of Kurtosis were used for this exploration:
1.	Pearson Kurtosis.
2.	Fisher Kurtosis.

•	Data Transformation:
After the checking for the skewness and kurtosis the data was found to be left skewed since all the values had skewness value were above 5 hence it was overly left skewed. To handle this issue log transformation was performed on all the numerical columns. As a result, the skewness was normalized considerably. 

•	Data Visualisation: 
1.	Univariate Analysis:
-	Histogram for Lowest Price
-	Histogram for Highest Price
-	Histogram for Opening Price
-	Histogram for Closing Price
2.	Before and After Log Transformation Visuals:
-	MarketCap
-	Volume
3.	Bi-Variate Analysis:
-	Top 6 Trending Crypto Currency by Closing Price
4.	Multi-Variate Analysis:
-	Area Graph of Yearly Closing Price for Top 3 Crypto Currencies
-	Scatter Plot for Volume and MarketCap by Crypto Currencies
-	Line Graph for Yearly Trend of Bitcoin Price

4) Methodology – LSTM Approach 
Deep learning comprises of models that are multi-layered. RNN (Recurrent Neural Network), CNN (Convolutional Neural Networks), LSTM (Long Short-Term Memory) etc. For the scope of the project, we have used LSTM. 
LSTMs are a type of RNN that can learn in order and can be used to solve sequence prediction problems. It does not only process single data points (uni-variate), but also multiple data sequences (multi-variate). LSTMS are particularly useful for forecasting time series data. LSTMs, unlike traditional feedforward neural networks, have feedback connections that aid in data backward propagation. LSTM can be used for image classification, speech-to-text recognition, sales forecasting, and other applications.
A typical LSTM unit consists of a cell, an input gate, an output gate, and a forget gate. The cell retains values across arbitrary time periods thanks to the three gates that govern the flow of information into and out of it.
The first thing we'll do with our data is normalize its values. The goal of normalization is to convert the values of numeric columns in a data set to a common scale while preserving differences in value ranges. The training data contains all data from 2013-05-05 to 2021-03-31 and the test data contains data from 2021-04-02 to 2022-10-23. We drop the log transformed data as we have already normalized the actual data. 
Finding the right layers and hyperparameters for each one will require several tweaks and attempts. The model construction is straightforward and typical for this type of problem.
We finally get plot with the predicted and actual bitcoin price, as you can observe the model was able to provide a decent prediction of the prices. 

5) Modeling and results:
The model used to train the dataset was linear regression which was done using python. 4 features were taken into consideration i.e “open”, “high”, “low” and “volume” and closing price of bitcoin was treated as target variable. 
 
Evaluation:
The price of bitcoin fluctuates over time as observed in the graph. Initially, the price increases exponentially and hits its peak around 2021-11, before falling and plummeting around 2022-7. As per the test data, the price of bitcoin is on the decline although it does increase slightly around 2022-09, it continues to decline as time progresses. The model fits pretty well and scores 0.9999251513161072 which is confirmation of good fit. The price of bitcoin in USD was used as the metric of analysis.
Major challenges and solutions:
Dealing with outliers was one of the major challenges we faced. As outliers usually tend to impact the performance of a model, we had to eliminate the outliers. Although our data set had a huge number of outliers, not all of them can be removed. This is because the outliers may have been caused due to actual events. We also need to consider the fact that the cryptocurrency market is very volatile and has huge variations. Thus, we dealt with it by using IQR. We only considered data that belonged within 40-60 percentile.
As with a lot of data sets, our dataset was left skewed. Thus, to overcome, we applied log transformation and were able to achieve normal distribution. 
Conclusion and future work:
By means of this project, we were able to understand the entire life cycle of a model. Through our research in finding the right dataset, we were able to understand concepts of data acquisition. By applying pre-processing techniques and performing data manipulations, our grasp on data engineering was strengthened. Our understanding of feature engineering and model development was further strengthened upon completion of the project. In the future, we may be able to perform web scrapping and sentiment analysis on crypto currency trends. We can even explore visualizing plots through software such as Tableau etc. 
