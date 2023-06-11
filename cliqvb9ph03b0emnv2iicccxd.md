---
title: "Learn Handling Missing Data in 10 Minutes"
seoTitle: "Learn Handling Missing Data in 10 Minutes"
seoDescription: "Master missing data handling quickly with this guide on strategies, techniques, and the Titanic dataset example"
datePublished: Sun Jun 11 2023 03:30:42 GMT+0000 (Coordinated Universal Time)
cuid: cliqvb9ph03b0emnv2iicccxd
slug: learn-handling-missing-data-in-10-minutes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686342662256/bda86c7d-c967-4c45-9d8d-edcd2b34c8f6.png
tags: python, data-science, machine-learning, data-analysis, python3

---

In the realm of data analysis and machine learning, working with real-world datasets often entails encountering missing data. Missing data can be a significant hurdle that compromises the integrity and accuracy of our analyses, leading to biased results and unreliable insights. Consequently, it becomes essential to address missing data appropriately to ensure the robustness of our models and the validity of our conclusions.

In this blog post, we will delve into the intricacies of handling missing data in a dataset. We will explore various strategies and techniques that can be employed to effectively deal with missing values, allowing us to unlock the full potential of our data.

Throughout this journey, we will utilize the popular Titanic dataset from Kaggle as a practical example. This dataset contains information about the passengers aboard the Titanic, including their demographics, cabin details, and survival outcomes. By applying different missing data handling techniques to this dataset, we can gain valuable insights into how each method impacts the data and the subsequent analysis.

We will begin by understanding the different types of missing data and the mechanisms behind their occurrence. We'll explore Missing Completely at Random (MCAR), Missing at Random (MAR), and Missing Not at Random (MNAR) patterns, shedding light on the underlying reasons for missingness in our dataset.

Next, we will dive into various imputation techniques, which involve filling in the missing values with estimated or imputed values. We will explore simple imputation methods such as mean, median, and mode imputation, as well as more advanced techniques like regression imputation and k-nearest neighbors imputation. Each method has its strengths and limitations, and we will discuss when to utilize them based on the nature of the missingness and the characteristics of the dataset.

# Prerequisite

#### Pandas

