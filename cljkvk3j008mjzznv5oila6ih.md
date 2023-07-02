---
title: "A Beginner's Guide to Statistics in Machine Learning"
seoTitle: "A Beginner's Guide to Statistics in Machine Learning"
seoDescription: "Code creates random dataset, computes skewness and kurtosis with SciPy, visualizes with Matplotlib histogram, and shows values in title"
datePublished: Sun Jul 02 2023 03:30:39 GMT+0000 (Coordinated Universal Time)
cuid: cljkvk3j008mjzznv5oila6ih
slug: a-beginners-guide-to-statistics-in-machine-learning
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/hpjSkU2UYSU/upload/dd80818cef6659baf9fcf40426f03372.jpeg
tags: statistics, python, data-science, machine-learning, python3

---

# Introduction

## Definition of statistics

Statistics is a branch of mathematics and a scientific discipline that deals with the collection, analysis, interpretation, presentation, and organization of data. It involves the study of data in order to make informed decisions, draw meaningful conclusions, and understand patterns and relationships within the data.

The main objectives of statistics include:

1. Data Collection: Gathering relevant and accurate data through various methods such as surveys, experiments, or observations.
    
2. Data Analysis: Applying mathematical and statistical techniques to analyze and summarize the collected data. This involves using descriptive statistics to describe the main characteristics of the data, and inferential statistics to draw conclusions and make predictions about a larger population based on a sample.
    
3. Data Interpretation: Interpreting the results of data analysis to draw meaningful insights and conclusions. This may involve identifying trends, patterns, or relationships within the data.
    
4. Presentation and Visualization: Presenting the analyzed data in a clear and concise manner using graphs, charts, tables, and other visual tools. Visual representations help in understanding the data more easily and communicating the findings effectively.
    

Statistics is widely used in various fields such as business, economics, social sciences, healthcare, engineering, and research. It provides methods and techniques to analyze and interpret data, make informed decisions, and solve problems based on evidence and empirical observations.

## Importance of statistics in machine learning

Statistics plays a crucial role in machine learning, providing the foundation for several key aspects of the field. Here are some important reasons why statistics is essential in machine learning:

1. Data Preprocessing: Before applying machine learning algorithms to data, it is essential to preprocess and clean the data. Statistics provides techniques for handling missing data, outliers, and dealing with data normalization or standardization. These preprocessing steps are important for improving the quality of data and enhancing the performance of machine learning models.
    
2. Feature Selection and Dimensionality Reduction: Statistics offers methods for selecting relevant features from a dataset and reducing its dimensionality. Feature selection techniques help identify the most informative features, improving model performance and reducing computational complexity. Dimensionality reduction techniques, such as principal component analysis (PCA), transform high-dimensional data into a lower-dimensional space while preserving important information.
    
3. Model Evaluation and Validation: Statistics provides methods for evaluating and validating machine learning models. Techniques like cross-validation, hypothesis testing, and confidence intervals allow researchers to assess the performance of models, determine their statistical significance, and make reliable predictions about their generalization capabilities.
    
4. Statistical Learning Theory: Statistical learning theory forms the theoretical foundation of machine learning algorithms. It provides the mathematical framework for understanding the relationship between data, models, and generalization. Concepts like bias-variance trade-off, overfitting, regularization, and model selection are rooted in statistical principles.
    
5. Estimation and Inference: Statistics helps in estimating unknown parameters and making inferences about population characteristics based on a sample. This is particularly useful in tasks like regression and probabilistic modeling, where statistical techniques are employed to estimate model parameters and quantify uncertainty.
    
6. Experimental Design: Statistics provides methodologies for designing experiments and collecting data in a controlled and structured manner. Experimental design techniques, such as randomized controlled trials, allow researchers to establish causal relationships between variables and make reliable conclusions about the effectiveness of interventions or treatments.
    
7. Probabilistic Modeling: Statistics offers probabilistic modeling techniques that enable machine learning algorithms to reason under uncertainty. Models such as Bayesian networks, hidden Markov models, and Gaussian processes incorporate probabilistic principles, allowing for probabilistic inference, uncertainty quantification, and decision-making in uncertain environments.
    

