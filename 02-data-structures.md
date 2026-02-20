---
title: Data Structures
teaching: 40
exercises: 25
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand fundamental data structures such as lists, arrays, dictionaries, and Pandas dataframes.
- Efficient data manipulation, selection and filtering.
- Tabular data management with Pandas.
- Read data from a URL.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I store information in Python?
- How can I access the elements of an array or a dictionary?
- How can I efficiently manage tabular data in Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

## List

A list is an indexed, ordered, changeable sequence of elements that can be of different types and it allows duplicate values. They are defined using square brackets `[]`:

```python
thislist = ["bacteria", "archea", "fungus", 4]
print(thislist)
```

```output
['bacteria', 'archea', 'fungus', 4]
```

To access elements in a list, we can use their index.

```python
first_element = thislist[0]
print(first_element)
```

```output
bacteria
```

We can also access elements in the list using negative indices, which count from the end of the list towards the beginning.

```python
print(thislist[-1])
```

```output
4
```

You can add elements to a list using the `append()` method to add an element to the end of the list.

```python
thislist.append('animal')
print(thislist)
```

```output
['bacteria', 'archea', 'fungus', 4, 'animal']
```

You can also extend a list by adding all the elements from another list using the `extend()` method.

```python
thislist.extend([1,2,3])
print(thislist)
```

```output
['bacteria', 'archea', 'fungus', 4, 'animal', 1, 2, 3]
```

You can remove elements from a list using the word `del` followed by the index of the element you want to remove.

```python
del thislist[3]
print(thislist)
```

```output
['bacteria', 'archea', 'fungus', 'animal', 1, 2, 3]
```

You can also use the `remove()` method to remove a specific element by its value.

```python
thislist.remove('animal')
print(thislist)
```

```output
['bacteria', 'archea', 'fungus', 1, 2, 3]
```

You can concatenate two lists using the `+` operator or the `extend()` method.

```python
mylist1 = ['bacteria', 'archea', 'fungus']
mylist2 = ['animal', 'algae', 'plant']

newlist = mylist1 + mylist2
print(newlist)
```

```output
['bacteria', 'archea', 'fungus', 'animal', 'algae', 'plant']
```

The `sort()` method sorts the elements of the list in ascending order by default. All elements need to be of the same type. If we try to sort the elements of the list `thislist`, we will get an error.

```python
thislist.sort()
```

```output
TypeError: '<' not supported between instances of 'int' and 'str'
```

```python
newlist.sort()
print(newlist)
```

```output
['bacteria', 'archea', 'fungus', 'animal', 'algae', 'plant']
```

To sort them in descending order:

```python
newlist.sort(reverse = True)
print(newlist)
```

```output
['plant', 'algae', 'animal', 'fungus', 'archea', 'bacteria']
```

Consider that the `sort()` method modifies the original list and does not return any value. To sort a list without modifying the original, you can use the `sorted()` function, which returns a new sorted list.

:::::::::::::::::::::::::::::::::::::::::  callout

## Select elements of a list with slices

:::::::::::::::  spoiler

## Extra content

Another way to access list data in Python is by using the "slice" method: list[start:end]. This slice includes the elements whose indices are in the range from `start` to `end - 1`:

- **start:** It is the index from which we start including elements in the slice.
- **end:** It is the index up to which we include elements in the slice, but not including the element at this index.

For example, if we want to get a slice of `newlist` from index 1 to index 4, we would use the notation `newlist[1:4]` and we will get a slice that includes elements from index 1 (inclusive) to index 4 (exclusive).

```python
newlist[1:4]
```

```output
['algae', 'animal', 'fungus']
```

Another syntax of "slices" in Python with the notation list[start:end:step] refers to the technique for selecting a subset of elements from a list using three parameters:

- **start:** Indicates the index from which we start including elements in the slice.
- **end:** Indicates the index up to which we include elements in the slice, excluding the element at this index.
- **step:** Indicates the size of the step or increment between the selected elements. That is, how many elements we skip in each step.

If we run `newlist[::2]`, we get a slice that includes elements of the `newlist`, but selecting every second element. It's like starting from the beginning of the list, ending at the end, and selecting every second element.

```python
newlist[::2]
```

