---
title: "Zomato EDA: Insights into Indian Food Industry Trends"
seoTitle: "Zomato EDA: Insights into Indian Food Industry Trends"
seoDescription: "The EDA on the Zomato dataset provides valuable insights into the food industry and consumer behaviour in India. These insights can help businesses to grow."
datePublished: Sun Apr 23 2023 03:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clgstnvr701aehsnvf2ph2366
slug: zomato-eda-insights-into-indian-food-industry-trends
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682142754633/78a794b3-46ce-4e0a-9edf-c675229ef09f.png
tags: python, data-science, machine-learning, data-analysis, python3

---

Zomato is one of the most popular online food delivery platforms in India. But what can we learn from the data that Zomato collects and shares? In this blog post, I will explore some interesting insights from the Zomato dataset using exploratory data analysis (EDA). EDA is a process of summarizing, visualizing, and understanding the data before applying any machine learning or statistical techniques. It can help us discover patterns, trends, outliers, and anomalies in the data. Let's get started!

Dataset -- [https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants](https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants)

# Prerequisites

Before going forward, make sure you have covered the prerequisites, if not then you can check out my articles on those libraries:

* Pandas --&gt; [Click Here To Learn Pandas in 10 minutes](https://neuronize.dev/pandas-101-learn-pandas-in-10-minutes)
    
* Matplotlib --&gt; [Click Here To Learn Matplotlib in 10 minutes](https://neuronize.dev/matplotlib-101-learn-matplotlib-in-10-minutes)
    
* Seaborn --&gt; [Click Here To Learn Seaborn in 10 minutes](https://neuronize.dev/seaborn-101-learn-seaborn-in-10-minutes)
    

# Importing Libraries

Let's import all the libraries that we need.

```python
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

sns.set_style('dark')
```

# Load the Data

First, let's load the data.

```python
df = pd.read_csv("zomato.csv")
df
```

![zomato dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1681737573487/3bbc7838-5ca6-4e4e-83b5-76b6af796051.png align="center")

## Check the Shape of the Data

Now, let's check how many rows and columns are there in this dataset.

```python
df.shape

#--------------------- OUTPUT------------------------#
(51717, 17)
#--------------------- OUTPUT------------------------#
```

## List all the Columns

Now, we'll find out all the columns of this dataset.

```python
df.columns

# ----------------------- OUTPUT -------------------- #
Index(['url', 'address', 'name', 'online_order', 'book_table', 'rate', 'votes', 'phone', 'location', 'rest_type', 'dish_liked', 'cuisines', 'approx_cost(for two people)', 'reviews_list', 'menu_item', 'listed_in(type)', 'listed_in(city)'], dtype='object')
# ----------------------- OUTPUT -------------------- #
```

Now, let's start data preprocessing.

# Data Preprocessing

First, let's see all the columns, their data type and how many non-null values are there in each column.

```python
df.info()
```

![zomato dataset info](https://cdn.hashnode.com/res/hashnode/image/upload/v1681737656497/26daff2a-efe4-4748-a5ce-5cf440075468.png align="center")

You can see that there are a total of 51717 entries or rows and most of the columns have no null values and there's only one column with `int` datatype. The total size of the dataset is 6.7+ MB.

Now, we'll remove all the columns that we don't need for this analysis. If you want to keep them, then feel free to use them in your analysis but for this article, I won't be using them, so I'll just simply delete them for now.

### Deleting Columns

```python
#removing url column, address column, last column

df.drop(columns=["url", "address","phone","menu_item", "reviews_list", "listed_in(city)"], inplace=True)
```

`drop` function is used whenever we want to delete a row or column. Here, the `drop` function takes two parameters. `columns` is used to specify which columns we want to delete and `inplace` is used to modify the original dataset `df` in place.

Let's take a look at the data after dropping the columns.

```python
df
```

![dropped columns from the dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1681737806989/cdbf9506-dde9-4dd6-ae47-b929d1378f47.png align="center")

Now, let's see the shape of the data.

```python
df.shape

# ---------------------- OUTPUT ---------------- #
(51717, 11)
# ---------------------- OUTPUT ---------------- #
```

You can see that the changes are in-place i.e the columns from the original data frame `df` got deleted.

Now, let's preprocess some columns.

## Rate Column

In the above data frame figure, we want to remove the `/5` in every rating and we also need to check if there are null values or not, there also can be some weird or garbage values. So, let's start cleaning the `rate` column.

First, we'll check all the unique values in the `rate` column, this will help us to know if there are null values or not and also if there are garbage values or not.

```python
df["rate"].unique()
```

![all the unique values in the rate column](https://cdn.hashnode.com/res/hashnode/image/upload/v1681737939759/fd67fc27-3030-4168-8d10-323e1103f0a8.png align="center")

You can see that, there is a garbage value that is "NEW" and "-" and null values are also there as a `nan` is there.

So, let's start by removing the garbage values replacing them with null values and removing the "/5" from all the valid ratings.

```python
# remove NEW, -, /5 from the rating

def rate_handler(value):

    if value == "NEW" or value == "-":
    
        return np.nan
    
    else:
    
        value = str(value).split('/')
        
        value = value[0]
    
    return float(value)
    
df["rate"] = df["rate"].apply(rate_handler)

df.head()
```

![dataset after removing the garbage values of rate column](https://cdn.hashnode.com/res/hashnode/image/upload/v1681738054157/83059016-1b51-40da-b64f-7d7fa8618e64.png align="center")

Now, let's check all the unique values again to confirm that the garbage values and the "/5" are completely removed.

```python
df.unique()
```

![all the unique values of rate column after removing garbage values](https://cdn.hashnode.com/res/hashnode/image/upload/v1681738139261/ff3a82c7-6dc5-4419-8dfb-db6a15ff8254.png align="center")

This confirms that there are no garbage values and no /5.

Now let's fill the null values with the average rating of all the restaurants. You can use different strategies but I'll go with this one.

```python
#handling missing rate values

def missing_value_handler(column):

    df[column].fillna(df[column].mean(), inplace=True)

missing_value_handler("rate")
```

Now, let's check if there are null values present or not in the rate column.

```python
df["rate"].isnull().sum()

# --------------------- OUTPUT --------------------- #
0
# --------------------- OUTPUT --------------------- #
```

So, this confirms that there are no null values and we have cleaned the `rate` column.

## approx\_cost(for two people) Column

Similarly, let's check all the unique values to know if there are null and garbage values present in the column or not.

```python
df["approx_cost(for two people)"].unique()
```

![all the unique cost values](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078220975/e2d57686-b58a-416c-a3d4-1affc68c5467.png align="center")

You can see that cost values having 4 digits consist of a "," and we don't want that, so let's remove the ",".

```python
# remove the comma

def cost_handler(value):

    value = str(value)
    
    if ',' in value:
    
        value = value.replace(',', '')
    
        return float(value)
    
    else:
    
        return float(value)

  

df["approx_cost(for two people)"] = df["approx_cost(for two people)"].apply(cost_handler)

df.head()
```

* Here, the function `cost_handler()` takes an argument value which is the cost.
    
* Then we are converting the cost to string so that we can do string manipulation.
    
* Then, we are saying if the cost string consists "," then replace it with an empty string.
    
* Finally, we are typecasting the string to float and returning the value.
    

The `apply()` function can be used to apply a function to every value in a pandas series or data frame. Here, we are applying the `cost_handler()` function to the `df` data frame.

Now, let's take a look at all the unique values again just to confirm that we have removed all the commas.

```python
df["approx_cost(for two people)"].unique()
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078345021/e52854c5-286c-40dc-a6c1-e917f136151b.png align="left")

You can see that all the commas in the 4-digit cost have been removed.

If you want to can fill in the null values in the `cost` column but I'm not going to do that for this analysis.

# EDA

Now, let's start to ask some questions and try to get the answers with visualization.

These are the 5 questions that we'll try to answer and visualize:

1. Number of restaurants having online order facility
    
2. Top 10 best-rated restaurants
    
3. Top 10 cuisines served by restaurants
    
4. Number of Restaurants in every location
    
5. Top 10 liked dishes
    

### Number of restaurants having online order facility

```python
sns.countplot(df["online_order"])
```

![number of restaurants having online order facility](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078421449/056c7b9b-713a-4500-829b-85ddc772ad41.png align="center")

Most restaurants provide online order service, and nearly 30,000 restaurants provide online order service. To find the exact number you can use pandas `value_counts` to get the count for each of the option `yes` and `no`.

### Top 10 best-rated restaurants

```python
# top 10 rated restaurants

df.groupby("name")["rate"].mean().sort_values(ascending=False).head(10)
```

* Here, we are grouping the data concerning `name` of restaurants.
    
* Then finds the mean of all the ratings for that particular restaurant.
    
* Finally, we are sorting the output of the above in decreasing order to get the highest ratings and then retrieving the top 10 data using `head(10)`.
    

![top 10 best-rated restaurants](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078483340/9deea75b-3644-43cd-a4c1-e0c26a7cb046.png align="center")

### Top 10 Cuisines Served

```python
# top 10 cousines served by restaurants

cousines = {}

def cousines_handler(value):

	value = str(value).split(',')
	
	for cousine in value:

		cousine = cousine.strip()

		if cousine in cousines:
		
			cousines[cousine] += 1
		
		else:
		
			cousines[cousine] = 1

for value in df["cousines"]:

	cousines_handler(value)

  

print(cousines)

# convert this to dataframe
cousines = pd.DataFrame(list(cousines.items()), columns=["cousines", "count"])

cousines

  
# getting the top 10 cousines
top_10_cousines = cousines.sort_values("count", ascending=False).head(10)

  
# plotting the top 10 cousines
top_10_cousines_bar_plot = sns.barplot(data=top_10_cousines, x="cousines",y="count")

top_10_cousines_bar_plot.set_xticklabels(top_10_cousines_bar_plot.get_xticklabels(), rotation=45, horizontalalignment='right')
```

* Here, first, we are creating a dictionary that will hold the count for every cuisine.
    
* Then, the function `cousines_handler()` is used to fill the dictionary
    
* Now, we converted the dictionary into a data frame just for best practices otherwise you could directly find the top 10 cuisines from the dictionary too.
    
* Now, we sorted the data frame in a decreasing manner using the `count` column.
    
* Finally, we plotted a bar graph with the above data and the last line is used to make the x-ticks rotate to 45 degrees so that the labels are easily visible.
    

![Top 10 Cuisines Served](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078601360/f91aa8e8-0d28-42b7-aada-6ecb5bba1301.png align="center")

You can observe that the most served cuisine is North Indian followed by Chinese.

### Top 10 Locations with Highest Restaurants

```python
# top 10 locations with highest restaurants

number_of_outlets = df.groupby("location")["name"].count()

# getting the top 10 location with most number of restaurants
top_10_location_with_highest_restaurants = number_of_outlets.sort_values(ascending=False).head(10)

  
# plotting the top 10 locations
top_10_location_with_highest_restaurants_bar_plot = sns.barplot(x=top_10_location_with_highest_restaurants.index, y=top_10_location_with_highest_restaurants.values)

# setting the xticks
top_10_location_with_highest_restaurants_bar_plot.set_xticklabels(top_10_location_with_highest_restaurants_bar_plot.get_xticklabels(), rotation=45, horizontalalignment='right')
```

* Here we are grouping the data using location.
    
* Then count the number of restaurants per location using the name.
    
* Finally, we just sort the restaurants in a decreasing manner concerning count and retrieving the top 10 using `head(10)`.
    
* Now, just plot the above result using seaborn, this is very similar to the top 10 cuisine question.
    

![Top 10 Locations with Highest Restaurants](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078705916/c07e003c-2f1e-4009-9226-8a4e7a45c98e.png align="center")

From this, we can observe that BTM has the most number of restaurants.

### Top 10 Liked Dishes

```python
# top 10 liked dishes

liked_dishes = {}

def liked_dishes_handler(value):

	value = str(value).split(',')
	
	for liked_dish in value:

		liked_dish = liked_dish.strip()
	
		if liked_dish in liked_dishes:
		
			liked_dishes[liked_dish] += 1
		
		else:
		
			liked_dishes[liked_dish] = 1

for value in df["dish_liked"]:

	liked_dishes_handler(value)

  

print(liked_dishes)

# convert this to dataframe

liked_dishes = pd.DataFrame(list(liked_dishes.items()), columns=["dishes", "count"])

liked_dishes

  
# getting the top 10 liked dishes
top_10_liked_dishes = liked_dishes.sort_values("count", ascending=False)[1:11]

  
# plotting the top 10 dishes
top_10_liked_dishes_bar_plot = sns.barplot(data=top_10_liked_dishes, x="dishes",y="count")

# setting the x-ticks
top_10_liked_dishes_bar_plot.set_xticklabels(top_10_liked_dishes_bar_plot.get_xticklabels(), rotation=45, horizontalalignment='right')
```

We are handling this almost the same as we did with the top 10 cuisine questions:

* We created a dictionary to store the count of liked\_dish per dish.
    
* Then the function is used to fill the dictionary with the dish as key and count as value.
    
* We converted the dictionary to a data frame.
    
* Finally, we sorted the data frame in decreasing order concerning count and plotted it using a barplot.
    

![top 10 liked dishes](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078789374/91e52152-a1cc-4d6e-95cd-1742d24e2ef4.png align="center")

From this, we can observe that Pasta is the most liked dish followed by Burgers.

# Conclusion

Based on the exploratory data analysis (EDA) conducted on the Zomato dataset, several insights have been uncovered about the food industry and consumer preferences in different cities across India.

The analysis revealed that online ordering and delivery have become increasingly popular, especially in urban areas. This trend has been further accelerated by the COVID-19 pandemic, which has led to a shift toward contactless and online ordering options.

One of the key findings of the analysis was the popularity of North Indian cuisine across most cities, followed by Chinese and South Indian cuisine. This highlights the importance of understanding regional food preferences to cater to the local market.

Another significant insight has been found that pasta is the most popular dish among consumers, followed by burgers. These insights can be used by food businesses to better understand consumer preferences and cater to their needs to improve customer satisfaction and drive business growth.

Overall, the EDA on the Zomato dataset provides valuable insights into the food industry and consumer behavior in India. These insights can be leveraged by businesses and policymakers to make data-driven decisions and improve their understanding of the market.