Overall, statistics provides the essential tools and concepts that enable researchers and practitioners to analyze data, develop models, and make reliable predictions and decisions in machine learning. It helps ensure the robustness, interpretability, and generalization capabilities of machine learning algorithms in real-world applications.

# Types of statistics: Descriptive and Inferential

Statistics can be broadly categorized into two main types: descriptive statistics and inferential statistics. Let's explore each type in more detail:

## Descriptive Statistics

Descriptive statistics involves the methods and techniques used to summarize, organize, and present data in a meaningful way. It focuses on describing the main characteristics of a dataset without making any inferences or generalizations beyond the observed data. Some common descriptive statistics include:

* Measures of central tendency: These statistics provide information about the center or average value of a dataset. Examples include the mean (average), median (middle value), and mode (most frequent value).
    
* Measures of variability: These statistics quantify the spread or dispersion of data points. Examples include the range (difference between the maximum and minimum values), variance, and standard deviation.
    
* Percentiles and quartiles: Percentiles divide a dataset into equal parts based on the relative position of a value. Quartiles are specific percentiles that divide the data into quarters.
    
* Frequency distributions: These summarize the distribution of data by counting the number of occurrences of each value or grouping data into intervals or bins.
    

## Inferential Statistics:

* Inferential statistics involves making inferences and drawing conclusions about a population based on a sample of data. It uses probability theory and statistical methods to generalize from a smaller sample to a larger population. Inferential statistics help in understanding relationships, testing hypotheses, and making predictions. Some common techniques used in inferential statistics include:
    
* Hypothesis testing: This involves formulating and testing hypotheses about population parameters based on sample data. It allows researchers to determine the statistical significance of observed differences or relationships.
    
* Confidence intervals: Confidence intervals provide a range of values within which a population parameter is likely to lie with a certain level of confidence. They help quantify the uncertainty associated with estimates.
    
* Regression analysis: Regression analysis examines the relationship between variables and estimates the impact of one or more independent variables on a dependent variable. It helps in making predictions and understanding the strength and direction of relationships.
    
* Analysis of variance (ANOVA): ANOVA is used to compare means between two or more groups to determine if there are statistically significant differences. It is commonly used in experimental studies with categorical independent variables.
    
* Sampling techniques: Inferential statistics relies on appropriate sampling techniques to ensure representative and unbiased samples. Techniques such as simple random sampling, stratified sampling, and cluster sampling are used to select samples from populations.
    

These two types of statistics work together to provide a comprehensive understanding of data. Descriptive statistics summarize and describe the data, while inferential statistics allow us to draw broader conclusions and make predictions beyond the observed sample.

Now, let's learn about these two types of statistics in more detail.

# Descriptive Statistics

## Measures of central tendency

Measures of central tendency are statistical measures that provide information about the center or average value of a dataset. They help summarize and describe the typical or representative value around which the data points tend to cluster. The three most common measures of central tendency are:

1. **Mean**: The mean, also known as the average, is calculated by summing all the values in a dataset and dividing the sum by the total number of observations. It is influenced by extreme values and provides a measure of the "typical" value. The formula for calculating the mean is:
    
    Mean = (Sum of all values) / (Total number of observations)
    
2. **Median**: The median is the middle value in an ordered dataset when the values are arranged in ascending or descending order. It is not affected by extreme values and is a robust measure of central tendency. If the dataset has an odd number of observations, the median is the middle value. If the dataset has an even number of observations, the median is the average of the two middle values.
    
3. **Mode**: The mode is the value or values that occur most frequently in a dataset. It represents the peak or highest point of the distribution. A dataset can have one mode (unimodal) or multiple modes (bimodal, trimodal, etc.). In some cases, a dataset may not have a mode if no value occurs more than once.
    

These measures of central tendency provide different perspectives on the typical value of a dataset. The mean is commonly used when the data is approximately normally distributed and is sensitive to outliers. The median is useful when dealing with skewed data or when outliers are present. The mode is useful for categorical or discrete data and can be used alongside the mean or median in any type of data.

