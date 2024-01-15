---
title: "Introduction to Python"
teaching: 30
exercises: 15
questions:
- ""
objectives:
- ""
keypoints:
- ""
---
## Using Python

In the following episodes, we will learn the fundamental knowledge to read and run the Python programming language. To run Python commands we will use a Jupyter Notebook, which is an interactive platform in which you can run code, write text, and see your results, for example, plots. Follow the instructions in the Setup [page](https://czirion.github.io/pangenomics-workshop/setup.html) to open a Notebook.

## Variables and data types

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
Until now the type of data that we have been using is string (`str`). And we saw that the result of summing strings is a longer combined string.
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

## Built-in functions and libraries
Python has basic functions to carry out specific actions. For example `len()
~~~
len(new_variable)
~~~
{: .language-python}
~~~
12 # The value 'aLongerValue' has 12 characters
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

The `len()` function can give us the number of characters in a string but it can not do anything with a number (type `int`, meaning integer).

[Here](https://docs.python.org/3/library/functions.html) you can check the built-in functions of the Python language.

For extra functionalities, there are libraries, which are collections of functions and data structures (see the next [episode](https://czirion.github.io/pangenomics-python/02-data-structures/index.html))  specialized in a common set of tasks.

Pandas is an indispensable library specialized in working with tabular data. To make it accessible you need to import it. One way to import a library is with `import` library `as` alias. This way you can access the functions using the alias.
~~~
import pandas as pd
~~~
{: .language-python}

~~~

~~~
{: .language-python}
~~~

~~~
{: .output}

> ## Exercise 1: 
>
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}

