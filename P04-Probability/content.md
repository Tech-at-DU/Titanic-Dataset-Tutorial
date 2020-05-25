---
title: "Women and Children First: Probability on the Titanic"
slug: probability
---

Let's dig into the survival rate on the Titanic and what features most influenced a passengers cha

# Conditional Probability and Percentage

1. What was the probability of survival for a child? P(Survived=true | Age<16)
1. What was the probability of survival for a woman? P(Survived= true | Sex=female)
1. What was the probability of survival for a man? P(Survived= true | Sex=male)

For these straightforward probabilities, we can simply take the percentage of the group who survived.

```py
children = df[df['Age'] < 16]
surviving_children = df[(df['Age'] < 16) & (df['Survived'] == 1)]
child_chance_of_survival = surviving_children / children
child_chance_of_survival
```



1. What is the conditional probability that a person survives given their sex and passenger-class?

```
P(S= true | G=female,C=1)
P(S= true | G=female,C=2)
P(S= true | G=female,C=3)
P(S= true | G=male,C=1)
P(S= true | G=male,C=2)
P(S= true | G=male,C=3)
```

To answer this final set of questions takes a little more than just caluclating percentage.

```
What is the probability that a child who is in third class and is 10 years old or younger survives? Since the number of data points that satisfy the condition is small use the "bayesian" approach and represent your probability as a beta distribution. Calculate a belief distribution for:
S= true | A≤10,C=3
You can express your answer as a parameterized distribution.
```

# Child Survival Rate

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

# Women and Children First: Getting to the Bottom

```py
children = df[df['Age'] < 16]
child_survival_rate = children['Survived'].value_counts(normalize=True) * 100
child_survival_rate
```

```py
women = df[(df['Sex'] == "female") & (df['Age'] > 16)]
women_survival_rate = women['Survived'].value_counts(normalize=True) * 100
women_survival_rate
```

What can you conclude? Children had a 59% chance of survival. Grown women had a 77% chance of survival, and grown men had a 17% chance of survival.

```
Children had a
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

So perhaps the clearest way to express this insight is to say the percent chance of dying for a 1st class and a 3rd class man?

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