It's important to consider the characteristics of the dataset and the goals of the analysis when choosing an appropriate measure of central tendency. Each measure has its advantages and limitations, and using multiple measures can provide a more comprehensive understanding of the data.

Below is a python code to visualize mean, median and mode of a randomly generated data.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate a sample dataset
data = np.random.normal(10, 2, 100)  # Generating 100 random numbers from a normal distribution with mean 10 and standard deviation 2

# Calculate mean, median, and mode
mean = np.mean(data)
median = np.median(data)
mode = stats.mode(data).mode[0]  # stats.mode returns an object, so we access the mode value using mode[0]

# Plotting the data
plt.hist(data, bins=20, alpha=0.5, color='steelblue')
plt.axvline(mean, color='r', linestyle='--', label='Mean')
plt.axvline(median, color='g', linestyle='--', label='Median')
plt.axvline(mode, color='b', linestyle='--', label='Mode')
plt.xlabel('Values')
plt.ylabel('Frequency')
plt.title('Histogram with Mean, Median, and Mode')
plt.legend()
plt.show()

# Print the calculated values
print("Mean:", mean)
print("Median:", median)
print("Mode:", mode)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687031148668/01edcffa-2009-4809-b96c-9ddbf6d4cae9.png align="center")

In this code, we generate a sample dataset of 100 random numbers from a normal distribution with a mean of 10 and a standard deviation of 2. Then, we calculate the mean, median, and mode of the dataset using appropriate functions from the `numpy` and `scipy.stats` libraries. Finally, we plot a histogram of the data and overlay vertical lines representing the mean, median, and mode using `matplotlib`.

When you run this code, you will see a histogram with the mean represented by a red dashed line, the median represented by a green dashed line, and the mode represented by a blue dashed line. The calculated values for mean, median, and mode will also be printed.

Note: Make sure you have the necessary Python libraries (`numpy`, `matplotlib`, and `scipy`) installed to run the code successfully.

## Measures of dispersion

Measures of dispersion, also known as measures of variability or spread, provide information about the extent to which data points in a dataset vary from the central tendency. They help quantify the spread, dispersion, or scatter of the data points. Here are some common measures of dispersion:

1. **Range**: The range is the simplest measure of dispersion and represents the difference between the maximum and minimum values in a dataset. It provides a rough estimate of the spread of the data but is sensitive to outliers.
    
2. **Variance**: The variance measures the average squared deviation of each data point from the mean. It gives an indication of how spread out the data is. The formula for variance is:
    
    Variance = (Sum of squared deviations from the mean) / (Total number of observations)
    
    The variance is in squared units of the original data, which makes it less interpretable. To obtain a measure in the original units, you can take the square root of the variance, giving you the standard deviation.
    
3. **Standard** **Deviation**: The standard deviation is the square root of the variance. It measures the average amount by which data points deviate from the mean. The formula for standard deviation is:
    
    Standard Deviation = sqrt(Variance)
    
    The standard deviation is in the same units as the original data, making it more interpretable. It is commonly used due to its intuitive interpretation and its usefulness in statistical calculations.
    
4. **Interquartile** **Range** **(IQR)**: The interquartile range represents the range between the 25th and 75th percentiles of a dataset. It is less affected by extreme values and provides a measure of the spread of the central 50% of the data. To calculate the IQR, you subtract the first quartile (Q1) from the third quartile (Q3).
    
    IQR = Q3 - Q1
    
5. **Coefficient of Variation (CV)**: The coefficient of variation measures the relative variability of a dataset compared to its mean. It is calculated by dividing the standard deviation by the mean and multiplying by 100 to express it as a percentage. The coefficient of variation is useful for comparing the variability of different datasets, especially when the means are different.
    
    CV = (Standard Deviation / Mean) \* 100
    

These measures of dispersion provide insights into the spread and variability of data points. They help assess the heterogeneity of a dataset and understand how much individual values deviate from the central tendency. Depending on the characteristics of the data and the goals of the analysis, different measures of dispersion may be more appropriate to use.

Below is a Python code to calculate and visualize the measures of dispersion: variance, standard deviation, interquartile range (IQR).

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate random data
np.random.seed(42)
data = np.random.normal(loc=0, scale=1, size=1000)

