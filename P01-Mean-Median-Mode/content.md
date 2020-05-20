---
title: "Mean, Median, Mode, Range"
slug: mean-median-mode
---

So now we have our Jupyter Notebook setup. Let's do some simple permutations of data: mean (average), median, mode, and range.

# Intro to Mean, Median, and Mode

If you are not already familiar, begin by reviewing what the mean, median, and mode are.

![ms-video-youtube](https://www.youtube.com/watch?v=h8EYEJ32oQ8&feature=youtu.be)

For more videos on these concepts, continue on [Khan Academy](https://www.khanacademy.org/math/ap-statistics/summarizing-quantitative-data-ap/measuring-center-quantitative/v/statistics-intro-mean-median-and-mode)


# New Notebook

Make a folder called "ql-notebooks" and inside boot up an instance of `juypter notebook`.

Inside that folder make a new notebook called "mean-media-mode".

# Our Basic Libraries

We're using Python 3+ as our language, but we also need some of the amazing Python packages

- **Pandas** is a library for basic data analysis
- **NumPy** is a library for advanced mathematical computation
- **MatPlotLib** is a library for basic data visualization

Make a new cell in your Jupyter Notebook and lets add these three basic libraries we'll be using.

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

Now we have those libraries loaded up to use to read, manipulate, and even visualize data!

# Mean (Average)

In the same cell as you loaded the libraries, let's add a simple dataset. For now we are just going to use a single Python list of decimal numbers (called "floats" in Python).

```py
data = np.array([1, 3, 5, 2, 3, 7, 8, 4, 10, 0, 6, 7, 3, 0, 3, 0, 5, 7, 10, 1, 4, 9, 3])
```

How do we get the average of these numbers?

Let's right a function called `compute_mean`

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



    return median

```


As we'll see over and over again, our libraries can help us out! Here is NumPy's median function:

```py
# NumPY
np.median(dataset)
```



# Median Educational Attainment

Using our new median function, let's calculate the median educational attainment.




# Mode (Most Frequent)


# Range & Variance
