---
title: "Seaborn 101 - Learn Seaborn in 10 Minutes"
seoTitle: "Seaborn 101 - Learn Seaborn in 10 minutes"
seoDescription: "You'll learn how to customise the aesthetics, how to plot different kinds of charts, and how to use statistical methods to explore your data."
datePublished: Sun Apr 16 2023 04:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clgiwso7c034ananvdcy79m06
slug: seaborn-101-learn-seaborn-in-10-minutes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681516127882/1f5c7bb1-68f5-41e8-bb48-8c982e1adc20.png
tags: programming-blogs, python, data-science, machine-learning, python-beginner

---

Seaborn is a powerful and versatile Python library for data visualization. It provides a high-level interface to create beautiful and informative plots from various types of data, such as pandas dataframes, numpy arrays, or Python lists.

In this blog post, I will introduce you to some of the features and functionalities of seaborn, such as how to customise the aesthetics, how to plot different kinds of charts, and how to use statistical methods to explore your data. By the end of this post, you will have a solid foundation to start using seaborn for your own projects and analyses.

I’ll be using the Titanic dataset. [Click Here to Download](https://www.kaggle.com/datasets/yasserh/titanic-dataset)

### Installing Seaborn

You can install seaborn in two ways:

#### Using pip

```python
pip install seaborn
```

#### Using conda

```python
conda install -c anaconda seaborn
```

### Importing Libraries

Let’s import the required libraries:

```python
import numpy as np  
import pandas as pd  
import seaborn as sns
import matplotlib.pyplot as plt
```

### Load the Data

Let’s load the Titanic dataset

```python
titanic_df = pd.read_csv("Titanic-Dataset.csv")
```

#### Take a Look at the Data

```python
titanic_df
```

![titanic dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1681513640997/1cf24dd0-2286-4de3-88c0-2e26ae51decf.png align="center")

# Distribution Plots

## Histogram

A histogram is a type of graph that shows the distribution of a numerical variable. It divides the data into bins or intervals and counts how many observations fall into each bin. For example, if we want to visualize the distribution of age of all passengers, we can use a histogram to see how many passengers belong in each bin. A histogram can help us understand the shape, centre, and spread of the data, as well as identify any outliers or gaps. Let's say you want to get the distribution of `total_rooms`, then you can use `his plot`.

```python
sns.histplot(titanic_df["Age"])

plt.show()
```

![histogram of age of all passengers](https://cdn.hashnode.com/res/hashnode/image/upload/v1681513755360/50d53a3f-5323-40de-b560-a42687ebc7f1.png align="center")

You can observe that most of the passengers are young adults and there are very few senior citizens.

You can also set the number of bins you want:

```python
sns.histplot(titanic_df["Age"], bins=10)

plt.show()
```

![histogram of age of all passengers using 10 bins](https://cdn.hashnode.com/res/hashnode/image/upload/v1681513833872/f415842e-4dc4-4f79-95e0-be88bb594e50.png align="center")

You can see that now there are only 10 bins and each of them is separated with an interval of 10. With this, you can observe that most of the passengers belong to 20-40 age group.

<mark>From now on, I'll be using California Housing Dataset because Titanic Dataset isn't that good for some of the plots that I'll be going to create.</mark>

[Click Here to Download the Dataset](https://www.kaggle.com/datasets/camnugent/california-housing-prices)

Let's import the California Housing dataset.

```python
df = pd.read_csv("housing.csv")
```

## Joint Plot

A jointplot is a type of plot that shows the relationship between two variables. It combines a scatter plot and a histogram for each variable.

For example, you can use a jointplot to visualize the relationship between total bedrooms and households in the California dataset. The scatter plot shows how the two variables are correlated, and the histograms show the distribution of each variable. You can create a jointplot using the seaborn library in Python. Here is an example code:

```python
sns.jointplot(x="total_bedrooms", y="households", data=df)
plt.show()
```

![jointplot of households and total bedrooms column](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514107816/0f4457db-5ec1-4138-ba30-a27171fd70ed.png align="center")

You can see that the higher the total number of bedrooms, the higher the number of households.

You can also change the kind of joint plot. Let's say you want a regression line and not just a scatter plot, then use the `kind` parameter.

```python
sns.jointplot(x="total_bedrooms", y="households", data=df, kind='reg')
```

![jointplot with regression line](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514209247/b33f5a58-8385-4347-983d-0260959aef09.png align="center")

## Pair Plot

A pairplot is a way of visualizing the relationships between multiple variables in a dataset. It shows a scatter plot for each pair of variables, and a histogram for each variable along the diagonal. A pairplot can help you explore the patterns and correlations in your data.

For example, you can use a pairplot to analyze the California housing dataset, which contains information about the median house value, median income, population, and other features for different locations in California. A pairplot can show you how these variables are related to each other, and which ones are most important for predicting the house value.

```python

sns.pairplot(df)
```

![pairplot of california dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514256652/82f6aa0f-7dac-4c0b-a29e-6c6ef78d2cc9.png align="center")

# Categorical Plots

## Bar Plots

A barplot is a type of graphical display that shows the relationship between a numerical variable and a categorical variable. Each category is represented by a rectangular bar, whose height or length is proportional to the numerical value. A barplot can also show the distribution of values within each category, using different colours or patterns to indicate subgroups.

Suppose we want to compare the median house value across different ocean proximity categories. We can create a barplot using the following code:

```python
sns.barplot(x='ocean_proximity', y='median_house_value', data=df)

plt.show()
```

![barplot of ocean proximity and median house value](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514371687/9ffeb1eb-1688-4821-95cd-f054fba6571c.png align="center")

We can see that the districts near the ocean have higher median house values than those inland ( not island ). We can also see the error bars that indicate the confidence intervals for each category. The confidence intervals are computed using bootstrapping, which is a statistical technique to estimate the variability of a sample statistic.

## Count Plot

A countplot is a type of bar plot that shows the counts of observations in each categorical bin. It can be useful for visualizing the distribution of a categorical variable or comparing the frequencies of different groups.

For example, we can use a countplot to show how many houses in the California housing dataset have different ocean proximity values. To do this, we need to import seaborn and matplotlib libraries, load the dataset, and use the `sns.countplot()` function with the `data` and `x` parameters. Here is some code that does this:

```python

sns.countplot(data=df, x="ocean_proximity")
plt.show()
```

![countplot of ocean proximity](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514531814/9ff45289-8304-47c6-ab05-61d0743416a6.png align="center")

We can see that most of the houses are located in the inland area, followed by &lt;1H OCEAN, NEAR OCEAN, and NEAR BAY. There are very few houses in the ISLAND category.

## Box plot

A boxplot is a way of showing the distribution of a numerical variable. It uses a rectangular box to represent the middle 50% of the data, and whiskers to show the range of the rest of the data. The line inside the box is the median, or the middle value of the data. A boxplot can help you compare different groups of data and identify outliers. For example, if you have a dataset about housing prices in California, you can use a boxplot to see how the prices vary by region or by house type.

```python
sns.boxplot(data=df, x="ocean_proximity", y="median_house_value")
```

![boxplot of ocean proximity and median house value](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514679342/69f3dac5-4aa0-4283-9045-5ab7e9f079ac.png align="center")

* The line inside the rectangle represents the **median** or the **50th percentile** which means that 50% of the data falls below this value and 50% of the data falls above this value.
    
* The top end of the rectangle in a box plot represents the **75th percentile** or the **third quartile** which means that 25% of the data falls above this value and 75% of the data falls below this value.
    
* The bottom end of the rectangle represents the **25th percentile** or the **first quartile** which means that 25% of the data falls below this value and 75% of the data falls above this value.
    

## Violin Plot

A violin plot is a type of chart that shows the distribution of a numerical variable for different categories. It combines a box plot with a kernel density plot, which shows the shape of the data using a smooth curve. A violin plot can help us compare how the values of a variable vary across different groups.

For example, we can use a violin plot to compare the median house value for different regions in California, using the California housing dataset. The dataset contains information about 20,640 census blocks in California, such as population, income, and house value. We can use the seaborn library in Python to create a violin plot with the following code:

```python
sns.violinplot(x="ocean_proximity", y="median_house_value", data=df)
```

![violin plot of ocean proximity and median house value](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514742031/d807ffd3-446c-45bd-a4c4-8880191c3103.png align="center")

We can see that the median house value is higher for blocks near the ocean or bay than for blocks inland or on an island. We can also see that there is more variation in house value for blocks near the bay than for other categories.

# Matrix Plots

## Heatmaps

Heatmaps are a great way to visualize correlations between variables. They are a graphical representation of data where the individual values contained in a matrix are represented as colours. Heatmaps are useful for visualizing complex data sets and identifying patterns that may not be immediately apparent in a table or spreadsheet.

```python
plt.figure(figsize=(12,8))

df_corr = df.corr()

sns.heatmap(df_corr, annot=True)
```

![heatmap of california house dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1681514796875/24f352a2-c0f1-4904-8425-1e3c3e54688a.png align="center")

* I use `plt.figure()` to change the size of the figure, it's the same as we did in the matplotlib 101 tutorial.
    
* Then, to build a heatmap you need to create a dataframe which consists of correlation of every pair of columns. `.corr()` is used to find correlation.
    
* `.heatmap()` take the dataframe and builds the heatmap
    
* I have used `annot` parameter to see the correlation value for every pair inside the heatmap.
    

# Styling Seaborn Figures

For this section, we'll again use the titanic dataset.

### Import The Data

```python
df = pd.read_csv("Titanic-Dataset.csv")
```

## Hue

One of the parameters that seaborn accepts is hue, which can be used to group data by a categorical variable and assign different colors to each group. For example, if we have a dataset about California housing prices, we can use hue to show the median house value by ocean proximity.

To use hue in seaborn, we need to specify the name of the column that contains the categorical variable as the hue argument. We also need to specify the column that contains the numerical variable as the x or y argument, depending on the type of plot we want to create. For example, if we want to create a histogram of median house values by ocean proximity, we can use the following code:

```python

# Create a histogram of Sex using Survived as hue
sns.countplot(x='Sex', hue='Survived', data=df)
```

![histogram of sex using survived as hue](https://cdn.hashnode.com/res/hashnode/image/upload/v1681515043746/ac14d26e-9828-45ab-b7d6-3359a2d82007.png align="center")

This plot shows that more females survived than males, and more males died than females. The hue parameter adds a color dimension to the plot based on the survived column, which has two values: 0 (died) and 1 (survived).

We can also use hue to show the distribution of a continuous variable by a categorical variable. For example, let us create a violin plot that shows the distribution of age by sex and survival status:

```python
sns.violinplot(x='sex', y='age', hue='survived', data=df)
```

![violinplot of age,sex using survived as hue](https://cdn.hashnode.com/res/hashnode/image/upload/v1681515123732/c8f3b366-c8c7-4b3c-a9ef-f07df0636cb8.png align="center")

This plot shows that younger females had a higher survival rate than older females, while older males had a lower survival rate than younger males. The hue parameter splits the violin plot by the survived column, creating two violins for each sex.

Finally, we can use hue to show the relationship between two categorical variables by a third categorical variable. For example, let us create a bar plot that shows the proportion of passengers who survived by sex and class:

```python
sns.barplot(x='Sex', y='Survived', hue='Pclass', data=titanic_df)
```

![barplot of sex,survived using Pclass as hue](https://cdn.hashnode.com/res/hashnode/image/upload/v1681515166265/0c552326-501a-465f-872d-5da11ad97190.png align="center")

This plot shows that females had a higher survival rate than males in all classes, and that first class passengers had a higher survival rate than second and third class passengers. The hue parameter adds a third dimension to the bar plot based on the class column, which has three values: First, Second, and Third.

In summary, seaborn hue is a useful parameter that can add color and depth to a plot based on another categorical variable. It can be used with various types of plots such as count plots, violin plots, and bar plots. It can help us explore and understand the data better by highlighting patterns and differences among groups.

## Figure Styles

There are five preset seaborn themes: `darkgrid`, `whitegrid`, `dark`, `white`, and `ticks`. They are each suited to different applications and personal preferences. The default theme is `darkgrid`. I prefer `darkgrid` as it's gives me a sense of dark mode.

```python
sns.set_style("darkgrid")

sns.violinplot(x='Sex', y='Age', hue='Survived', data=titanic_df)
```

![changed figure style to dark](https://cdn.hashnode.com/res/hashnode/image/upload/v1681515209974/e3fd219d-dfe1-4a47-ad59-cf7220c370a3.png align="center")

I have just plotted the previous chart but used the dark-grid figure style.

# Subplots

One of the features of seaborn is the ability to create subplots, which are multiple plots in a single figure. Subplots can be useful for comparing different aspects of a dataset or showing different levels of a categorical variable.

We will use seaborn to create two subplots: one that shows the distribution of age by survival status, and another that shows the count of passengers by class and sex.

To create subplots with seaborn, we need to use the FacetGrid class, which creates a grid of axes for plotting conditional relationships. The FacetGrid constructor takes a data frame and one or more arguments that specify how to split the data into different subplots. For example, we can use the col argument to create subplots based on a categorical variable, such as sex. Then, we can use the map method to apply a plotting function to each subplot. For example, we can use sns.distplot to plot the distribution of age.

The code below shows how to create a FacetGrid with two subplots based on sex, and plot the distribution of age by survival status using sns.distplot:

```python

# Create a FacetGrid with two columns based on sex

g = sns.FacetGrid(data=titanic_df, col='Sex')

  

# Map sns.distplot to each subplot with age as x and survived as hue

g.map(sns.histplot, 'Age', kde=False, palette='Set1')

  

# Add a legend and adjust the layout

g.add_legend()

g.tight_layout()
```

![subplots  using seaborn](https://cdn.hashnode.com/res/hashnode/image/upload/v1681515238750/4ccd4771-8ffe-4ff4-9ff6-58286f109c6c.png align="center")

We can see that both in male and female category, most of the passengers are young and there are no female passengers over the age of 60 but there are some male passengers who are over the age of 60.

# Conclusion

In this blogpost, we learned seaborn, a powerful and elegant Python library for data visualization. We have seen how to create different types of plots, such as scatter plots, histograms, box plots, and heatmaps, using simple and intuitive commands. We have also explored how to customize the appearance of our plots. Seaborn is a great tool for exploring and communicating insights from data, and I hope this blogpost has inspired you to try it out for yourself.