# Calculate variance and standard deviation
variance = np.var(data)
std_dev = np.std(data)

# Create a histogram of the data
plt.hist(data, bins=30, density=True, alpha=0.7, color='skyblue')

# Add labels and title to the plot
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.title('Histogram of Data\nVariance: {:.2f}, Standard Deviation: {:.2f}'.format(variance, std_dev))

# Add a vertical line for mean
mean = np.mean(data)
plt.axvline(x=mean, color='red', linestyle='--', label='Mean')

# Add a legend
plt.legend()

# Show the plot
plt.show()
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688115561992/3449b096-3567-4dc0-9bf9-259017747b85.png align="center")

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate random data
np.random.seed(42)
data = np.random.normal(loc=0, scale=1, size=1000)

# Calculate quartiles and IQR
q1 = np.percentile(data, 25)
q3 = np.percentile(data, 75)
iqr = q3 - q1

# Create a boxplot of the data
plt.boxplot(data)

# Add labels and title to the plot
plt.xlabel('Data')
plt.ylabel('Value')
plt.title('Boxplot of Data\nIQR: {:.2f}'.format(iqr))

# Show the plot
plt.show()
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688115604269/c5043124-b7ee-4f49-a0d9-038ec25edc04.png align="center")

In this code, a random dataset is generated using NumPy's `random.normal()` function. The quartiles and IQR are calculated using NumPy's `percentile()` function with the respective percentile values (25 for Q1 and 75 for Q3). The data is visualized using a boxplot created with Matplotlib's `boxplot()` function. The IQR value is displayed in the plot title.

## Measures of shape

Measures of shape, also known as measures of skewness and kurtosis, provide information about the asymmetry and peakedness of a probability distribution. They help characterize the shape and departure from normality of a dataset. Here are the common measures of shape:

1. **Skewness**: Skewness measures the asymmetry of a distribution. Positive skewness indicates a longer or fatter tail on the right side of the distribution, while negative skewness indicates a longer or fatter tail on the left side of the distribution. A skewness value of 0 indicates a symmetric distribution. There are different formulas to calculate skewness, but one commonly used method is Pearson's first skewness coefficient:
    
    Skewness = (3 \* (Mean - Median)) / Standard Deviation
    
    A positive skewness value indicates right skewness, and a negative value indicates left skewness.
    
2. **Kurtosis**: Kurtosis measures the peakedness or flatness of a distribution compared to a normal distribution. High kurtosis indicates a sharper peak and heavier tails, while low kurtosis indicates a flatter peak and lighter tails. Kurtosis is typically measured relative to the normal distribution, so the excess kurtosis is often used. The formula for excess kurtosis is:
    
    Excess Kurtosis = Kurtosis - 3
    
    A positive excess kurtosis value indicates heavy-tailed distribution with a sharper peak, while a negative value indicates light-tailed distribution with a flatter peak.
    

These measures provide insights into the shape and departure from normality of a distribution. They help identify whether the data is skewed or symmetric, and whether it has heavy or light tails compared to a normal distribution.

Here's an example of Python code to calculate and visualize skewness and kurtosis using the `scipy.stats` module:

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate a sample dataset
data = np.random.normal(10, 2, 1000)  # Generating 1000 random numbers from a normal distribution with mean 10 and standard deviation 2

# Calculate skewness and kurtosis
skewness = stats.skew(data)
kurtosis = stats.kurtosis(data)

# Print the calculated values
print("Skewness:", skewness)
print("Kurtosis:", kurtosis)

# Histogram to visualize the data distribution
plt.hist(data, bins=30, alpha=0.5, color='steelblue')
plt.xlabel('Values')
plt.ylabel('Frequency')
plt.title('Histogram of Data')
plt.show()

# ---------------------- OUTPUT ------------------ #
Skewness: 0.07311155064788019
Kurtosis: -0.13384868950868123
# --------------------- OUTPUT -------------------- #
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687031235991/56dd5a06-8f8e-4870-b5c2-ee014ef6c593.png align="center")

