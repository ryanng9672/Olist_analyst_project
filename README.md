# Olist_analyst_project
**Project Description**
* Olist Store is the largest department store in Brazilian marketplaces. Olist connects small businesses from all over Brazil to channels without hassle and with a single contract. The Brazilian ecommerce public dataset of orders (from 2016 to 2018) made at Olist Store is provided to your company for analysis.
Your manager is asking you to critically analyse the provided datasets using Business Intelligence tools and provide some marketing findings / recommendations in a report format. The dataset has information of 100k orders made at multiple marketplaces in Brazil. Its features allow viewing an order from multiple dimensions: from order status, price, payment and freight performance to customer location, product attributes and finally reviews written by customers. A geolocation dataset that relates Brazilian zip codes to lat/lng coordinates is also integrated in the dataset.
After a customer purchases the product from Olist Store, a seller gets notified to fulfill that order. Once the customer receives the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where they can give a note for the purchase experience and write down some comments.
![Alt text](https://miro.medium.com/v2/resize:fit:1200/1*keRx7Vf35vpi0s9WdjWV8A.png)

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


