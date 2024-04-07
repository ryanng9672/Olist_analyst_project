# Olist_analyst_project
**Project Description**
* Olist Store is the largest department store in Brazilian marketplaces. Olist connects small businesses from all over Brazil to channels without hassle and with a single contract. The Brazilian ecommerce public dataset of orders (from 2016 to 2018) made at Olist Store is provided to your company for analysis.
Your manager is asking you to critically analyse the provided datasets using Business Intelligence tools and provide some marketing findings / recommendations in a report format. The dataset has information of 100k orders made at multiple marketplaces in Brazil. Its features allow viewing an order from multiple dimensions: from order status, price, payment and freight performance to customer location, product attributes and finally reviews written by customers. A geolocation dataset that relates Brazilian zip codes to lat/lng coordinates is also integrated in the dataset.
After a customer purchases the product from Olist Store, a seller gets notified to fulfill that order. Once the customer receives the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where they can give a note for the purchase experience and write down some comments.
![Alt text](https://miro.medium.com/v2/resize:fit:1200/1*keRx7Vf35vpi0s9WdjWV8A.png)
# Table of Content
* [Possible scopes of the marketing findings / recommendations from the dataset] (Possible scopes of the marketing findings / recommendations from the dataset)
# Possible scopes of the marketing findings / recommendations from the dataset
* Feedback Sentiment Analysis: Evaluate the polarity of the tweets as customer feedback positive, negative or neutra
* Clustering: Some customers did not write a review. But why are they happy or mad?
* Sales Prediction: With purchase date information you will be able to predict future sales.
* Delivery Performance: You will also be able to work through delivery performance and find ways to optimize delivery times

# Project Objectives
* #Use Power BI to answer following questions
* How many customers, orders, and orders per customer does the company have?
* What is the number of customers by state?
* What is the number of orders by month?
* What are the top 5 product categories?
* Visualise the company’s customers’ demographics, sales trend, orders by categories, orders changes by year, etc. and use Power BI to help make better decisions
* Map and compare report data with data from database query to validate the reports (functional testing)
* Critically analyse relevant data using statistical methods (e.g. Predictive Modelling or Machine Learning)

# SET_UP
To Run this project, install it locally Or in Virtual Environment as your refercence, using Python Package Managers (pip) :
```shell
pip install -r requirements.txt
```

# python
**data cleaing**
```shell
#def missing data
def missing_info(data,num):
    null_data = clean_df.isnull().sum().sort_values(ascending=False)
    percent = clean_df.isnull().sum()/data.isnull().count()
    missing_data = pd.concat([null_data,percent.apply(lambda x: format(x, '.2%'))],axis=1,keys=['T_missing','missing %'])
#drop nall
na_df=clean_df.dropna()
#check duplicated
na_df.duplicated()
```
**nltk**
```shell
#use the DeepL api to Translate English and find the keyword
df_en['result'] = df_en['result'].astype(str)
def extract_trigrams(text):
    text = text.translate(str.maketrans('', '', string.punctuation)).lower()
    tokens = word_tokenize(text)
    trigrams = ngrams(tokens, 3)
    return [' '.join(tri) for tri in trigrams]

trigrams_list = df_en['result'].apply(extract_trigrams).tolist()
trigrams_list = [trigram for sublist in trigrams_list for trigram in sublist]

trigram_counts = Counter(trigrams_list)
most_common_trigrams = trigram_counts.most_common(150)
```
**RandomForestClassifier**
#Machine Learning in python
```shell
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=101)
rf = RandomForestClassifier(n_estimators=100, random_state=101)
rf.fit(X_train, y_train)
predictions = rf.predict(X_test)
accuracy = accuracy_score(y_test, predictions)
conf_matrix = confusion_matrix(y_test, predictions)
class_report = classification_report(y_test, predictions)
#Giving up because of a 69% hit rate
```
# Analysis（powerBI)(16Page)[Dashboard link](https://app.powerbi.com/links/2N6xyywIlN?ctid=ed1bf5fb-9f74-42ae-9ecc-f244d532c626&pbi_source=linkShare)
The various analysis tasks are listed and explained below:
**Joining data**
The original data is used to derive multiple datasets by joins and manipulations. The Data manipulation and combinig jupyter notebook contains the step by step process and explanations.
* Preliminary data analysis
The Desktop Preliminary Data analysis contains the detailed analysis. This notebook visualizes and summarizes the original and the combined datasets, to find trends, patterns or faults. This analysis gives a holistic view of th dataset.

# **GMV analysis**
![螢幕擷取畫面 2024-04-02 180458](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/6a03ad23-9a79-45c3-a3a6-ab56284657d9)
![螢幕擷取畫面 2024-04-02 180517](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/ae83732b-7dbc-43d1-9832-254e2eae178b)
**An overarching examination of GMV will reveal the growth trajectory of Olist's sales. We will delve into the patterns and fluctuations in GMV across various timeframes, identifying peak periods and potential areas for expansion.Customer behavior analysis sheds light on the purchasing patterns that contribute significantly to GMV. Repeat purchase rates, average order value, and customer lifetime value are among the metrics analyzed to understand their impact on the platform's financial performance.**


# **Product analysis**
![螢幕擷取畫面 2024-04-02 180554](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/7b0c02ac-641e-402f-9112-0950519884ae)
![螢幕擷取畫面 2024-04-02 180604](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/d178a936-e9a3-4f03-ba80-9bd72830590d)
**The objective of this analysis is to find the most popular products, popular product categories and category wise popular products in the Olist ecosystem. Further, the delivery times and product characteristics , are compared to popularity to find correlations in the data. The Product analysis notebook contains the detailed code.**

# **Reviews sentiment analysis**
![螢幕擷取畫面 2024-04-02 180616](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/f921b140-e173-485f-9d9e-c89341e975af)
**Sentiment analysis is carried out on the reviews offered by customers. The notebook contains Supervised and Unsupervised methods for sentiment analysis, Reviews Sentiment Analysis.**

# **Freight value prediction**
![螢幕擷取畫面 2024-04-02 180641](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/c3d9f1c3-3d17-4930-bddf-da05402fda9f)
![螢幕擷取畫面 2024-04-02 180651](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/9f26a2de-4f78-49bb-8316-f8ca9d0cd27c)
**The freight value is the shipping value associated with each order. The Freight value prediction notebook contains detailed model building steps to predict the shipping value for an order, given the distance between seller and customer, the dimensions and weight of the product.**

# **RFM analysis**
![螢幕擷取畫面 2024-04-02 180716](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/c6116e76-a957-4e30-bdaa-c08332bfe82b)
**RFM analysis is a marketing technique used to quantitatively rank and group customers based on their purchasing patterns. RFM stands for Recency, Frequency, and Monetary value, each corresponding to a key customer trait. Recency measures how recently a customer made a purchase, Frequency assesses how often they make purchases, and Monetary value determines how much money they have spent on purchases over a specific period. This analysis helps businesses to identify high-value customers and develop targeted marketing strategies.**

# What is the most important issue for OLIST to address?
**In our analysis, the first and foremost problem that needs to be solved is the transportation time.**
![螢幕擷取畫面 2024-04-02 180728](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/7d7f9b1a-82bb-4b7f-919a-07474e75af92)
![螢幕擷取畫面 2024-04-02 180736](https://github.com/ryanng9672/Olist_analyst_project/assets/158177590/986badf3-68d3-4399-afde-b5c9e22347bd)


# Technologies
* Pandas
* numpy
* train_test_split
* more in requirements.txt

# PPT/Project_file
* ppt have our Improvement of Opinions [https://tome.app/ryan-e262/grouppjd-cltzhcae40fy0ll5y2u6gfg7a]
* [>>**project_file**<<](https://github.com/ryanng9672/Olist_analyst_project/tree/main/project_file)
  #project_file have pdf and pbix
  