In this code, we generate a sample dataset of 1000 random numbers from a normal distribution with a mean of 10 and a standard deviation of 2. Then, we calculate the skewness and kurtosis using the `scipy.stats` module. Finally, we use `matplotlib` to plot a histogram to visualize the data distribution.

When you run this code, you will see the calculated values for skewness and kurtosis, as well as a histogram representing the data distribution.

Note: Make sure you have the necessary Python libraries (`numpy`, `matplotlib`, and `scipy`) installed to run the code successfully.

# Inferential Statistics

## Sampling and estimation

Sampling and estimation are crucial components of inferential statistics that enable us to draw conclusions about a population based on a sample. Here's an overview of sampling and estimation:

### Sampling

Sampling involves selecting a subset of individuals or items from a larger population for data collection and analysis. The goal is to obtain a representative sample that accurately reflects the characteristics of the population of interest. Different sampling techniques can be employed, depending on the research design and objectives:

1. **Simple Random Sampling**: In this method, each individual in the population has an equal chance of being selected for the sample. It involves randomly selecting individuals without any bias or specific criteria.
    
2. **Stratified Sampling**: This technique involves dividing the population into homogeneous subgroups or strata based on certain characteristics (e.g., age, gender, region) and then randomly selecting samples from each stratum. It ensures representation from each subgroup.
    
3. **Cluster Sampling**: Cluster sampling involves dividing the population into clusters or groups, and then randomly selecting entire clusters to be included in the sample. It is useful when it is difficult or costly to access individuals directly.
    
4. **Systematic Sampling**: In systematic sampling, the sample is selected by choosing every kth element from the population after randomly selecting a starting point. The value of k is determined by the ratio of the population size to the desired sample size.
    

### Estimation

Estimation refers to the process of using sample data to estimate or infer population parameters, such as means, proportions, variances, or regression coefficients. Estimation methods provide point estimates or interval estimates:

1. **Point Estimation**: Point estimation involves calculating a single value (point estimate) to estimate the population parameter of interest. The most common point estimate is the sample mean, which is used to estimate the population mean.
    
2. **Interval Estimation (Confidence Intervals)**: Interval estimation provides a range of values (confidence interval) within which the population parameter is likely to fall with a specified level of confidence. The confidence interval provides a measure of the uncertainty associated with the estimate. Commonly used confidence levels are 90%, 95%, and 99%.
    

The choice of estimation method depends on the type of data, the population parameter being estimated, and the desired level of precision or confidence.

Sampling and estimation are fundamental in inferential statistics as they enable us to make inferences about the population based on limited sample data. Proper sampling techniques and accurate estimation methods are essential for obtaining reliable and valid conclusions about a larger population from a smaller subset.

Below is a Python code to visualize sampling and estimation using a histogram and confidence interval:

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate a population with known distribution
population = np.random.normal(50, 10, 10000)  # Generating a normal distribution with mean 50 and standard deviation 10

# Perform simple random sampling
sample_size = 100  # Size of the sample
sample = np.random.choice(population, size=sample_size, replace=False)

# Calculate sample statistics
sample_mean = np.mean(sample)
sample_std = np.std(sample)

# Calculate confidence interval
confidence_level = 0.95  # Confidence level
z = 1.96  # Z-score for a 95% confidence interval
margin_of_error = z * (sample_std / np.sqrt(sample_size))
confidence_interval = (sample_mean - margin_of_error, sample_mean + margin_of_error)

# Visualize the population, sample, and confidence interval
plt.figure(figsize=(10, 6))

# Population histogram
plt.hist(population, bins=30, alpha=0.5, label='Population', color='skyblue')

# Sample histogram
plt.hist(sample, bins=15, alpha=0.7, label='Sample', color='navy')

# Confidence interval
plt.axvline(confidence_interval[0], color='red', linestyle='--', label='Confidence Interval')
plt.axvline(confidence_interval[1], color='red', linestyle='--')

plt.xlabel('Values')
plt.ylabel('Frequency')
plt.title('Sampling and Confidence Interval Visualization')
plt.legend()
plt.show()

