---
title: "Introduction to Python"
teaching:  10
exercises: 5
questions:
- "How can I store information?"
- "How can I perform actions?"
objectives:
- "Assign values to variables."
- "Run built-in functions."
- "Import libraries."
keypoints:
- "Variables are Python objects that store information when you assign it to them."
- "Python has built-in functions that are always accessible."
- "Libraries give you access to more functions."
---
## Using Python

In the following episodes, we will learn the fundamental knowledge to read and run the Python programming language. To run Python commands, we will use a Jupyter Notebook, an interactive platform to run code, write text, and see your results, such as plots. Follow the instructions in the Setup [page](https://carpentries-incubator.github.io/pangenomics-workshop/setup.html) to open a Notebook.

## Variables

In Python, you store information in variables, which have a name and an assigned value.
~~~
variable_name = "value" # Here we assign the value to the variable name
variable_name # Here we ask to see the value
~~~
{: .language-python}
~~~
'value'
~~~
{: .output}
The values can be the result of operations.
~~~
new_variable = "a" + "Longer" + "Value"
new_variable
~~~
{: .language-python}
~~~
'aLongerValue'
~~~
{: .output}
Until now, the data type we have been using is string (`str`). We saw that summing strings results in a longer combined string.
If we work with numerical values the result will be the mathematical one.
~~~
a_number = 300
a_number
~~~
{: .language-python}
~~~
300
~~~
{: .output}
~~~
a_biger_number = 300 + 300
a_biger_number
~~~
{: .language-python}
~~~
600
~~~
{: .output}

We can also perform operations with variables that are already set.
~~~
a_new_number = a_number + a_biger_number + 100
a_new_number
~~~
{: .language-python}
~~~
1000
~~~
{: .output}

And if we want to be more efficient, we can assign values to more than one variable in the same line.

~~~
color_variable , size_variable = "blue", "big"
color_variable
~~~
{: .language-python}
~~~
'blue'
~~~
{: .output}
~~~
size_variable
~~~
{: .language-python}
~~~
'big'
~~~
{: .output}

## Built-in functions and libraries

Python has basic functions to carry out specific actions. In Python, the arguments of the functions go inside parentheses, and different functions take different kinds and numbers of arguments. The function `len()` takes one argument and outputs its length. In the case of a string, the length is the number of characters.
~~~
len(new_variable)
~~~
{: .language-python}
~~~
12
~~~
{: .output}
~~~
len(a_number)
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
/tmp/ipykernel_55271/3566361226.py in <module>
      1 a_number = 300
----> 2 len(a_number)

TypeError: object of type 'int' has no len()
~~~
{: .error}

The `len()` function can give us the number of characters in a string, but it can not do anything with a number (that is of the type `int`, meaning integer). 

[Here](https://docs.python.org/3/library/functions.html), you can check the built-in functions of the Python language.

For extra functionalities, there are libraries, which are collections of functions and data structures (see the next [episode](https://czirion.github.io/pangenomics-python/02-data-structures/index.html))  specialized in a common set of tasks.

Pandas is an indispensable library specialized in working with tabular data. To make it accessible, you need to import it. 
There are several ways to import libraries. 

Import a library while establishing an alias to access the functions using the alias.
~~~
import pandas as pd
pd.read_csv()
~~~
{: .language-python}

Import a library without an alias. You need to access the functions with the complete name of the library.
~~~
import pandas
pandas.read_csv()
~~~
{: .language-python}
Import only certain functions from a library. You don't need to specify a name or alias when calling the function.
~~~
from pandas import read_csv
read_csv()
~~~
{: .language-python}

> ## Exercise 1: 
> Create three variables with the common name of your favorite bird as the variable name and the scientific name as the value.
> Use [built-in functions](https://docs.python.org/3/library/functions.html) to get the length of the scientific name that has the *max*imum length.
>  
> > ## Solution
> > ~~~
> > swallow, goldcrest, sparrow = "Tachycineta thalassina", "Regulus regulus", "Passer domesticus"
> > max(len(swallow), len(goldcrest),len(sparrow))
> > ~~~
> > {: .language-python}
> > ~~~
> > 22
> > ~~~
> > {: .output}
> > 
> {: .solution}
{: .challenge}
