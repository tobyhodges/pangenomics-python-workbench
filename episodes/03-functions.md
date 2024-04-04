---
title: "Functions"
teaching: 10
exercises: 10
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

Lets look if two characters representing nucleotides are equal.
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

> ## Exercise 1: Evaluate if two strings have equal length
> Fill in the blanks to evaluate if the following strings have equal lengths.
> ~~~
> str1="ACGT"
> str2="GATAKA"
> 
> __ ___(____) != ___(____):
>       print("Strings does not have equal length")
> ~~~
> {: .language-python}
>   
> 
{: .language-python}
> > ## Solution
> > ~~~
> > if len(str1) != len(str2):
> >       print("Strings does not have equal length")
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
> str1="ACGTAC"
> str2="GATAKA"
distance=0
    for char1, char2 in zip(str1, str2):
        # If the characters are different, increment the distance
        if char1 != char2:
            distance += 1
~~~
{: .language-python}

            
## Functions
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

> ## Exercise 1: Sort the function to count the nucleotides in a string
>  ~~~
>   return nucleotide_counts  
>    nucleotide_counts = {'A': 0, 'C': 0, 'G': 0, 'T': 0}
>
>      if nucleotide in nucleotide_counts:
>    for nucleotide in sequence:
>            nucleotide_counts[nucleotide] += 1
>
>     def calculate_nucleotide_frequency(sequence):
>  ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> >     def calculate_nucleotide_frequency(sequence):
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

> ## Exercise 2: Evaluate the number of nucleotides in a string 
>
>  
> > ## Solution
> >
> > 
> {: .solution}
{: .challenge}


Let's assume that "population" is a numpy ndarray with genomes as rows.
~~~
def calculate_hamming_matrix(population):
    # Number of genomes
    num_genomes = population.shape[0]
    # Create an empty matrix for Hamming distances
    hamming_matrix = np.zeros((num_genomes, num_genomes), dtype=int)
   # Calculate the Hamming distance between each pair of genomes
    for i in range(num_genomes):
        for j in range(i+1, num_genomes):  # j=i+1 to avoid calculating the same distance twice
            # The Hamming distance is multiplied by the number of genes to convert it into an absolute distance
            distance = hamming(population[i], population[j]) * len(population[i])
            hamming_matrix[i, j] = distance
            hamming_matrix[j, i] = distance  # The matrix is symmetric
    
    return hamming_matrix
~~~
{: .language-python}


Apart from the built-in functions and the library functions you can make your own functions, first you define them and then you use them. To define a function you need to give it a name, say what information you need to feed to it, and what output you want.

The function hamming_distance() takes two parameters: str1 and str2, which are the two strings for which the Hamming distance is to be calculated.
We first check if the lengths of the two strings are equal. If they are not equal, we raise a ValueError because the Hamming distance is only defined for strings of equal length.
We initialize a variable distance to store the Hamming distance.
We then iterate over the characters of the two strings using the zip() function, which pairs corresponding elements of the two strings together.
For each pair of characters, if they are different, we increment the distance variable.
Finally, we return the calculated Hamming distance.
You can use this function to calculate the Hamming distance between any two strings in Python.
