---
title: "Titanic Mean, Median, and Mode"
slug: titanic-mean-median-mode
---

Now let's

# Getting the Titanic Dataset

Head over to the [Kaggle Titanic Competition](https://www.kaggle.com/c/titanic/data) webpage and on the "Data" tab click "Download" to get the csv of Titanic data.

Next, in your Jupyter Notebook, click the "Upload" button and find  the file `titanic/train.csv` and upload it into your Jupyter Notebook. Rename it 'titanic.csv'

Because the Titanic data is a table, and not a simple array, we are going to use the Pandas python library which affords us similar methods as NumPy but is built to handle more complex data sets that have multiple labeled columns.

Let's load the Titanic data into a Pandas DataFrame object by using the Pandas `.read_csv()` method. Then we'll call the `.head()` function to review that the data is loading properly.

```py
df = pd.read_csv('titanic.csv')
df.head()
```

# Asking Questions

Data analysis and data science are all about exploring datasets through asking and answering questions about the data. Here are some questions we might ask about passengers on the Titanic:

**What is the mean, median, and mode of people's Age?**

```py
df.mean('Age')
df.median('Age')
df.mode('Age')
```

**What was the mean, median, and mode of people's fare?**

Can you calculate this one on your own?

# Stop for a Second

Just take breather and look how far you've come! Seriously.

You might have already known what mean, median, and mode were from high school math, but could you have downloaded an official data science dataset and in five lines of python computed these three statistical foundational descriptors?

You've opened up pandora's box! How far will you take this new superpower you have?

# Other Questions (Required Challenges)

Now try solving some other questions that goes a bit outside of Mean Median and Mode:

1. Who was the oldest passenger aboard the ship? (Hint, `.max(column)`)
1. How much did the cheapest ticket cost? (Hint, `.min(column)`)
1. What was the range of ticket prices? (Hint max - min)