If you want a refresher of pandas, then you can check out my [Pandas 101 - Learn Pandas in 10 minutes](https://neuronize.dev/pandas-101-learn-pandas-in-10-minutes) article.

In the context of missing data, there are several terms that describe different patterns or mechanisms by which data can be missing. Let's clarify some of the commonly used terms:

# Missing Completely At Random ( MCAR )

MCAR refers to a scenario where the missingness of data points is unrelated to the observed or unobserved variables. In other words, the missingness occurs randomly and does not depend on any other variables in the dataset.

## Example

Consider a study investigating the effect of a new medication on blood pressure. The researchers collect data from participants, including their age, gender, and blood pressure measurements before and after taking the medication. However, due to an error during data collection, some participants' blood pressure measurements after taking the medication are missing.

To determine if the missingness is MCAR, we need to assess whether the probability of missingness is unrelated to both observed and unobserved variables.

In this scenario, if the missingness of blood pressure measurements after medication is MCAR, it means that the probability of missingness is the same for all participants, regardless of their age, gender, or actual blood pressure values.

Here's an example to illustrate MCAR:

* Let's say the missingness of blood pressure measurements after medication is unrelated to both observed and unobserved variables. It occurs purely by chance, and there is no pattern or relationship between the missingness and any other variables in the dataset.
    
* For instance, during the data collection process, the missingness of blood pressure measurements after medication may be due to technical issues like a malfunctioning device that failed to record some readings. This missingness is not related to any characteristics of the participants, such as their age, gender, or actual blood pressure values.
    
* In this case, the probability of missingness is consistent across all participants, regardless of their characteristics or actual blood pressure values. The missingness is completely random and not influenced by any systematic factors.
    

To confirm if the missingness is MCAR, you can examine the missingness patterns in the dataset and perform statistical tests, such as Little's MCAR test. These analyses aim to identify any relationships between the missingness and observed variables or auxiliary variables.

Remember that assessing the missingness mechanism is not always definitive, and it requires careful examination of the data, domain knowledge, and statistical tests. The MCAR assumption is commonly made in statistical analyses, but it's crucial to consider the limitations and potential biases associated with different missingness mechanisms.

# Missing At Random ( MAR )

Missing At Random (MAR) occurs when the probability of missingness depends on observed variables but is unrelated to unobserved variables.

## Example

Consider the same example of the study investigating the effect of a new medication on blood pressure. In this case, let's assume that the missingness of blood pressure measurements after medication is related to the participants' age but not directly related to their actual blood pressure values.

Here's an example to illustrate MAR:

* In the dataset, the missingness of blood pressure measurements after medication is not completely random but depends on an observed variable, which is the participants' age. Younger participants tend to have a higher likelihood of having missing blood pressure measurements after medication, regardless of their actual blood pressure values.
    
* For instance, during the data collection process, it was found that the younger participants had difficulty using the blood pressure measurement device correctly, resulting in a higher rate of missing measurements for this group. However, for participants of all ages who managed to provide measurements, the missingness is unrelated to their actual blood pressure values.
    
* In this case, the missingness is related to an observed variable (age) but unrelated to the unobserved variable (actual blood pressure values) within each age group. The missingness pattern is not completely random, but it is systematic and depends on a specific observed variable.
    

To handle missing data under the MAR assumption, various imputation techniques can be used. For example, you can impute missing values using regression imputation, where the observed variables (such as age) are used to predict the missing values.

It's important to note that the MAR assumption cannot be verified directly since the unobserved variables are unknown. Instead, it is based on the assumption that any systematic relationship between the missingness and the observed variables has been captured. Sensitivity analyses and careful consideration of the underlying assumptions are crucial when dealing with MAR.

# Missing Not At Random ( MNAR )

Missing Not At Random (MNAR) occurs when the missingness of data is related to the unobserved values themselves, even after accounting for observed variables.

## Example

Continuing with the same example of the study on the effect of a new medication on blood pressure, let's assume that the missingness of blood pressure measurements after medication is directly related to the participants' actual blood pressure values. In other words, participants with higher blood pressure values are more likely to have missing measurements after medication.

Here's an example to illustrate MNAR:

* In the dataset, the missingness of blood pressure measurements after medication is related to the participants' actual blood pressure values. Participants with higher blood pressure values have a higher likelihood of having missing measurements after medication.
    
* For instance, participants with higher blood pressure values might have experienced discomfort or adverse effects from the medication, leading them to refuse or omit providing their post-medication blood pressure measurements. This missingness pattern is directly related to the unobserved variable of interest (actual blood pressure values).
    
* In this case, the missingness is not random and cannot be explained solely by observed variables. It depends on the unobserved values themselves and introduces potential biases in the analysis if not properly addressed.
    

Handling missing data under the MNAR assumption is challenging since the missingness is related to unobserved variables. Specialized techniques, such as selection models or pattern-mixture models, are often used to handle MNAR. These approaches aim to model the missingness mechanism explicitly and make assumptions about the relationship between the missingness and the unobserved values.

It's important to note that MNAR is the most challenging type of missing data mechanism to handle since it assumes missingness patterns that cannot be fully accounted for with observed variables alone. Careful consideration of the underlying assumptions, sensitivity analyses, and potential biases introduced by MNAR are essential when dealing with missing data under this mechanism.

Understanding the specific missing data mechanism (MCAR, MAR, MNAR) is crucial for selecting appropriate handling methods and interpreting the results accurately in statistical analyses.

# Handling Missing Values in Dataset

You can get the code here - [Handling missing value source code](https://github.com/dotslashbit/blog_notebooks/tree/main/data_preprocessing)

## Loading the Titanic Dataset

Let's begin by loading the [Titanic dataset](https://www.kaggle.com/competitions/titanic/overview), which contains information about the passengers aboard the Titanic. We will use the pandas library to read the dataset.

```python
import pandas as pd

# Load the Titanic dataset
data = pd.read_csv('titanic.csv')
```

## Check for missing values

Before handling missing values, we first need to know how which columns have how many missing values.

```python
# Check for missing values
missing_values = data.isnull().sum()
```

## Understanding the Missing Data

To effectively handle missing values, we need to understand the patterns and extent of missing data in our dataset. This understanding will help us decide on the most appropriate imputation method.

1. Age Column:
    
    * Type of Missingness: The missingness in the Age column can be considered as Missing Completely at Random (MCAR) because there is no specific pattern or dependency observed between the missingness and the available data or any other variables.
        
    * Possible Reasons: The missingness in the Age column could be due to various reasons such as incomplete record-keeping, data entry errors, or individuals choosing not to disclose their age.
        
2. Embarked Column:
    
    * Type of Missingness: The missingness in the Embarked column can be considered as Missing Completely at Random (MCAR) as there doesn't appear to be any discernible pattern or relationship between the missingness and other variables.
        
    * Possible Reasons: The missingness in the Embarked column could be due to data recording issues, errors, or missing information during the collection process.
        
3. Cabin Column:
    
    * Type of Missingness: The missingness in the Cabin column can be considered as Missing Not at Random (MNAR) because there appears to be a pattern or dependency between the missingness and other variables. Specifically, the missingness is related to whether or not a passenger's cabin information was recorded.
        
    * Possible Reasons: The missingness in the Cabin column could be due to several factors. Passengers who did not have a cabin assigned (e.g., crew members or individuals with lower-class accommodations) may have missing cabin information. Additionally, the missingness could be due to incomplete records or the absence of available information for certain passengers.
        

**Hey, just a heads up** that these ideas about why cabin info might be missing are just based on what we can see in the data and some guesses about how it was collected. Keep in mind that we might not know the real reasons for the missing info just by looking at the dataset.

## Handling Missing Data using Pandas

Pandas provides various methods to handle missing data. Let's explore a few of them:

### Dropping Missing Values

If the missing data is minimal and doesn't significantly affect the dataset's integrity, we can choose to drop the rows or columns with missing values using the `dropna()` function.

```python
# Drop rows with missing values
data_cleaned = data.dropna()
```

### Filling Missing Values

In cases where dropping missing values is not a suitable option, we can fill the missing values using different techniques.

#### Filling with Mean/Median

To fill missing numerical values, we can use the mean or median of the available data.

```python
# let's make a copy of the original data and then do our experiments
data_1 = data.copy()

# Fill missing age values with the median
data_1['Age'].fillna(data['Age'].median(), inplace=True)
data_1.isnull().sum()
```

#### Filling with Mode

For categorical variables, filling missing values with the mode (most frequent value) is a common approach.

```python
# Fill missing embarked values with the mode
data_1['Embarked'].fillna(data['Embarked'].mode()[0], inplace=True)
data_1.isnull().sum()
```

#### Random Sample Imputation

This technique involves randomly selecting values from the available observations and using them to fill in the missing values. It preserves the statistical properties of the original dataset.

```python
#let's make another copy of the original data
data_2 = data.copy()

# Randomly select values to fill missing age values
random_sample = data_2['Age'].dropna().sample(data_2['Age'].isnull().sum(), random_state=0)
data_2.loc[data_2['Age'].isnull(), 'Age'] = random_sample.values

data_2.isnull().sum()
```

## Handling Missing Data using Imputation in scikit-learn

Scikit-learn provides several imputation techniques to handle missing data. Let's explore some of the commonly used methods:

### Simple Imputer

The SimpleImputer class provides basic strategies for imputing missing values. We can use mean, median, mode, or a constant value to replace missing values.

```python
data_si = data.copy()

from sklearn.impute import SimpleImputer

# Create an instance of SimpleImputer with strategy='mean'
imputer = SimpleImputer(strategy='mean')

# Impute missing age values using the mean
imputed_data = imputer.fit_transform(data_si[['Age']])

data_si["Age"] = imputed_data
```

### KNN Imputer

The KNNImputer class imputes missing values by utilizing the k-nearest neighbors approach. It estimates missing values based on the values of k closest neighbors.

```python
data_knn = data.copy()

from sklearn.impute import KNNImputer

# Create an instance of KNNImputer with k=5 (default value)
imputer = KNNImputer()

# Impute missing age values using the KNNImputer
imputed_data = imputer.fit_transform(data_knn[['Age']])

data_knn["Age"] = imputed_data
```

The KNNImputer replaces missing values by calculating the average or weighted average of the nearest neighbors' values. It is particularly useful when the missing values exhibit some degree of similarity with other data points in the dataset.

## Evaluating the Imputation Results

After applying the imputation techniques, it is crucial to assess the quality of the imputed data. You can inspect the imputed values and compare them with the original missing values to ensure the imputation process was successful.

# When Should I Use Which Type of Imputation

The choice of imputation technique depends on the nature of the missing data, the dataset's characteristics, and the specific requirements of your analysis or model. Here's a guide to help you decide which type of imputation to use in different scenarios:

1. Mean/Median/Mode Imputation:
    
    * Use when:
        
        * Missing data is missing completely at random (MCAR) or missing at random (MAR).
            
        * The missing values are in numerical or categorical variables.
            
    * Advantages:
        
        * Simple to implement.
            
        * Preserves the variable's distribution (mean or mode).
            
    * Considerations:
        
        * May underestimate the variance of the variable.
            
        * May introduce bias if the missing data is not MCAR or MAR.
            
2. Random Sample Imputer:
    
    * Use when:
        
        * Missing data is missing completely at random (MCAR).
            
        * The missing values are in numerical or categorical variables.
            
    * Advantages:
        
        * Preserves the variable's distribution.
            
        * Avoids introducing systematic biases.
            
    * Considerations:
        
        * Randomness in the imputation process can lead to different results in each run.
            
        * May introduce some noise into the dataset.
            
3. KNN Imputer:
    
    * Use when:
        
        * Missing data has a pattern or is not missing completely at random (not MCAR).
            
        * There are numerical variables with similar patterns or clusters.
            
    * Advantages:
        
        * Utilizes the similarity between observations to impute missing values.
            
        * Preserves relationships between variables.
            
    * Considerations:
        
        * The performance of KNN imputation depends on the chosen k value.
            
        * Can be computationally expensive for large datasets.
            

# Conclusion

Missing data is a common challenge in data analysis, and handling it properly is crucial for accurate and reliable results. In this blog post, we explored how to handle missing data using pandas and various imputation techniques in scikit-learn. By utilizing these methods, we can effectively deal with missing values in the Titanic dataset or any other dataset. Remember to choose the most appropriate method based on the nature and context of your data. Handling missing data properly empowers us to draw meaningful insights and build reliable models from incomplete datasets.