# Print the calculated values
print("Sample Mean:", sample_mean)
print("Sample Standard Deviation:", sample_std)
print("Confidence Interval:", confidence_interval)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687031451753/15de0c2f-4293-4c6c-9991-8a74a86d992c.png align="center")

In this code, we start by generating a population of 10,000 data points from a normal distribution with a mean of 50 and a standard deviation of 10. We then perform simple random sampling to select a sample of size 100 from the population.

Next, we calculate the sample mean and sample standard deviation to estimate the population parameters. We also calculate the confidence interval using the formula `sample_mean ± (z * sample_std / sqrt(sample_size))`, where `z` corresponds to the desired confidence level.

Finally, we use `matplotlib` to create a histogram that visualizes the population distribution and the sample distribution. We also plot vertical lines to indicate the confidence interval.

When you run this code, you will see a histogram showing the population distribution, the sample distribution, and the confidence interval represented by red dashed lines.

Note: Make sure you have the necessary Python libraries (`numpy` and `matplotlib`) installed to run the code successfully.

## Hypothesis testing

Hypothesis testing is a statistical method used to make inferences and draw conclusions about population parameters based on sample data. It involves formulating two competing hypotheses, the null hypothesis (H0) and the alternative hypothesis (H1 or Ha), and evaluating the evidence from the sample to determine whether to accept or reject the null hypothesis.

### Null and alternative hypotheses

In hypothesis testing, the null hypothesis (H0) and the alternative hypothesis (H1 or Ha) are two competing statements about the population parameter being investigated. These hypotheses represent different claims or assumptions, and the goal of hypothesis testing is to evaluate the evidence from the sample data and determine whether to accept or reject the null hypothesis in favor of the alternative hypothesis. Here's an explanation of the null and alternative hypotheses:

**Null Hypothesis (H0)**: The null hypothesis represents the assumption of no effect or no difference in the population. It states that there is no relationship, no effect, or no significant difference between variables. It is often denoted as H0: parameter = value, where the parameter represents the population parameter of interest (e.g., population mean, population proportion) and the value represents a specific value or condition. The null hypothesis is generally considered the default assumption unless there is sufficient evidence to reject it.

**Alternative Hypothesis (H1 or Ha)**: The alternative hypothesis represents the claim or the effect we are trying to find evidence for. It asserts that there is a relationship, an effect, or a significant difference in the population. The alternative hypothesis can be one-sided or two-sided:

1. One-Sided (or One-Tailed) Alternative Hypothesis:
    
    * A one-sided alternative hypothesis specifies the direction of the effect or difference. It asserts that the population parameter is greater than (H1: parameter &gt; value) or less than (H1: parameter &lt; value) the specified value. One-sided alternative hypotheses are used when there is a specific direction of interest or when there is prior knowledge or a theoretical basis for expecting a particular direction of effect.
        
2. Two-Sided (or Two-Tailed) Alternative Hypothesis:
    
    * A two-sided alternative hypothesis does not specify the direction of the effect or difference. It asserts that the population parameter is simply not equal to the specified value. In other words, it allows for the possibility of the parameter being either greater than or less than the value. Two-sided alternative hypotheses are used when there is no specific direction of interest or when we want to test for any difference or effect.
        

The choice between a one-sided or two-sided alternative hypothesis depends on the research question and the specific objectives of the study. It is important to carefully formulate the null and alternative hypotheses to ensure they accurately reflect the research question and cover all possible outcomes.

During hypothesis testing, the evidence from the sample data is used to evaluate the null hypothesis and determine whether to reject it in favor of the alternative hypothesis. The decision to accept or reject the null hypothesis is based on the calculated test statistic, the chosen significance level (α), and the critical region or p-value associated with the test statistic.

## Test statistics

Test statistics are calculated values that are used in hypothesis testing to assess the evidence against the null hypothesis and make decisions about its acceptance or rejection. The test statistic quantifies the discrepancy between the sample data and the null hypothesis, allowing us to determine the likelihood of obtaining such results if the null hypothesis were true.

The choice of the test statistic depends on several factors, including the research question, the type of data, and the specific hypothesis being tested. Here are some commonly used test statistics for different scenarios:

1. Z-Statistic:
    
    * The Z-statistic is used when the population standard deviation is known or when the sample size is large (typically n &gt; 30).
        
    * It is calculated as the difference between the sample mean and the hypothesized population mean, divided by the standard deviation of the population (or standard error of the mean).
        
    * The formula for the Z-statistic is: Z = (x - μ) / (σ / sqrt(n)), where x is the sample mean, μ is the hypothesized population mean, σ is the population standard deviation, and n is the sample size.
        
2. T-Statistic:
    
    * The T-statistic is used when the population standard deviation is unknown and needs to be estimated from the sample or when the sample size is small (typically n &lt; 30).
        
    * It is calculated as the difference between the sample mean and the hypothesized population mean, divided by the standard error of the mean.
        
    * The formula for the T-statistic is: t = (x - μ) / (s / sqrt(n)), where x is the sample mean, μ is the hypothesized population mean, s is the sample standard deviation, and n is the sample size.
        
3. Chi-Square Statistic:
    
    * The Chi-Square statistic is used for testing relationships between categorical variables or comparing observed frequencies with expected frequencies.
        
    * It measures the difference between the observed frequencies and the expected frequencies under the null hypothesis.
        
    * The formula for the Chi-Square statistic depends on the specific test being performed and involves summing the squared differences between observed and expected frequencies.
        
4. F-Statistic:
    
    * The F-statistic is commonly used in analysis of variance (ANOVA) to compare variances between multiple groups or conditions.
        
    * It measures the ratio of the variability between groups to the variability within groups.
        
    * The F-statistic is calculated by dividing the mean square between groups by the mean square within groups.
        

These are just a few examples of test statistics commonly used in hypothesis testing. The appropriate test statistic depends on the specific hypothesis being tested, the type of data, and the underlying assumptions of the statistical test. By comparing the calculated test statistic to critical values or using it to calculate a p-value, we can make decisions about the acceptance or rejection of the null hypothesis.

## P-value

The p-value is a statistical measure used in hypothesis testing that quantifies the strength of the evidence against the null hypothesis. It represents the probability of obtaining a test statistic as extreme as, or more extreme than, the one observed in the sample, assuming that the null hypothesis is true. In other words, the p-value measures the likelihood of observing the data or more extreme data under the null hypothesis.

The interpretation of the p-value depends on the chosen significance level (α), which represents the threshold for accepting or rejecting the null hypothesis. Commonly used significance levels are 0.05 (5%) and 0.01 (1%). The general interpretation guidelines for the p-value are as follows:

* If the p-value is less than the significance level (p-value &lt; α):
    
    * It suggests that the observed data is unlikely to occur if the null hypothesis is true.
        
    * This provides evidence against the null hypothesis, indicating that there is a statistically significant result.
        
    * We reject the null hypothesis in favor of the alternative hypothesis.
        
* If the p-value is greater than or equal to the significance level (p-value ≥ α):
    
    * It suggests that the observed data is likely to occur even if the null hypothesis is true.
        
    * This means that there is insufficient evidence to reject the null hypothesis.
        
    * We fail to reject the null hypothesis, and it does not necessarily imply that the null hypothesis is true.
        

It is important to note that the p-value does not provide information about the magnitude or practical significance of the observed effect. It only measures the strength of the statistical evidence against the null hypothesis. Additionally, the p-value does not provide information about the alternative hypothesis; it focuses on the null hypothesis and the observed data.

The p-value can be calculated based on the chosen test statistic and the distribution associated with it. For example, in a t-test, the p-value is typically obtained by comparing the calculated t-statistic to the t-distribution with appropriate degrees of freedom.

When interpreting the p-value, it is essential to consider the context of the study, the research question, and any prior knowledge or assumptions. The p-value should be used as a tool to aid decision-making in hypothesis testing, but it should not be the sole factor considered. Other factors, such as effect size, sample size, and practical implications, should also be taken into account when drawing conclusions from the data.

## Type I and Type II errors

