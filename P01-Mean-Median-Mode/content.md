---
title: "Describing the Titanic—Mean, Median, and Mode"
slug: mean-median-mode
---

So now we have our Jupyter Notebook setup. Let's begin by doing some **Descriptive Statistics** where we just get our bearings about the rough shape and dimensions of the data we are looking at. We will start by computing a few key measurements: mean (average), median, and mode.

We'll first look at these concepts with simple array examples, then we will put them to use to describe some features of the Titanic Dataset.

# Intro to Mean, Median, Mode

If you are not already familiar, begin by reviewing what the mean, median, and mode are.

![ms-video-youtube](https://www.youtube.com/watch?v=h8EYEJ32oQ8)

> [info]
> For more videos on these concepts, continue on [Khan Academy](https://www.khanacademy.org/math/ap-statistics/summarizing-quantitative-data-ap/measuring-center-quantitative/v/statistics-intro-mean-median-and-mode)

# New Notebook

Make a folder called `ql-notebooks` and inside run `$ juypter notebook`.

Inside that folder make a new notebook called "mean-media-mode".

# Our Basic Libraries

We're using Python 3+ as our language, but we also need some of the amazing Python packages

- **NumPy** is a library for advanced mathematical computation
- **Pandas** is a library for handling and manipulating tables of data
- **MatPlotLib** is a library for basic data visualization

Make a new cell in your Jupyter Notebook and lets add these three basic libraries we'll be using.

```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

Now we have those libraries loaded up to use to read, manipulate, and even visualize data!

# Mean (Average)

In the same cell as you loaded the libraries, let's add a simple dataset. For now we are just going to use a single Python list of decimal numbers (called "floats" in Python).

```py
data = np.array([1, 3, 5, 2, 3, 7, 8, 4, 10, 0, 6, 7, 3, 0, 3, 0, 5, 7, 10, 1, 4, 9, 3])
```

How do we get the average of these numbers?

Let's write a function called `compute_mean`

```py
def compute_mean(dataset):
    """ Main function that calculates the average value across our data. """
    return

compute_mean(data)
```

Now let's put the psuedocode for the evaluative statements of this function stub.

```py
data = np.array([1, 3, 5, 2, 3, 7, 8, 4, 10, 0, 6, 7, 3, 0, 3, 0, 5, 7, 10, 1, 4, 9, 3])

def compute_mean(dataset):
    # make a sum variable
    # loop over the list and add up all total
    # divide the total by the length of the list
    # return the mean
    return

compute_mean(data)
```

Now let's fill in code under each psuedocoded statement


```py
data = np.array([1, 3, 5, 2, 3, 7, 8, 4, 10, 0, 6, 7, 3, 0, 3, 0, 5, 7, 10, 1, 4, 9, 3])

def compute_mean(dataset):
    # make a sum variable
    sum = 0

    # loop over the listand add up all total
    for t in dataset:
        sum = sum + t

    # divide the total by the length of the list
    mean = sum / len(dataset)

    # return the mean
    return mean

compute_mean(data)
```

Now we have a nice little function to compute the average of a dataset.

# Using NumPy

Now that we wrote our own `compute_mean()` function, let's just use NumPy's function for the same thing.

```py
np.mean(data)
```

Go and review numpy's [documentation](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mean.html) on their `.mean()` function.

Always remember that the statistical libraries you are using are very powerful and often can help you solve problems very quickly if you review their documentation or google.


# Median (Middle Element)

Next we want to get the median or middle-th element of the dataset.

We could do this ourselves:

```py

def compute_median(dataset):
    # check if the dataset is even or odd
    if dataset % 2 != 0
      # if odd, subtract the length by 1, divide in half, and then take the next element
      median_index = (len(dataset) - 1)/2 + 1
      median = dataset[median_index]
    else
      # otherwise, divide the dataset in half and take the mean of the two middling elements
      left_index = len(dataset)/2 + 1
      right_index = len(dataset)/2 - 1
      median = (dataset(left_index) + dataset(right_index))/2
    return median

```

As we'll see over and over again, our libraries can help us out! Here is NumPy's median function:

```py
# NumPY
np.median(dataset)
```

# Mode (Most Frequent)

Mode is the most common element.

In this case NumPy doesn't have a mode function, so we can import SciPy's `stats` module and use their mode method.

First pip install SciPy

```bash
$ pip3 install scipy
```

Now let's use it:

```py
import scipy.stats as stats

mode = stats.mode(data)
print(mode)
```

# Mean, Median, and Mode in Pandas

You can also use Pandas to get your mean, median, and mode. To use Pandas, we load data into what is called a `DataFrame` object, conventionally denoted by the variable `df`. Notice that DataFrames are not simple arrays, but tables of data with named columns (denoted in the `columns=[]` option). Think of a Pandas DataFrame as an Excel spreadsheet or a SQL table.

Add the following code to your Jupyter Notebook to see how Panda DataFrames can be used to

```py
import pandas as pd

df = pd.DataFrame([[10, 20, 30, 40], [7, 14, 21, 28], [55, 15, 8, 12],
                   [15, 14, 1, 8], [7, 1, 1, 8], [5, 4, 9, 2]],
                  columns=['Apple', 'Orange', 'Banana', 'Pear'],
                  index=['Basket1', 'Basket2', 'Basket3', 'Basket4',
                         'Basket5', 'Basket6'])

print("\n----------- Calculate Mean -----------\n")
print(df.mean())

print("\n----------- Calculate Median -----------\n")
print(df.median())

print("\n----------- Calculate Mode -----------\n")
print(df.mode())
```

Reference: [PythonProgramming.in—Find Mean, Median and Mode of DataFrame in Pandas](https://www.pythonprogramming.in/find-mean-median-and-mode-of-dataframe-in-pandas.html)

# .describe()

Or to simplify use the Pandas `.describe()` method:

```py
df.describe()
```

Use this [Pandas Cheat Sheet](https://www.dataquest.io/blog/pandas-cheat-sheet/) for reference for awsome Pandas Methods.

children = df[df['Age'] < 16]
children.shape