```output
['plant', 'animal', 'archea']
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise 1(Begginer): Manipulating lists

You are working with genetic data represented by the following list:

```python
genes = ["AGCT", "TCGA", "ATCG", "CGTA"]
```

How can you remove the sequence "TCGA" and add a new sequence "CATG"? What is the sequence at index 2.

:::::::::::::::  solution

## Solution

You can remove "TCGA" from the list using the remove() method:

```python
genes.remove("TCGA")
```

To add "CATG" to the list, you can use the append() method:

```python
genes.append("CATG")
```

To find the sequence at index 2, you can access the element at that index using indexing.

```
sequence_at_index_2 = genes[2]
print(sequence_at_index_2)
```

```output
CGTA
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Dictionary

Dictionaries (dict) are collections of key-value pairs. Each element in the dictionary has a key and an associated value. They are defined using curly braces {} and separating the keys and values with colons `:`. Dictionaries in Python are mutable, meaning you can add, modify, and delete elements as needed.

```python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
```

You can access the values of the dictionary using their keys.

```python
print(thisdict['brand']) 
```

```output
Ford
```

```python
print(thisdict['year'])
```

```output
1964
```

If you try to access a key that does not exist in the dictionary, Python will raise a KeyError.

```python
print(thisdict['color'])
```

```output
KeyError: 'color'
```

You can add a new key-value pair to the dictionary by simply assigning a value to a new key.

```python
thisdict['color'] = 'red'
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Mustang', 'year': 1964, 'color': 'red'}
```

You can modify the value associated with an existing key in the dictionary.

```python
thisdict['year'] = 2022
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022, 'color': 'red'}
```

You can delete an item from the dictionary using the `del` word.

```python
del thisdict['color']
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022}
```

You can also use the `pop()` method to remove an item and return its value.

```python
thisdict['color'] = 'red'
deleted_value = thisdict.pop('color')
print(deleted_value) 
```

```output
red
```

```python
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Mustang', 'year': 2022}
```

Reserved methods for dictionaries include `keys()`, `values()`, and `items()`. These methods provide convenient ways to access different aspects of a dictionary:

- `keys()`: This method returns a view object that displays a list of all the keys in the dictionary. It allows you to iterate over the keys or convert them into a list if needed.

```python
keys = thisdict.keys()
print(keys)  
```

```output
dict_keys(['brand', 'model', 'year'])
```

- `values()`: This method returns a view object that displays a list of all the values in the dictionary. Similar to `keys()`, it allows iteration over the values or conversion into a list.

```python
values = thisdict.values()
print(values)
```

```output
dict_values(['Ford', 'Mustang', 2022])
```

- `items()`: This method returns a view object that displays a list of tuples, where each tuple contains a key-value pair from the dictionary. It's useful for iterating over both keys and values simultaneously, or for converting the dictionary into a list of key-value pairs.

```python
items = thisdict.items()
print(items) 
```

```output
dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 2022)])
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Modify a dictionary

:::::::::::::::  spoiler

## Extra content

You can modify (update) a dictionary using the `update()` method. When you call the `update()` method on a dictionary, you pass another dictionary as an argument. The method then iterates over the key-value pairs in the second dictionary and adds them to the first dictionary. If any keys in the second dictionary already exist in the first dictionary, their corresponding values are updated to the new values.

```python
otherdict = {'model': 'Focus', 'price': 30000}
thisdict.update(otherdict)
print(thisdict)
```

```output
{'brand': 'Ford', 'model': 'Focus', 'year': 2022, 'price': 30000}
```

To add new entries to our dictionary, we use the `append()` method.

```python
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
```

```output
{'brand': ['Ford', 'Toyota', 'Honda'], 'model': ['Mustang', 'Corolla', 'Civic'], 'year': [1964, 2020, 2019], 'color': ['red', 'blue', 'green'], 'price': [15000, 20000, 18000]}
```

One way to get the model and year values for each brand is as follows.

```python
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
```

```output
Ford's Year: 1964
Ford's Model: Mustang
Toyota's Year: 2020
Toyota's Model: Corolla
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise 2(Begginer): Manipulating Dictionaries

Suppose that you have the following dictionary:

```
genes_dict = {"gene1": { "name": "BRCA1", "start_position": 43044295, "end_position": 43125483},
              "gene2": { "name": "TP53", "start_position": 7571720, "end_position": 7588830},
              "gene3": { "name": "EGFR", "start_position": 55086715, "end_position": 55225454}}
~~~
{: .language-python}

Which command correctly adds a new gene "gene4" with its associated information to an existing genes dictionary in Python?
 
a) `genes_dict.add("gene4", {"name": "GENE4", "start_position": 123456, "end_position": 234567})`
 
b) `genes_dict["gene4"] = {"name": "GENE4", "start_position": 123456, "end_position": 234567}`
 
c) `genes_dict.append("gene4": {"name": "GENE4", "start_position": 123456, "end_position": 234567})`
 
d) `genes_dict.insert(4, {"name": "GENE4", "start_position": 123456, "end_position": 234567})`
 
> ## Solution
>
> The correct answer is option b).
> It uses the indexing syntax to add a new key-value pair to the genes_dict dictionary, where the key is "gene4" and the value is a dictionary representing the gene's characteristics.
> 
{: .solution}
```

::::::::::::::::::::::::::::::::::::::::::::::::::

## Array

An method for creating and manipulating multidimensional arrays is by using NumPy. NumPy serves as a foundational library for scientific computing in Python, offering robust support for multidimensional arrays and an extensive array of mathematical functions for efficient memory utilization and rapid numerical operations.

To import it, we use the following.

```python
import numpy as np
```

To create a one-dimensional array, we use the following.

```python
myarray = np.array([1,2,3,4,5,6])
print(myarray)
```

```output
[1 2 3 4 5 6]
```

In NumPy, there are functions to create arrays of zeros or ones. To create an array filled with zeros, you can use `np.zeros(shape)`, where shape is the desired shape of the array:

```python
zeros_array = np.zeros(10)
print(zeros_array)
```

```output
[0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
```

To create an array filled with ones, you can use `np.ones(shape)`.

```python
ones_array = np.ones(10)
print(ones_array)
```

```output
[1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Other ways to create arrays and multidimensional arrays

:::::::::::::::  spoiler

## Extra content

Another way to create arrays is by using sequences with `arange()`, for example:

```python
np.arange(10)
```

```output
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

Or using a notation similar to slices: `arange(start, stop, step)`:

```python
np.arange(1,10,1)
```

```output
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
```

We can also create them using random values:

```python
np.random.randint(0, 10, 5)
```

```output
array([9, 6, 0, 2, 7])
```

Multidimensional arrays can be created in various ways by specifying the dimensions of each dimension. For example, to create a 2-dimensional array filled with zeros, ones, or random values:

```python
array_zeros = np.zeros((3,3))
array_ones = np.ones((3,3))
array_rand = np.random.randint(0,10,(3,3))

print(array_zeros)
print(array_ones)
print(array_rand)
```

```output
[[0. 0. 0.]
[0. 0. 0.]
[0. 0. 0.]]

[[1. 1. 1.]
[1. 1. 1.]
[1. 1. 1.]]

[[4 5 4]
[1 7 8]
[7 9 9]]
```

Another way to create a two dimensional array is:

```python
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(arr_2d)
```

```output
[[1 2 3]
[4 5 6]
[7 8 9]]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

The expression `len(array)` returns the length of the array, which corresponds to the number of elements in the array. For a one-dimensional array, this is the number of elements it contains. For a two-dimensional array, it is the number of rows in the array.

```python
length = len(ones_array)
print(length)
```

```output
10
```

The NumPy library also allows us to load databases using `loadtxt`. We will use a toy dataset to learn how to import a `csv` file into a numpy array. The `request` module is used in Python to make HTTP requests to web servers.

```python
import requests

#  The url to the csv file
url = "https://raw.githubusercontent.com/carpentries-incubator/pangenomics/gh-pages/files/spiral_2d.csv"

# Get the content of the file
response = requests.get(url)
content = response.text

# Load the data into a NumPy array
data = np.loadtxt(content.splitlines(), delimiter=' ')

data
```

```output
array([[   2.728,    6.513],
       [   3.776,   26.114],
       [   5.595,   38.47 ],
       ...,
       [2003.23 , 1849.23 ],
       [2003.95 , 1928.41 ],
       [2004.09 , 1966.77 ]])
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise 3(Begginer): Manipulating arrays