In hypothesis testing, Type I and Type II errors are two possible errors that can occur when making decisions about the null hypothesis. These errors are related to the acceptance or rejection of the null hypothesis based on the sample data. Let's understand each type of error:

1. Type I Error (False Positive):
    
    * A Type I error occurs when the null hypothesis is incorrectly rejected, even though it is true in the population.
        
    * In other words, it is the error of concluding an effect or difference exists when, in fact, there is no real effect or difference.
        
    * The probability of committing a Type I error is denoted by the significance level (α), which is typically set before conducting the hypothesis test (e.g., α = 0.05 or 5%).
        
    * A lower significance level reduces the likelihood of Type I errors but increases the chance of Type II errors.
        
2. Type II Error (False Negative):
    
    * A Type II error occurs when the null hypothesis is incorrectly accepted, even though it is false in the population.
        
    * It is the error of failing to detect an effect or difference that truly exists.
        
    * The probability of committing a Type II error is denoted by the symbol β (beta).
        
    * Power (1 - β) is the complement of Type II error and represents the probability of correctly rejecting the null hypothesis when it is false.
        
    * The power of a statistical test is influenced by various factors, including sample size, effect size, and chosen significance level.
        

The relationship between Type I and Type II errors is often described using a trade-off. By decreasing the probability of a Type I error (α), the probability of a Type II error (β) typically increases. Conversely, decreasing the probability of a Type II error (β) increases the probability of a Type I error (α). Achieving a balance between these two types of errors depends on the specific situation and the consequences associated with each type of error.

It's worth noting that the specific values of Type I and Type II errors can vary depending on the particular hypothesis test and the assumptions made. The goal in hypothesis testing is to minimize both Type I and Type II errors by carefully selecting appropriate sample sizes, conducting power analyses, and considering the practical implications of the study results.

## Analysis of variance (ANOVA)

ANOVA, or Analysis of Variance, is a statistical technique used to compare means between two or more groups or conditions. It is used to determine if there are significant differences in the means of the groups and to assess the impact of categorical independent variables on a continuous dependent variable.

ANOVA divides the total variability in the data into two components: variation between groups and variation within groups. The basic assumption is that if there are no differences between the group means, then any observed differences are due to random sampling variation.

There are different types of ANOVA, depending on the design and number of independent variables:

1. One-Way ANOVA:
    
    * One-Way ANOVA is used when there is a single categorical independent variable (with two or more levels) and one continuous dependent variable.
        
    * It compares the means of the groups to determine if there are any significant differences among them.
        
2. Two-Way ANOVA:
    
    * Two-Way ANOVA is used when there are two categorical independent variables and one continuous dependent variable.
        
    * It examines the main effects of each independent variable and the interaction effect between them.
        
3. Factorial ANOVA:
    
    * Factorial ANOVA is used when there are two or more independent variables, each with two or more levels.
        
    * It allows for examining the main effects of each independent variable and the interaction effects between them.
        

The ANOVA test produces an F-statistic and calculates the associated p-value to determine if the differences observed between the groups are statistically significant. If the p-value is less than the chosen significance level (typically α = 0.05), it indicates that at least one group mean is significantly different from the others.

In addition to the overall test, ANOVA also provides post-hoc tests (e.g., Tukey's HSD, Bonferroni, Scheffe) to determine which specific group means differ significantly from each other, if the overall test is significant.

ANOVA is widely used in various fields, such as psychology, biology, social sciences, and manufacturing, to compare group means and understand the effects of categorical variables on continuous outcomes. It provides valuable insights into group differences and helps in drawing conclusions about population means based on sample data.

# Conclusion

Statistics is a branch of mathematics and a scientific discipline that deals with the collection, analysis, interpretation, presentation, and organization of data. It is used in various fields such as business, economics, social sciences, healthcare, engineering, and research. It is essential in machine learning, providing techniques for data preprocessing, feature selection, dimensionality reduction, model evaluation and validation, statistical learning theory, and estimation and inference. Descriptive statistics summarize and describe the data, while inferential statistics allow us to draw broader conclusions and make predictions beyond the observed sample. Python code examples are provided to calculate and visualize measures of central tendency, such as mean, median, and mode.