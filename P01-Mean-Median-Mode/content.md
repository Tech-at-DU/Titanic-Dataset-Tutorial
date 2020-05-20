---
title: "Mean, Median, Mode, Range"
slug: mean-median-mode
---

So now we have our Jupyter Notebook setup. Let's do some simple permutations of data: mean (average), median, mode, and range.

# Intro to Mean, Median, and Mode

If you are not already familiar, begin by reviewing what the mean, median, and mode are.

![ms-video-youtube](https://www.youtube.com/watch?v=h8EYEJ32oQ8&feature=youtu.be)

For more videos on these concepts, continue on [Khan Academy](https://www.khanacademy.org/math/ap-statistics/summarizing-quantitative-data-ap/measuring-center-quantitative/v/statistics-intro-mean-median-and-mode)

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
    # loop over the listand add up all total
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

# A Bigger Dataset

Let's use our little function to take a bigger average.

1. Go to the US Census website [Educational Attainment page](https://www.census.gov/data/tables/2019/demo/educational-attainment/cps-detailed-tables.html)
2. Click on "Both Sexes" and download that spreadsheet
3. Look at the row labeled "Total"
4. Write a function that finds out the average educational attainment of an American in 2019

This last step is a bit of a leap so let's break it down.

1. Let's assign a coefficient to each level of attainment (1,2,3,4, etc)
1. Make a new list where each element is the number of people who achieved that level of education times the level coefficient.
1. Then take the average of that new list.
1. Then divide that average by the total people
1. We should, in the end have a coefficient number that stands for the average level of educational attainment.


```py

data = np.array([8603,	13372,	62259,	34690,	22738,	49937,	22214,	3136,	4529])

def mean_edu_attainment(dataset, total):
  # create list weighted to index of position
  weighted_list = []

  for n, i in dataset:
    weighted_list.push(n*i)

  mean = compute_mean(weighted_list)

  # calculate total
  total = 0
  for n in dataset
    total += n

  mean_attainment = mean/total

  return mean_attainment

mean_edu_attainment(data, total)

```

# Median (Middle Element)


# Median Educational Attainment

Using our new median function, let's calculate the median educational attainment.




# Mode (Most Frequent)


# Range & Variance
