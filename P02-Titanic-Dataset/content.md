---
title: "Describing the Titanic—Mean, Median, and Mode"
slug: titanic-mean-median-mode
---

Now let's go get that Titanic data and see if we can use Mean, Median, and Mode to describe what was going on on the Titanic and start to ask and answer some questions.

# Getting the Titanic Dataset

Head over to the [Kaggle Titanic Competition](https://www.kaggle.com/c/titanic/data) webpage and on the "Data" tab click "Download" to get the csv of Titanic data.

Next, in your Jupyter Notebook, click the "Upload" button and find  the file `titanic/train.csv` and upload it into your Jupyter Notebook. Rename it 'titanic.csv'.

Remember to change the name of your notebook to be "Titanic-Description" because we're focusing on describing the Titanic data using mean, median, mode, range, and variance.

Because the Titanic data is a table, and not a simple array, we are going to use the Pandas python library which affords us similar methods as NumPy but is built to handle more complex data sets that have multiple labeled columns.

Let's load the Titanic data into a Pandas DataFrame object by using the Pandas `.read_csv()` method. Then we'll call the `.head()` function to review that the data is loading properly.

```py
df = pd.read_csv('titanic.csv')
df.head()
```

# Features and the Data Dictionary

Columns in a table of data like this are called "Features" in data science.

There are many features here, but what do they mean? What is `sibsp`? Or `parch`? To know this you have to look at the data dictionary. This dataset has a clear data dictionary on [its page in kaggle.com](https://www.kaggle.com/c/titanic/data).

Review the meaning of each feature.

Scroll through the data and look at it all. What do you notice? What questions or hypothesis are coming up for you that you want tests or prove?

# Asking Questions

Data analysis and data science are all about exploring datasets through asking and answering questions about the data. Here are some questions we might ask about passengers on the Titanic:

**What is the mean, median, and mode of people's Age?**

```py
df.mean('Age')
df.median('Age')
df.mode('Age')
```

**What was the mean, median, and mode of people's Fare?**

Can you calculate these on your own?

# Stop for a Second

Just take breather and look how far you've come! Seriously.

You might have already known what mean, median, and mode were from high school math, but could you have downloaded an official data science dataset and in five lines of python computed these three statistical foundational descriptors?

You've opened up pandora's box! How far will you take this new superpower you have?

# Other Questions (Required Challenges)

Now try solving some other questions that goes a bit outside of Mean Median and Mode:

1. Who was the oldest passenger aboard the ship? (Hint, `.max(column)`)
1. How much did the cheapest ticket cost? (Hint, `.min(column)`)
1. What was the range of ticket prices? (Hint max - min)
