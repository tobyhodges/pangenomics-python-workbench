---
title: "Functions"
teaching: 10
exercises: 10
questions:
- ""

objectives:
- "Use the `if` conditional to decide an action"
- "Use the `for` loop to iterate actions"
- "Create your functions"

keypoints:
- "The conditional `if` evaluate a statement and perform an action"
- "The for loop repeats an action a predetermined number of times"
- "Custom functions can be defined with `def`"
---




## If statements
~~~

   # Check if the strings have equal length
    if len(str1) != len(str2):
        raise ValueError("Strings must have equal length")
~~~
{: .language-python}

Another example
~~~
if char1 != char2:
            distance += 1
~~~
{: .language-python}

## For loops
 # Iterate over the characters of the strings
~~~
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

~~~
def calculate_nucleotide_frequency(sequence):
    nucleotide_counts = {'A': 0, 'C': 0, 'G': 0, 'T': 0}

    for nucleotide in sequence:
        if nucleotide in nucleotide_counts:
            nucleotide_counts[nucleotide] += 1

    return nucleotide_counts
~~~
{: .language-python}

Let's assume that "population" is a numpy ndarray with your genomes as rows.
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
