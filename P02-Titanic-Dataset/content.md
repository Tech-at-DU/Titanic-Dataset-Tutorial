---
title: "Describing the Titanic—Mean, Median, and Mode"
slug: titanic-mean-median-mode
---

Now let's go get that Titanic data and see if we can use Mean, Median, and Mode to describe what was going on on the Titanic and start to ask and answer some questions.

# Asking Questions

Data analysis and data science are all about exploring datasets through asking and answering questions about the data. Here are some questions we might ask about passengers on the Titanic:

**What is the mean, median, and mode of people's Age?**

Try using your mean, median, and mode function and then verify them with the Pandas mean, median, and mode functions.

```py
df.mean('Age')
df.median('Age')
df.mode('Age')
```

> [action]
> **What was the mean, median, and mode of people's Fare?**
>
> Can you calculate these on your own?

# Drawing the Histogram

Let's also look at the histogram of Age and Fare to rapidly graph the distribution of these features.

```py
df.hist(column="Age")
```

```py
df.hist(column="Fare")
```

# Conclusions

Just from these two simple calculations: mean, median, mode, and histogram, what can you concluded from the data? What sorts of statements can you confidently say about the Titanic and the people aboard?

# Stop for a Second

Just take breather and look how far you've come! Seriously.

You might have already known what mean, median, and mode were from high school math, but could you have downloaded an official data science dataset and in five lines of python computed these three statistical foundational descriptors?

You've opened up pandora's box! How far will you take this new superpower you have?

# Other Questions (Required Challenges)

Now try solving some other questions that goes a bit outside of Mean Median and Mode:

1. Who was the oldest passenger aboard the ship? (Hint, `.max(column)`)
1. How much did the cheapest ticket cost? (Hint, `.min(column)`)
1. What was the range of ticket prices? (Hint max - min)
