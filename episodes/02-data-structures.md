---
title: "Data Structures"
teaching: 10
exercises: 10
questions:
- "How can I store information in Python?"
- "How can I acces to the elements of an array or a dictionary?"
- "How can I efficiently manage tabular data in Python?"

objectives:
- "Understand fundamental data structures such as list, arrays, dictionaries and Panda dataframes."
- "Efficient data manipulation, selectiom and filtering."
- "Tabular data management with Pandas."
- "Read data from an URL."

keypoints:
- "Gain familiarity with fundamental data structures such as tuples, sets, list, dictionaries and arrays."
- "Develop skills in manipulating data by accessing, modifying and filtering elements within data structures."
- "Lear to work with tabular data using Pandas DataFrames, including loading and exploring data."
---

## List

A list is indexed, ordered, changeable sequence of elementes that can be of different types and allows duplicate values. They are defined using square brackets `[]`:

~~~
thislist = ["apple", "banana", "cherry", 4]
print(thislist)
~~~
{: .language-python}
~~~
['apple', 'banana', 'cherry', 4]
~~~
{: .output}

To access elements in a list, we can use their index.
~~~
first_element = thislist[0]
print(first_element)
~~~
{: .language-python}

~~~
apple
~~~
{: .output}

We can also access elements in the list using negative indices, which count from the end of the list towards the beginning.

~~~
print(thislist[-1])
~~~
{: .language-python}

~~~
4
~~~
{: .output}

You can add elements to a list using the `append()` method to add an element to the end of the list.

~~~
thislist.append('grape')
print(thislist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 4, 'grape']
~~~
{: .output}

You can also extend a list by adding all the elements from another list using the `extend()` method.

~~~
thislist.extend([1,2,3])
print(thislist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 4, 'grape', 1, 2, 3]
~~~
{: .output}

You can remove elements from a list using the word `del` followed by the index of the element you want to remove.

~~~
del thislist[3]
print(thislist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 'grape', 1, 2, 3]
~~~
{: .output}

You can also use the `remove()` method to remove a specific element by its value.

~~~
thislist.remove('grape')
print(thislist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 1, 2, 3]
~~~
{: .output}

You can concatenate two lists using the `+` operator or the `extend()` method.

~~~
mylist1 = ['apple', 'banana', 'cherry']
mylist2 = ['grape', 'lemon', 'orange']

newlist = mylist1 + mylist2
print(newlist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 'grape', 'lemon', 'orange']
~~~
{: .output}

The `sort()` method sorts the elements of the list in ascending order by default. All elements need to be of the same type. If we try to sort the elements of the list thislist, we will get an error.

~~~
thislist.sort()
~~~
{: .language-python}

~~~
TypeError: '<' not supported between instances of 'int' and 'str'
~~~
{: .output}

~~~
newlist.sort()
print(newlist)
~~~
{: .language-python}

~~~
['apple', 'banana', 'cherry', 'grape', 'lemon', 'orange']
~~~
{: .output}

To sort them in descending order:

~~~
newlist.sort(reverse = True)
print(newlist)
~~~
{: .language-python}

~~~
['orange', 'lemon', 'grape', 'cherry', 'banana', 'apple']
~~~
{: .output}

Consider that the `sort()` method modifies the original list and does not return any value. To sort a list without modifying the original, you can use the `sorted()` function, which returns a new sorted list.

> ## Slice method
>
> > ## Select elements of a list with slices
>> Another way to access list data in Python is by using the "slice" method: list[start:end]. This slice includes the elements whose indices are in the range from `start` to `end - 1`: 
>> - **start:** It is the index from which we start including elements in the slice.
>> - **end:** It is the index up to which we include elements in the slice, but not including the element at this index.
>>
>> 
>> For example, if we want to get a slice of `newlist` from index 1 to index 4, we would use the notation `newlist[1:4]` and we will get a slice that includes elements from index 1 (inclusive) to index 4 (exclusive).
>> ~~~
newlist[1:4]
~~~
{: .language-python}
>> ~~~
['lemon', 'grape', 'cherry']
~~~
{: .output}
>>
>> Another syntax of "slices" in Python with the notation list[start:end:step] refers to the technique for selecting a subset of elements from a list using three parameters:
>> - **start:** Indicates the index from which we start including elements in the slice.
>> - **end:** Indicates the index up to which we include elements in the slice, excluding the element at this index.
>> - **step:** Indicates the size of the step or increment between the selected elements. That is, how many elements we skip in each step.
>>
>> If we run `newlist[::2]`, we get a slice that includes elements of the `newlist`, but selecting every second element. It's like starting from the beginning of the list, ending at the end, and selecting every second element.
>>
>> ~~~
newlist[::2]
~~~
{: .language-python}
>>
>> ~~~
['orange', 'grape', 'banana']
~~~
{: .output}
>>
> {: .solution}
{: .callout}


