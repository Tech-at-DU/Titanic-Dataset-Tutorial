---
title: "PDFs—Probability Density Function"
slug: pdfs
---

https://towardsdatascience.com/histograms-and-density-plots-in-python-f6bda88f5ac0
https://stats.stackexchange.com/questions/48109/what-does-the-y-axis-in-a-kernel-density-plot-mean

Descriptive Statistics

Predictive Statistics

# Explaining PDFs

First watch one of these primers in PDFs and CDFs.

![ms-video-youtube](https://www.youtube.com/watch?v=YXLVjCKVP7U)
![ms-video-youtube](https://www.youtube.com/watch?v=PYIjkw0HN1Q)

First let's review the difference between discrete and continuous random variables:

* **Discrete**: takes on a finite or countable number of values.
* **Continuous**: takes on an infinite number of values

Because continuous random variables can take on an infinite number of values, we can't say with certainty what value the variable will be at any point, so we have to instead provide an interval, or range of values that the variable could be.

### For Example: New York City Snow

For example, what's the probability that New York City get's 4 inches of snow on December 17th? 3.99999 and 4.0001 inches don't count, it has to be exactly 4. It would be impossible to say with exact certainty given there are infinite decimals! However, if instead of looking for exactly 4, we looked at the range of values between 3.9 and 4.1, we could compute the probability for that range! This is where PDFs come in to help us calculate this!


### Not a Histogram

When we graph a PDF, it has a similar pattern to a histogram. The main difference is that instead of the y-axis corresponding to values, it shows the percent probability of the x-axis values. This is known as normalizing the values.

A PDF gives us the ability to say things like

```

```


# Our First PDF

```py
import numpy as np
import pandas as pd

df = pd.read_csv('titanic.csv')
```

First let's look at the age in histogram form:

```py
import seaborn as sns
# create a list of Age values not including N/A values
ls_age = df['Age'].dropna()
# Now plot the data in this list into a histogram!
sns.distplot(ls_age, hist=True, kde=False, bins=16)
```

Now lets look at it with the PDF:

```py
import seaborn as sns
# Notice only the KDE parameter is different!
# What does kde stand for? https://seaborn.pydata.org/generated/seaborn.distplot.html
sns.distplot(df['Age'].dropna(), hist=True, kde=True, bins=16)
```

**Notice that the y-axes are different between the two!** The histogram is the value at an interval of the x-axis, and the PDF y-axis is the probability of being that value.



# Graphing PDFs
