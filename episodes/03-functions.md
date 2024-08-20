---
title: "Functions"
teaching: 20
exercises: 20
questions:
- "How can evaluate a condition?"
- "How can I repeat an action?"
- "How can create my custom functions?"

objectives:
- "Use the `if` conditional to decide an action"
- "Use the `for` loop to iterate actions"
- "Create your functions"

keypoints:
- "The conditional `if` evaluates a statement and performs an action"
- "The for loop repeats an action a predetermined number of times"
- "Custom functions can be defined with `def`"
---




## If statements
The `if` statement is a conditional statement in Python that allows us to execute a 
block of code only if a certain condition is true. It follows this syntax:
~~~
if condition:
    # code block to execute if condition is True
~~~
{: .language-python}

Let's look at whether the two characters representing nucleotides are equal.
~~~
char1='A'
char2='A'

if char1 == char2:
    print( char1,"equal", char2)
~~~
{: .language-python}

The else conditional executes a block when the condition in the if is not true.
~~~
char1='A'
char1='G'

if char1 == char2:
    print( char1,"equal", char2)
else:
    print( char1,"is not equal", char2)
~~~
{: .language-python}

~~~
 A is not equal G
~~~
{: .output}  

You can add as many instructions inside the `if` as you want by indenting the sentences.
Just remember always to keep the same amount of characters in the indentation. 

> ## Exercise 1(Begginer): Evaluate if two strings have equal length
> Fill in the blanks to evaluate if the following strings have equal lengths.
> ~~~
> str1="ACGT"
> str2="GATAKA"
> 
> __ ___(____) != ___(____):
>       print("Strings does not have equal length")
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > if len(str1) != len(str2):
> >     print(str1,str2)
> >     print("Strings does not have equal length")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}


## For loops
The for loop is used in Python to iterate over a sequence (such as a list, tuple, string, etc.) 
and execute a block of code for each element in the sequence. It follows this syntax:
~~~
for item in sequence:
    # code block to execute for each item
~~~
{: .language-python}

~~~
str1="ACGTAC"
distance=0
for char in str1:
    print("The character is",char)
~~~
{: .language-python}

~~~
str1="ACGTAC"
str2="GATAKA"
distance=0
for char1, char2 in zip(str1, str2):
    # If the characters are different, increment the distance
    if char1 != char2:
        distance += 1
~~~
{: .language-python}
            
## Functions
Apart from the built-in functions and the library functions, you can make your functions, 
first, you define them, and then you use them. To define a function you need to give it a name, 
say what information you need to feed to it, and what output you want.

Here we will wrap the conditional to decide if two characters are equal in the function
equal_chars. First, we defined the function and then we called it.
~~~
def equal_chars(character1, character2):
    value=""
    if character1 == character2:
        value="equal"
    else:
        value="Not equal"

    return value
~~~
{: .language-python}

~~~
char1='A'
char1='G'

equal_chars(char1,char2)
~~~
{: .language-python}

After we create our first function, Let's create a hamming distance function for two strings. 
The function hamming_distance() takes two parameters: str1 and str2, the two strings for which the Hamming distance is calculated.

First, we check if the lengths of the two strings are equal. If they are not equal, we raise a ValueError 
because the Hamming distance is only defined for strings of equal length.
We initialize a variable distance to store the Hamming distance.
We then iterate over the characters of the two strings using the zip() function, which pairs 
the corresponding elements of the two strings together.
For each pair of characters, if they are different, we increment the distance variable.
Finally, we return the calculated Hamming distance.
You can use this function to calculate the Hamming distance between any two strings in Python.
~~~
def hamming_distance(str1, str2):
    # Check if the strings have equal length
    if len(str1) != len(str2):
        raise ValueError("Strings must have equal length")

    # Initialize the Hamming distance to 0
    distance = 0

    # Iterate over the characters of the strings
    for char1, char2 in zip(str1, str2):
        # If the characters are different, increment the distance
        if char1 != char2:
            distance += 1

    # Return the calculated Hamming distance
    return distance
