---
title: "Describing the Titanic—Mean, Median, and Mode"
slug: titanic-mean-median-mode
---

Now let's go get that Titanic data and see if we can use Mean, Median, and Mode to describe what was going on on the Titanic and start to ask and answer some questions.

# Exploring, Asking Questions, Gaining Insights

We are going to do some **Exploratory Data Analysis** (EDA), and as we go along, we're going to gain some familiarity with statistical identities and formulas to better understand what was happening on the Titanic.

That means we are exploring datasets through asking and answering questions about the data. Here are some questions we might ask about passengers on the Titanic:

* Which gender had a better chance of survival?
* Which social class had a better chance of survival?
* Which age group had a better chance of survival?

# Getting Started: Mean Median and Mode

To start honing in on providing confident answers to questions like those, we first have to get a general sense of who was aboard the Titanic.

We can use the mean, median, and mode functions to gain some **insights** about people's age aboard the Titanic. Use yor methods first and then verify them with the Pandas mean, median, and mode functions.

```py
df.mean('Age')
df.median('Age')
df.mode('Age')
```

> [action]
> **What was the mean, median, and mode of people's Fare?**
>
> Calculate these on your own

# Drawing the Histogram

Let's also look at the histogram of Age and Fare to rapidly graph the distribution of these features.

```py
df.hist(column="Age")
```

```py
df.hist(column="Fare")
```

# Conclusions

Just from these two simple calculations: mean, median, mode, and histogram, what can you concluded from the data? What sorts of statements can you confidently say about the Titanic and the people aboard? Were most people old or young? Was it a ship full of children or the elderly?

# Stop for a Second

Just take breather and look how far you've come! Seriously.

You might have already known what mean, median, and mode were from high school math, but could you have downloaded an official data science dataset and in five lines of python computed these three statistical foundational descriptors?

You've opened up pandora's box! How far will you take this new superpower you have?

# Other Questions (Required Challenges)

Now try solving some other questions that goes a bit outside of Mean Median and Mode:

1. Who was the oldest passenger aboard the ship? (Hint, `.max(column)`)
1. How much did the cheapest ticket cost? (Hint, `.min(column)`)
1. What was the range of ticket prices? (Hint max - min)
