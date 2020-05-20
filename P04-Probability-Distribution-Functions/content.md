---
title: "PDFs—Probability Distribution Functions"
slug: pdfs
---



# Explaining PDFs

First let's review the difference between discrete and continuous random variables:

* **Discrete**: takes on a finite or countable number of values.
* **Continuous**: takes on an infinite number of values

Because continuous random variables can take on an infinite number of values, we can't say with certainty what value the variable will be at any point, so we have to instead provide an interval, or range of values that the variable could be.

### For Example: New York City Snow

For example, what's the probability that New York City get's 4 inches of snow on December 17th? 3.99999 and 4.0001 inches don't count, it has to be exactly 4. It would be impossible to say with exact certainty given there are infinite decimals! However, if instead of looking for exactly 4, we looked at the range of values between 3.9 and 4.1, we could compute the probability for that range! This is where PDFs come in to help us calculate this!

# Graphing PDFs

When we graph a PDF, it has a similar pattern to a histogram. The main difference is that instead of the y-axis corresponding to values, it shows the percent probability of the x-axis values. This is known as normalizing the values.

```py
import numpy as np
import pandas as pd

df = pd.read_csv('../Pandas/titanic.csv')
```