> ## Exercise 2: 
>
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}


## Dictionary

Dictionaries (dict) are collections of key-value pairs. Each element in the dictionary has a key and an associated value. They are defined using curly braces {} and separating the keys and values with colons `:`. Dictionaries in Python are mutable, meaning you can add, modify, and delete elements as needed.
~~~
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
print(thisdict)
~~~
{: .language-python}
~~~
{'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
~~~
{: .output}

You can access the values of the dictionary using their keys.
~~~
print(thisdict['brand']) 
~~~
{: .language-python}

~~~
Ford
~~~
{: .output}


~~~
print(thisdict['year'])
~~~
{: .language-python}

~~~
1964
~~~
{: .output}

If you try to access a key that does not exist in the dictionary, Python will raise a KeyError.

~~~
print(thisdict['color'])
~~~
{: .language-python}

~~~
KeyError: 'color'
~~~
{: .output}

You can add a new key-value pair to the dictionary by simply assigning a value to a new key.

~~~
thisdict['color'] = 'red'
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': 'Ford', 'model': 'Mustang', 'year': 1964, 'color': 'red'}
~~~
{: .output}

You can modify the value associated with an existing key in the dictionary.

~~~
thisdict['year'] = 2022
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022, 'color': 'red'}
~~~
{: .output}

You can delete an item from the dictionary using the `del` word.

~~~
del thisdict['color']
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022}
~~~
{: .output}


You can also use the `pop()` method to remove an item and return its value.

~~~
thisdict['color'] = 'red'
deleted_value = thisdict.pop('color')
print(deleted_value) 
~~~
{: .language-python}

~~~
red
~~~
{: .output}


~~~
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022}
~~~
{: .output}


Reserved methods for dictionaries include `keys()`, `values()`, and `items()`. These methods provide convenient ways to access different aspects of a dictionary:

- `keys()`: This method returns a view object that displays a list of all the keys in the dictionary. It allows you to iterate over the keys or convert them into a list if needed.

~~~
keys = thisdict.keys()
print(keys)  
~~~
{: .language-python}

~~~
dict_keys(['brand', 'model', 'year'])
~~~
{: .output}

- `values()`: This method returns a view object that displays a list of all the values in the dictionary. Similar to `keys()`, it allows iteration over the values or conversion into a list.

~~~
values = thisdict.values()
print(values)
~~~
{: .language-python}

~~~
dict_values(['Ford', 'Mustang', 2022])
~~~
{: .output}

- `items()`: This method returns a view object that displays a list of tuples, where each tuple contains a key-value pair from the dictionary. It's useful for iterating over both keys and values simultaneously, or for converting the dictionary into a list of key-value pairs.
  
~~~
items = thisdict.items()
print(items) 
~~~
{: .language-python}

~~~
dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 2022)])
~~~
{: .output}


You can modify (update) a dictionary using the `update()` method. When you call the `update()` method on a dictionary, you pass another dictionary as an argument. The method then iterates over the key-value pairs in the second dictionary and adds them to the first dictionary. If any keys in the second dictionary already exist in the first dictionary, their corresponding values are updated to the new values.

~~~
otherdict = {'model': 'Focus', 'price': 30000}
thisdict.update(otherdict)
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': 'Ford', 'model': 'Focus', 'year': 2022, 'price': 30000}
~~~
{: .output}


To add new entries to our dictionary, we use the `append()` method.
~~~
thisdict = {
    'brand': ['Ford', 'Toyota'],
    'model': ['Mustang', 'Corolla'],
    'year': [1964, 2020],
    'color': ['red', 'blue'],
    'price': [15000, 20000]
}

# Add a new brand, model, year, color, and price
new_brand = 'Honda'
new_model = 'Civic'
new_year = 2019
new_color = 'green'
new_price = 18000

thisdict['brand'].append(new_brand)
thisdict['model'].append(new_model)
thisdict['year'].append(new_year)
thisdict['color'].append(new_color)
thisdict['price'].append(new_price)

# Print the updated dictionary
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': ['Ford', 'Toyota', 'Honda'], 'model': ['Mustang', 'Corolla', 'Civic'], 'year': [1964, 2020, 2019], 'color': ['red', 'blue', 'green'], 'price': [15000, 20000, 18000]}
~~~
{: .output}