Suppose you have a the following array dna\_array containing DNA sequences as strings.

```python
dna_sequences = ["AGCT", "TCGA", "ATCG", "CGTA", "GATTACA"]
dna_array = np.array(dna_sequences)
print(dna_array)
```

You want to extract the sequences that meet a specific condition. Which NumPy function would you use to extract DNA sequences from `dna_array` that contain "AT"?

a) `np.extract(dna_array == 'AT', dna_array)`

b) `np.where(dna_array == 'AT')`

c) `np.extract(np.char.startswith(dna_array, 'AT'), dna_array)`

d) `dna_array[np.char.count(dna_array, 'AT') > 0]`

:::::::::::::::  solution

## Solution

The correct is d).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## DataFrame

As we see in the first episode, Pandas is an indispensable library specialized in working with tabular data or a DataFrame. We will import the Pandas with its usual alias `pd`.

```python
import pandas as pd
```

One form to create a DataFrame is with a dictionary. We will use the dictionary `thisdict` and then we will convert it to a dataframe.

```python
print(thisdict)
```

```output
{'brand': ['Ford', 'Toyota', 'Honda'], 'model': ['Mustang', 'Corolla', 'Civic'], 'year': [1964, 2020, 2019], 'color': ['red', 'blue', 'green'], 'price': [15000, 20000, 18000]}
```

We will add a row name with `index`.

```python
df = pd.DataFrame(thisdict, index = ['C1', 'C2', 'C3'])
print(df)
```

```output
     brand    model  year  color  price
C1    Ford  Mustang  1964    red  15000
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
```

We can explore the dataframe using different methods, such as head(), tail(), info(), describe(), etc. For example:

```python
# Print the first two rows
print(df.head(2))
```

```output
     brand    model  year color  price
C1    Ford  Mustang  1964   red  15000
C2  Toyota  Corolla  2020  blue  20000
```

```python
# Print the last two rows
print(df.tail(2))
```

```output
     brand    model  year  color  price
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
```

```python
# Display summary statistics
print(df.describe())
```

```output
              year         price
count     3.000000      3.000000
mean   2001.000000  17666.666667
std      32.046841   2516.611478
min    1964.000000  15000.000000
25%    1991.500000  16500.000000
50%    2019.000000  18000.000000
75%    2019.500000  19000.000000
max    2020.000000  20000.000000
```

```python
# Display the information of the DataFrame
print(df.info())
```

```output
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
```

Pandas provides different methods for indexing and selecting data from DataFrames. You can use `iloc[]` for integer-based indexing and `loc[]` for label-based indexing. For example:

- Select columns by name:

```python
print(df['model'])
```

```output
C1    Mustang
C2    Corolla
C3      Civic
Name: model, dtype: object
```

- Select rows by index using `iloc[]`

```python
print(df.iloc[1])
```

```output
brand     Toyota
model    Corolla
year        2020
color       blue
price      20000
Name: C2, dtype: object
```

- Select rows by index name using `loc[]`

```python
print(df.loc['C1'])
```

```output
brand       Ford
model    Mustang
year        1964
color        red
price      15000
Name: C1, dtype: object
```

- Select rows and columns with `iloc[]`

```python
print(df.iloc[0:2, 0:2])
```

```output
     brand    model
C1    Ford  Mustang
C2  Toyota  Corolla
```

- Select multiple columns.

```python
print(df[['model', 'year']])
```

```output
      model  year
C1  Mustang  1964
C2  Corolla  2020
C3    Civic  2019
```

We can filter the data by some conditions. For example:

```python
print(df[df['year']> 2000])
```

```output
     brand    model  year  color  price
C2  Toyota  Corolla  2020   blue  20000
C3   Honda    Civic  2019  green  18000
```

We can modify DataFrames by adding or removing rows and columns, updating values, and performing various data transformations. For example:

```python
# Add a column
df['mileage'] = [150000, 5000, 30000]
print(df)
```

```output
     brand    model  year  color  price  mileage
C1    Ford  Mustang  1964    red  15000   150000
C2  Toyota  Corolla  2020   blue  20000     5000
C3   Honda    Civic  2019  green  18000    30000
```

```python
# Remove a column from the DataFrame
df.drop(columns=['color'], inplace=True)

print(df)
```

