---
title: "Variance and Covariance on the Titanic"
slug: variance-and-covariance
---

Now lets start to look at how we can start to describe data and begin to get our bearings so we can start to ask questions and discover insights.

# Variance & Covariance

**Variance** is a measure of how spread out the data is or to put it another way it measures how far a set of numbers is spread out from their average value.

We can use the NumPy function `.var(arr)` to find the variance score of an array. The `.var(arr)` function uses "the average of the squared deviations from the mean"—which in english reads: The average of the square of the absolute difference between each element and the average of the whole dataset.

```
var = mean(abs(x - x.mean())**2)
```

In a Juypter Notebook, use the following code to calculate the variance of two arrays:

```py
low_variance = [7,8,7,8,9,6,7,7,7,8,9,8,7,4]

np.mean(low_variance)
np.var(low_variance)

high_variance = [102,2,50023,30,03040,50,20,1,50,-304,-50349]

np.mean(high_variance)
np.var(high_variance)
```

# Variance in Features in the Titanic Dataset



# Covariance vs. Correlation

Both of these words mean that two variables are dependent on each other, but they are subtly different:

"In simple words, both the terms measure the relationship and the dependency between two variables. “Covariance” indicates the direction of the linear relationship between variables. “Correlation” on the other hand measures both the strength and direction of the linear relationship between two variables." [Towards Data Science Article](https://towardsdatascience.com/let-us-understand-the-correlation-matrix-and-covariance-matrix-d42e6b643c22)

**Covariance** can be used to measure how two variables change or vary together. A positive covariance means the variables are positively related, while a negative covariance means the variables are inversely related.

**Correlation**

# Getting the Titanic Data Set

Let's add some more code to our Titanic Jupyter notebook. We're going to use Pandas and another library called SciPy, which is "a Python-based ecosystem of open-source software for mathematics, science, and engineering. In particular, these are some of the core packages." We'll be adding the `stats` package from SciPy.

```py
import pandas as pd
import scipy.stats

```

Now we want to use a Pandas **DataFrame** using the Pandas and we'll use the conventional variable `df`.

```py
df = pd.read_csv('titanic.csv')
```

Next we need to write a function that will calculate pearson's correlation coefficient.

```py
#here is a function to calculate pearson's correlation coefficient
def pearson_corr(x, y):
    x_mean = np.mean(x)
    y_mean = np.mean(y)
    num = [(i - x_mean)*(j - y_mean) for i,j in zip(x,y)]
    den_1 = [(i - x_mean)**2 for i in x]
    den_2 = [(j - y_mean)**2 for j in y]
    correlation_x_y = np.sum(num)/np.sqrt(np.sum(den_1))/np.sqrt(np.sum(den_2))
    return correlation_x_y

print(pearson_corr(df['Fare'], df['Siblings/Spouses Aboard']))
print(scipy.stats.pearsonr(df['Fare'], df['Siblings/Spouses Aboard']))
```