One way to get the model and year values for each brand is as follows.

~~~
# Get the year and model of each car directly from the dictionary
ford_year = thisdict['year'][thisdict['brand'].index('Ford')]
ford_model = thisdict['model'][thisdict['brand'].index('Ford')]

toyota_year = thisdict['year'][thisdict['brand'].index('Toyota')]
toyota_model = thisdict['model'][thisdict['brand'].index('Toyota')]

# Print the year and model of each car
print("Ford's Year:", ford_year)
print("Ford's Model:", ford_model)
print("Toyota's Year:", toyota_year)
print("Toyota's Model:", toyota_model)
~~~
{: .language-python}

~~~
Ford's Year: 1964
Ford's Model: Mustang
Toyota's Year: 2020
Toyota's Model: Corolla
~~~
{: .output}

> ## Exercise 3: 
>
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}

## Array

An method for creating and manipulating multidimensional arrays is by using NumPy. NumPy serves as a foundational library for scientific computing in Python, offering robust support for multidimensional arrays and an extensive array of mathematical functions for efficient memory utilization and rapid numerical operations.

To import it, we use the following.

~~~
import numpy as np
~~~
{: .language-python}

To create a one-dimensional array, we use the following.

~~~
myarray = np.array([1,2,3,4,5,6])
print(myarray)
~~~
{: .language-python}

~~~
[1 2 3 4 5 6]
~~~
{: .output}

In NumPy, there are functions to create arrays of zeros or ones. To create an array filled with zeros, you can use `np.zeros(shape)`, where shape is the desired shape of the array:

~~~
zeros_array = np.zeros(10)
print(zeros_array)
~~~
{: .language-python}