```output
     brand    model  year  price  mileage
C1    Ford  Mustang  1964  15000   150000
C2  Toyota  Corolla  2020  20000     5000
C3   Honda    Civic  2019  18000    30000
```

```python
# Update values in a DataFrame
df.loc[df['model'] == 'Corolla', 'mileage'] = 25000

print(df)
```

```output
     brand    model  year  price  mileage
C1    Ford  Mustang  1964  15000   150000
C2  Toyota  Corolla  2020  20000    25000
C3   Honda    Civic  2019  18000    30000
```

Just like with numpy, we can read CSV files that are stored on our computer or on the internet.

```python
# Read the url database
url = "https://raw.githubusercontent.com/carpentries-incubator/pangenomics/gh-pages/files/familias_minis.csv"
df_genes = pd.read_csv(url, index_col=0)
df_genes.head(5)
```

```output
                                  g_A909               g_2603V               g_515               g_NEM316
A909|MGIDGNCP_01408  A909|MGIDGNCP_01408  2603V|GBPINHCM_01420   515|LHMFJANI_01310  NEM316|AOGPFIKH_01528
A909|MGIDGNCP_00096  A909|MGIDGNCP_00096  2603V|GBPINHCM_00097   515|LHMFJANI_00097  NEM316|AOGPFIKH_00098
A909|MGIDGNCP_01343  A909|MGIDGNCP_01343                   NaN                  NaN  NEM316|AOGPFIKH_01415
A909|MGIDGNCP_01221  A909|MGIDGNCP_01221                   NaN   515|LHMFJANI_01130                    NaN
A909|MGIDGNCP_01268  A909|MGIDGNCP_01268  2603V|GBPINHCM_01231   515|LHMFJANI_01178  NEM316|AOGPFIKH_01341  
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise 4(Advanced): Manipulating dataframes

Use the dataframe `df_genes` and add a column that counts how many genes are in each row, for example, the first row has 4 genes but the third row has only two.

:::::::::::::::  solution

## Solution

With the following command you can add a column. The method `count` counts how many elements there are per row, with `axis = 1` we can fix the column.

```python
df_genes['Number of genes'] = df_genes.count(axis=1)
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Another data structures: Sets and Tuples

:::::::::::::::  spoiler

## Extra content

### Tuple

Tuples are indexed and ordered sequences, they are immutable, meaning they cannot be modified after creation. The elements of a tuple can be numbers, strings, or combinations of both types. A tuple is defined using parentheses `()`:

```python
thistuple = ("bacteria", "archea", "fungus", 3)
print(thistuple)
```

```output
('bacteria', 'archea', 'fungus', 3)
```

To access the elements of a tuple, we can use its index. In Python, indexing typically starts at 0. This means that the first element in a sequence (such as a list, tuple, or string) has an index of 0, the second element has an index of 1, and so on.

```python
first_element = thistuple[0]
print(first_element)
```

```output
bacteria
```

We can also access tuple elements using negative indices, which count from the end of the tuple towards the beginning.

```python
print(thistuple[-1])
```

```output
3
```

### Set

Sets are unindexed, unordered collections of  unique element, duplicates are not allowed. The sets can contain different data types. They are defined using curly braces {}:

```python
myset = {"bacteria", "archea", "fungus", 4}
print(myset)
```

```output
{'archea', 3, 'fungus', 'bacteria'}
```

Sets in Python are mutable, meaning you can add and remove elements, but you cannot directly modify existing elements. To add elements to a set, you can use the `add()` method.

```python
myset.add('animal')
print(myset)
```

```output
{3, 'fungus', 'bacteria', 'animal', 'archea'}
```

To remove an element from a set, you can use the `remove()`.

```python
myset.remove(3)
print(myset)
```

```output
{'fungus', 'bacteria', 'animal', 'archea'}
```

Sets are useful when you need to store a collection of unique elements and perform efficient set operations such as removing duplicates and comparing collections.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Gain familiarity with fundamental data structures such as tuples, sets, lists, dictionaries, and arrays.
- Develop skills in manipulating data by accessing, modifying, and filtering elements within data structures.
- Learn to work with tabular data using Pandas DataFrames, including loading and exploring data.

::::::::::::::::::::::::::::::::::::::::::::::::::


