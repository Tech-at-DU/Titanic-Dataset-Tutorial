---
title: "Correlation on the Titanic"
slug: correlation
---

Do not fall into the trap of mistaking correlation for causation. The rain falls, the plants grow, thats causation because there is a causal link between the water of the rain and the plants growing. On the other hand, did you know that the rates of violent crime and murder have been known to jump when ice cream sales do?

Reference [HowStuffWorks—10 Correlations That Are Not Causations](https://science.howstuffworks.com/innovation/science-questions/10-correlations-that-are-not-causations.htm)

In this chapter we're going to use Python statistical libraries to begin to measure the correlation between various features in a dataset.

# Covariance vs. Correlation

Both of these words mean that two variables are dependent on each other, but they are subtly different:

"In simple words, both the terms measure the relationship and the dependency between two variables. “Covariance” indicates the direction of the linear relationship between variables. “Correlation” on the other hand measures both the strength and direction of the linear relationship between two variables." [Towards Data Science Article](https://towardsdatascience.com/let-us-understand-the-correlation-matrix-and-covariance-matrix-d42e6b643c22)

# Getting the Titanic Data Set

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
