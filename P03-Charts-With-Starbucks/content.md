---
title: "Charts with Starbucks"
slug: charts-with-starbucks
---

Data visualization is the presentation of data in graphical format. Data visualization is both an art and a science as it combines creating visualizations that are both engaging and accurate. In matheimatical applications visualizations can help you better observe trends and patterns in data, or discribe large datasets in a concise way. In this lesson we will focus on some of the most common graphs used to visualize data and describe some tools in Python that can help you create these visualizations!

### Matplotlib

To create our visulizations in Python we will be using the matplotlib library, which will give us the tools to easily create graphs and customiza them. We will cover some of the matplotlib functionality in this lesson, but check out this resource if you want some more introduction to how to use this library.

# Starbucks Drink Menu

In this chapter we will be using the drinks file from the [Starbucks nutrition dataset](https://www.kaggle.com/starbucks/starbucks-menu). This dataset includes the nutritional information for Starbucks’ food and drink menu items. All nutritional information for drinks are for a 12oz serving size. In this lesson we will be using the starbucks drinks csv file as the basis for our visualizations. In python there is a library called csv that makes handling csv files easier. Take a look at the example below to learn more about how to use this library.


Create a new Jupyter Notebook in your `ql-tutorials folder` called "starbucks-drink-menu" and put the drink menu data set .csv in the same directory. First let's look at the csv:

```py
import csv #the csv library
with open('starbucks_drinkMenu_expanded.csv') as csvfile: #open the file
    #creates a csv reader object which stores the lines of the files in lists and lets us iterate over them
    drinksreader = csv.reader(csvfile)
    headers = next(drinksreader, None) #skip over the headers
    for row in drinksreader:
        print(row)#take a look at what is being printed out
```

# Adding a Bar Chart

Let's start by creating a visualization that you might already be familiar with: a bar chart. Bar charts are used to show comparisons between categories of data. A bar chart will have two axis, one will typically be numerical values while the other will be some sort of category. There are two types of bar charts: vertical and horizontal. Let's looks at some examples of how to create a bar chart using our dataset!

In this example let's compare the sugar content of different types of drinks (lattes, mochas, and teas) using our dataset. Here are the steps we are going to perform to create this visualization:

    1. Read in the data
    1. Extract the headers
    1. Find the index which corresponds to the beverage category and grams of sugar
    1. Filter for the types of drinks we are interested in (lattes, mochas, and teas)
    1. Store in a list
    1. Average the amount of sugar per type
    1. Use matplotlib to build a bar chart

The first axis of our bar chart will be the beverage type, the second will be the the average sugar content in grams. More on bar charts in matplotlib [here](https://pythonspot.com/matplotlib-bar-chart/)
