---
title: "Women and Children First—Probability Aboard the Titanic"
slug: probability
---

Let's dig into the survival rate on the Titanic and what features most influenced a passengers chances of survival. We'll move beyond correlation to derive the actual probabilities of various features.

Open up a new Jupyter Notebook called "Titanic Probability" and add your standard libraries and define your pandas DataFrame using the `titanic.csv`.

# Child Survival Rate

Was it really women and children first on the Titanic?

We have to "dig in" to the data. Correlation is not giving us a clear answer about if children were more likely to survive the sinking of the Titanic. We see there was a pretty weak correlation between being older and dying. What if we want to find out if any children died?

Now we'll have to actually do a bit of query on our dataframe.

Looking back at our awesome [Pandas Cheat Sheet](https://www.dataquest.io/blog/pandas-cheat-sheet/) we can find how to query for just the youths and children.

```py
children = df[df['Age'] < 16]
children.shape
```

We can call `.hist()` to see histograms of each feature:

```py
children.hist()
```

We can see from that that some children did die. Let's get the living and dead children into two dataframes.

```py
living_children = df[(df['Age'] < 16) & (df['Survived'] == 1)]
living_children.hist()
```

```py
dead_children = df[(df['Age'] < 16) & (df['Survived'] == 0)]
dead_children
```

Do you see anything that could answer our question about women and children?

Does calling the `.hist()` method help see any more?

```py
living_children.hist()

dead_children.hist()
```

# Women and Children vs. Grown Men

Another way to answer this question would be to look at the likelihood of two separate populations of survival.

```py
women_and_children = df[(df['Sex'] == "female") or (df['Age'] < 16)]
w_a_c_survival_rate = women_and_children['Survived'].value_counts(normalize=True) * 100
w_a_c_survival_rate
```

```py
adult_men = df[(df['Sex'].str.match('male')) & (df['Age'] > 16)]
a_m_survival_rate = adult_men['Survived'].value_counts(normalize=True) * 100
a_m_survival_rate
```

From these two we can see that adult men had an 17% chance of survival, and women and children had a 71% chance of survival. In English we would say:

```
Women and children had a more than 4x better chance of survival than men.
```

Because 71% is about 4x 17%.

But we saw that correlation between survival and sex was high, but not so high for age. What if we looked at the chance of survival of grown men, grown women, and children of both sexes?

# Conditional Probability and Percentage

Let's ask some simple probability questions:

1. What was the probability of survival for a child? P(Survived=true | Age<16)
1. What was the probability of survival for a woman? P(Survived= true | Sex=female)
1. What was the probability of survival for a man? P(Survived= true | Sex=male)

For these straightforward probabilities, we can simply take the percentage of the group who survived.

We'll use the first element of the `.shape` method to extract the number of rows in each the DataFrame. (`.shape` returns two integers in an array—the first is the row count, the second is the column count of a DataFrame.)

All we have to do is divide the number of surviving children by the total number of children to get the percentage chance of survival for children.

```py
children = df[df['Age'] < 16]
surviving_children = df[(df['Age'] < 16) & (df['Survived'] == 1)]
child_chance_of_survival = surviving_children.shape[0] / children.shape[0]
format(child_chance_of_survival, ".0%")
```

We use Python's built-in `format()` function to return a nice clean percentage rounded to the ones column.

Let's do the same for women. (Remember that Sex has returned to a string column in this new notebook.)

```py
women = df[(df['Sex'] == 'female') & (df['Age'] > 16)]
surviving_women = df[(df['Sex'] == 'female') & (df['Age'] > 16) & (df['Survived'] == 1)]
women_chance_of_survival = surviving_women.shape[0] / women.shape[0]
format(women_chance_of_survival, ".0%")
```

Now calculate it for grown men on your own.

Now let's graph them:

```py
import matplotlib.pyplot as plt

fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
x_axis = ["Children", "Women", "Men"]
data = [child_chance_of_survival, women_chance_of_survival, men_chance_of_survival]
ax.bar(x_axis, data)
plt.show()
```

What can you conclude?

# Multiple Factors: Class

So grown women had the best chance of surviving, and children also had a strong chance. Men, however, did not. From this data we could say a definitive insight such as:

```
Less than 1 in 5 men on the Titanic survived.

Almost 4 in 5 women on the Titanic survived.
```

Couldn't we also say:

```
Women had almost 4x the survival rate of men
```

This last statement is relative and therefore far more deceptive than the first two which are absolute. Because if women's survival rate was 4x that of men that could mean either:

```
.01% - men survival rate
.04% - women survival rate
```

or

```
20% - men survival rate
80% - women survival rate
```

But is being a child or a woman or man the most definitive factor in someone's survival aboard the Titanic. If we had a map of the Titanic and available life boats, we might be able to see if each passengers' cabin's proximity to a lifeboat was the determing factor. We do have another factor that might hypothetically contribute to surival: class.

We have the fare price and ticket class of each passenger. So we could ask a question:

```
Which was more important to survival aboard the Titanic? Your class, your being a child, or your sex?
```

or, using statistical jargon:

```
What is the conditional probability that a person survives given their sex and passenger-class?

P(S= true | G=female,C=1)
P(S= true | G=female,C=2)
P(S= true | G=female,C=3)
P(S= true | G=male,C=1)
P(S= true | G=male,C=2)
P(S= true | G=male,C=3)
```

# The Men Who Lived

Of the men who lived, what were they like?

```py
surviving_men = df[(df['Sex'] == "male") & (df['Age'] > 16) & (df['Survived'] == 1)]
surviving_men.describe()
```

```py
dead_men = df[(df['Sex'] == "male") & (df['Age'] > 16) & (df['Survived'] == 0)]
dead_men.describe()
```

If we compare various attributes of all adult men aboard we might find some insights

```py
dead_men.describe()
```

From this we can see that the average fare for survivors was about double 46.73/22.56 (survived/dead), and their average class was 1.8/2.4 (survived/dead).

If we take the median fare and class of each the difference becomes even more stark and obvious. The median survivor's fare was 261% higher fare than the median of the dead men. The median class of the deaths was 3rd class (the lowest) and the median class of the surviving men was 1st class (the highest).

# First vs. Third Class Men

So perhaps the clearest way to express this insight is to say the percent chance of dying for a 1st class and a 3rd class man? We can use the `.value_counts(normalize=True) * 100` method to output a percentage as well.

```py
third_class_adult_men = df[(df['Sex'] == "male") & (df['Age'] > 16) & (df['Pclass'] == 3)]
thrird_class_adult_men_survival_rate = third_class_adult_men['Survived'].value_counts(normalize=True) * 100
thrird_class_adult_men_survival_rate
```

```py
first_class_adult_men = df[(df['Sex'] == "male") & (df['Age'] > 16) & (df['Pclass'] == 1)]
first_class_adult_men_survival_rate = first_class_adult_men['Survived'].value_counts(normalize=True) * 100
first_class_adult_men_survival_rate
```

Thrid class men had a 12% chance of survival, and first class men had a 37% chance of survival. From these we can say:

```
An adult man in first class on the Titanic had 3x better chance of survival than an adult man in third class
```

# The Dead

By looking at the histograms of who died on the Titanic, it is abundantly clear that working class men (especially 18-35 year old men) gave up their lives so that the women and children could survive.

```py
the_dead = df[df["Survived"] == 0]
the_dead.hist()
```

Who says dead men tell no tales?

# What About Women and Men By Class

Lets generate a similar comparison between first class women and third class women?

We can quickly graph the chance of survival of women by class using seaborn:

```py
sn.barplot(x='Pclass', y='Survived', data=women)
```

It looks like wealthy women had an almost 100% survival rate.

What about men? We can add them as a side-by-side barplot in seaborn using the `hue="" attribute and setting the `data` attribute to the whole dataframe.

```py
sn.barplot(x='Pclass', y='Survived', hue="Sex", data=df)
```

3rd class women had a 30% higher survival rate than 1st class men.

We can also look at this the other way around, see each sex by class:

```py
sn.barplot(x='Sex', y='Survived', hue="Pclass", data=df)
```

First and second class women survived at much higher rates on the Titanic. Perhaps we can hypothesize that a sense of "Chivalry" was alive and well in those times. Maybe if we read some first hand accounts of survivors we could confirm this hypothesis.

# Summing Up

Can you say which factor is the most important?

Do you need to do more calculations to see it clearly?