~~~
[0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
~~~
{: .output}

To create an array filled with ones, you can use `np.ones(shape)`.

~~~
ones_array = np.ones(10)
print(ones_array)
~~~
{: .language-python}

~~~
[1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
~~~
{: .output}

Another way to create arrays is by using sequences with `arange()`, for example:

~~~
np.arange(10)
~~~
{: .language-python}

~~~
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
~~~
{: .output}

Or using a notation similar to slices: `arange(start, stop, step)`:

~~~
np.arange(1,10,1)
~~~
{: .language-python}

~~~
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
~~~
{: .output}

We can also create them using random values:

~~~
np.random.randint(0, 10, 5)
~~~
{: .language-python}

~~~
array([9, 6, 0, 2, 7])
~~~
{: .output}

Multidimensional arrays can be created in various ways by specifying the dimensions of each dimension. For example, to create a 2-dimensional array filled with zeros, ones, or random values:

~~~
array_zeros = np.zeros((3,3))
array_ones = np.ones((3,3))
array_rand = np.random.randint(0,10,(3,3))

print(array_zeros)
print(array_ones)
print(array_rand)
~~~
{: .language-python}

~~~
[[0. 0. 0.]
 [0. 0. 0.]
 [0. 0. 0.]]
 
[[1. 1. 1.]
 [1. 1. 1.]
 [1. 1. 1.]]

[[4 5 4]
 [1 7 8]
 [7 9 9]]
~~~
{: .output}

Another way to create a two dimensional array is:

~~~
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(arr_2d)
~~~
{: .language-python}

~~~
[[1 2 3]
 [4 5 6]
 [7 8 9]]
~~~
{: .output}

The expression `len(array)` returns the length of the array, which corresponds to the number of elements in the array. For a one-dimensional array, this is the number of elements it contains. For a two-dimensional array, it is the number of rows in the array. For example, for the two-dimensional array:

~~~
length = len(arr_2d)
print(length)
~~~
{: .language-python}

~~~
3
~~~
{: .output}

The NumPy library also allows us to load databases using `loadtxt`. We will use a toy dataset to learn how to import a `csv` file into a numpy array. The `request` module is used in Python to make HTTP requests to web servers.

~~~
import requests

#  The url to the csv file
url = "https://raw.githubusercontent.com/carpentries-incubator/pangenomics/gh-pages/files/spiral_2d.csv"

# Get the content of the file
response = requests.get(url)
content = response.text

# Load the data into a NumPy array
data = np.loadtxt(content.splitlines(), delimiter=' ')

data
~~~
{: .language-python}

~~~
array([[   2.728,    6.513],
       [   3.776,   26.114],
       [   5.595,   38.47 ],
       ...,
       [2003.23 , 1849.23 ],
       [2003.95 , 1928.41 ],
       [2004.09 , 1966.77 ]])
~~~
{: .output}

> ## Exercise 4: 
>
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}

## DataFrame

As we see in the first episode, Pandas is an indispensable library specialized in working with tabular data or a DataFrame. We will import the Pandas with its usual alias `pd`.

~~~
import pandas as pd
~~~
{: .language-python}

One form to create a DataFrame is with a dictionary. We will use the dictionary `thisdict` and then we will convert it to a dataframe.

~~~
print(thisdict)
~~~
{: .language-python}

~~~
{'brand': ['Ford', 'Toyota', 'Honda'], 'model': ['Mustang', 'Corolla', 'Civic'], 'year': [1964, 2020, 2019], 'color': ['red', 'blue', 'green'], 'price': [15000, 20000, 18000]}
~~~
{: .output}

We will add a row name with `index`.

~~~
df = pd.DataFrame(thisdict, index = ['C1', 'C2', 'C3'])
print(df)
~~~
{: .language-python}


~~~
     brand    model  year  color  price
C1    Ford  Mustang  1964    red  15000
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
~~~
{: .output}


We can explore the dataframe using different methods, such as head(), tail(), info(), describe(), etc. For example:

~~~
# Print the first two rows
print(df.head(2))
~~~
{: .language-python}

~~~
     brand    model  year color  price
C1    Ford  Mustang  1964   red  15000
C2  Toyota  Corolla  2020  blue  20000
~~~
{: .output}

~~~
# Print the last two rows
print(df.tail(2))
~~~
{: .language-python}

~~~
     brand    model  year  color  price
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
~~~
{: .output}


~~~
# Display summary statistics
print(df.describe())
~~~
{: .language-python}

~~~
              year         price
count     3.000000      3.000000
mean   2001.000000  17666.666667
std      32.046841   2516.611478
min    1964.000000  15000.000000
25%    1991.500000  16500.000000
50%    2019.000000  18000.000000
75%    2019.500000  19000.000000
max    2020.000000  20000.000000
~~~
{: .output}

~~~
# Display the information of the DataFrame
print(df.info())
~~~
{: .language-python}

~~~
<class 'pandas.core.frame.DataFrame'>
Index: 3 entries, C1 to C3
Data columns (total 5 columns):
 #   Column  Non-Null Count  Dtype 
---  ------  --------------  ----- 
 0   brand   3 non-null      object
 1   model   3 non-null      object
 2   year    3 non-null      int64 
 3   color   3 non-null      object
 4   price   3 non-null      int64 
dtypes: int64(2), object(3)
memory usage: 144.0+ bytes
None
~~~
{: .output}

Pandas provides different methods for indexing and selecting data from DataFrames. You can use `iloc[]` for integer-based indexing and `loc[]` for label-based indexing. For example:

- Select columns by name:
  
~~~
print(df['model'])
~~~
{: .language-python}

~~~
C1    Mustang
C2    Corolla
C3      Civic
Name: model, dtype: object
~~~
{: .output}

- Select rows by index using `iloc[]`

~~~
print(df.iloc[1])
~~~
{: .language-python}

~~~
brand     Toyota
model    Corolla
year        2020
color       blue
price      20000
Name: C2, dtype: object
~~~
{: .output}

- Select rows by index name using `loc[]`

~~~
print(df.loc['C1'])
~~~
{: .language-python}

~~~
brand       Ford
model    Mustang
year        1964
color        red
price      15000
Name: C1, dtype: object
~~~
{: .output}


- Select rows and columns with `iloc[]`

~~~
print(df.iloc[0:2, 0:2])
~~~
{: .language-python}

~~~
     brand    model
C1    Ford  Mustang
C2  Toyota  Corolla
~~~
{: .output}

- Select multiple columns.

~~~
print(df[['model', 'year']])
~~~
{: .language-python}

~~~
      model  year
C1  Mustang  1964
C2  Corolla  2020
C3    Civic  2019
~~~
{: .output}

We can filter the data by some conditions. For example:


~~~
print(df[df['year']> 2000])
~~~
{: .language-python}

~~~
     brand    model  year  color  price
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
~~~
{: .output}


We can modify DataFrames by adding or removing rows and columns, updating values, and performing various data transformations. For example:

~~~
# Add a column
df['mileage'] = [150000, 5000, 30000]
print(df)
~~~
{: .language-python}

~~~
     brand    model  year  color  price  mileage
C1    Ford  Mustang  1964    red  15000   150000
C2  Toyota  Corolla  2020   blue  20000     5000
C3   Honda    Civic  2019  green  18000    30000
~~~
{: .output}


~~~
# Remove a column from the DataFrame
df.drop(columns=['color'], inplace=True)

print(df)
~~~
{: .language-python}

~~~
     brand    model  year  price  mileage
C1    Ford  Mustang  1964  15000   150000
C2  Toyota  Corolla  2020  20000     5000
C3   Honda    Civic  2019  18000    30000
~~~
{: .output}

~~~
# Update values in a DataFrame
df.loc[df['model'] == 'Corolla', 'mileage'] = 25000

print(df)
~~~
{: .language-python}

~~~
     brand    model  year  price  mileage
C1    Ford  Mustang  1964  15000   150000
C2  Toyota  Corolla  2020  20000    25000
C3   Honda    Civic  2019  18000    30000
~~~
{: .output}

Just like with numpy, we can read CSV files that are stored on our computer or on the internet.

~~~
# Read the url database
url = "https://raw.githubusercontent.com/carpentries-incubator/pangenomics/gh-pages/files/familias_minis.csv"
df_genes = pd.read_csv(url, index_col=0)
df_genes.head(5)
~~~
{: .language-python}

~~~
                                  g_A909               g_2603V               g_515               g_NEM316
A909|MGIDGNCP_01408  A909|MGIDGNCP_01408  2603V|GBPINHCM_01420   515|LHMFJANI_01310  NEM316|AOGPFIKH_01528
A909|MGIDGNCP_00096  A909|MGIDGNCP_00096  2603V|GBPINHCM_00097   515|LHMFJANI_00097  NEM316|AOGPFIKH_00098
A909|MGIDGNCP_01343  A909|MGIDGNCP_01343                   NaN                  NaN  NEM316|AOGPFIKH_01415
A909|MGIDGNCP_01221  A909|MGIDGNCP_01221                   NaN   515|LHMFJANI_01130                    NaN
A909|MGIDGNCP_01268  A909|MGIDGNCP_01268  2603V|GBPINHCM_01231   515|LHMFJANI_01178  NEM316|AOGPFIKH_01341  
~~~
{: .output}


> ## Exercise 5: 
> Use the dataframe `df_genes` and add a column that counts how many genes are in each row, for example, the first row has 4 genes but the third row has only two. 
>  
> > ## Solution
> > ~~~
> > df_genes['Number of genes'] = df_genes.count(axis=1)
> > ~~~
> > {: .language-python}

## Another data structures

### Tuple

Tuples are indexed and ordered sequences, they are immutable, meaning they cannot be modified after creation. The elements of a tuple can be numbers, strings, or combinations of both types. A tuple is defined using parentheses `()`:

~~~
thistuple = ("apple", "banana", "cherry", 3)
print(thistuple)
~~~
{: .language-python}

~~~
('apple', 'banana', 'cherry', 3)
~~~
{: .output}

To access the elements of a tuple, we can use its index. In Python, indexing typically starts at 0. This means that the first element in a sequence (such as a list, tuple, or string) has an index of 0, the second element has an index of 1, and so on.

~~~
first_element = thistuple[0]
print(first_element)
~~~
{: .language-python}

~~~
apple
~~~
{: .output}

We can also access tuple elements using negative indices, which count from the end of the tuple towards the beginning.

~~~
print(thistuple[-1])
~~~
{: .language-python}

~~~
3
~~~
{: .output}


### Set

Sets are unindexed, unordered collections of  unique element, duplicates are not allowed. The sets can contain different data types. They are defined using curly braces {}:

~~~
myset = {"apple", "banana", "cherry", 4}
print(myset)
~~~
{: .language-python}

~~~
{'banana', 3, 'cherry', 'apple'}
~~~
{: .output}

Sets in Python are mutable, meaning you can add and remove elements, but you cannot directly modify existing elements. To add elements to a set, you can use the `add()` method.


~~~
myset.add('grape')
print(myset)
~~~
{: .language-python}

~~~
{3, 'cherry', 'apple', 'grape', 'banana'}
~~~
{: .output}

To remove an element from a set, you can use the `remove()`.
~~~
myset.remove(3)
print(myset)
~~~
{: .language-python}

~~~
{'cherry', 'apple', 'grape', 'banana'}
~~~
{: .output}

Sets are useful when you need to store a collection of unique elements and perform efficient set operations such as removing duplicates and comparing collections.

> ## Exercise 5: 
> 
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}

> {: .solution}
{: .challenge}