~~~
{: .language-python}


Now lets add a multiline comment documenting the parameters needed for the fucntion.
~~~
def hamming_distance(str1, str2):
    """
    Calculate the Hamming distance between two strings.

    Parameters:
    str1 (str): First string
    str2 (str): Second string

    Returns:
    int: Hamming distance between the two strings
    """
    # Check if the strings have equal length
    if len(str1) != len(str2):
        raise ValueError("Strings must have equal length")

    # Initialize the Hamming distance to 0
    distance = 0

    # Iterate over the characters of the strings
    for char1, char2 in zip(str1, str2):
        # If the characters are different, increment the distance
        if char1 != char2:
            distance += 1

    # Return the calculated Hamming distance
    return distance
~~~
{: .language-python}

> ## Exercise 2(Intermediate): Sort the function to count the nucleotides in a string
>  ~~~
>   return nucleotide_counts  
>    nucleotide_counts = {'A': 0, 'C': 0, 'G': 0, 'T': 0}
>
>      if nucleotide in nucleotide_counts:
>    for nucleotide in sequence:
>            nucleotide_counts[nucleotide] += 1
>
>  def calculate_nucleotide_frequency(sequence):
>  ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > def calculate_nucleotide_frequency(sequence):
> >     nucleotide_counts = {'A': 0, 'C': 0, 'G': 0, 'T': 0}
> > 
> >     for nucleotide in sequence:
> >        if nucleotide in nucleotide_counts:
> >             nucleotide_counts[nucleotide] += 1
> > 
> >    return nucleotide_counts
> >  ~~~
> > {: .language-python}
> > 
> {: .solution}
{: .challenge}

Combining the data types you just learned, it is possible to automatize the function even more.
Suppose that "population" is a numpy ndarray with genomes as rows. Genomes are represented with only
two characters: 1 and 0. 

> ## Exercise 3(Intermediate): Sort the comments to document a Hamming distance function for matrixes
>  ~~~
> # The Hamming distance is multiplied by the number of genes to convert it into an absolute distance
>  # Number of genomes 
>  # Calculate the Hamming distance between each pair of genomes
>  # Saving the distance in the matrix
>  # Create an empty matrix for Hamming distances
>  
>  def calculate_hamming_matrix(population):
>     # COMMENT 1
>     num_genomes = population.shape[0]
>     # COMMENT 2
>     hamming_matrix = np.zeros((num_genomes, num_genomes), dtype=int)
>     # COMMENT 3
>     for i in range(num_genomes):
>         for j in range(i+1, num_genomes):  # j=i+1 to avoid calculating the same distance twice
>             #COMMENT 4
>             distance = hamming(population[i], population[j]) * len(population[i])
>             hamming_matrix[i, j] = distance # COMMENT 5
>             hamming_matrix[j, i] = distance  # The matrix is symmetric
>      
>     return hamming_matrix
>   ~~~
>  {: .language-python}
>
> > ## Solution
> > ~~~
> > def calculate_hamming_matrix(population):
> >    # Number of genomes
> >    num_genomes = population.shape[0]
> >    # Create an empty matrix for Hamming distances
> >    hamming_matrix = np.zeros((num_genomes, num_genomes), dtype=int)
> >    # Calculate the Hamming distance between each pair of genomes
> >    for i in range(num_genomes):
> >        for j in range(i+1, num_genomes):  # j=i+1 to avoid calculating the same distance twice
> >            # The Hamming distance is multiplied by the number of genes to convert it into an absolute distance
> >            distance = hamming(population[i], population[j]) * len(population[i])
> >            hamming_matrix[i, j] = distance
> >            hamming_matrix[j, i] = distance  # The matrix is symmetric
> >    return hamming_matrix
> >  ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}






