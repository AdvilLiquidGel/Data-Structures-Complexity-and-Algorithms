# Data Structures Notes

__Lesson 1: Matrices & List Comprehension__

Mathematically, matrix is a representations of numbers, symbols, or expressions in a 2-Dimensional Array.

__Mathematical Matrix Diagram__

![image](https://user-images.githubusercontent.com/129079093/231789697-5293dc66-673c-4bac-b0ab-2ccc6c6387d8.png)

This is a mathematical notation of what a matrix looks like; explanations are as follows:

Let A represent the matrix
Matrix A has m rows and n columns ... in this case 2 rows and 4 columns.

Row 1 has values of 1 2 3 4
Column 2 has values of 2 6

__Matrix A in Python 3__

 ```python 3
 # Python 3 Representation of matrix A

matrix_A = [
    [1, 2, 3, 4],
    [5, 6, 7, 8]
]

# Accessing Matrix A
print('Row 1: %s' % matrix_A[0]) # Recall: Indexing starts at zero in Python
print('Value at Row 2 Column 2: %s' % matrix_A[1][1])
```

Row 1: [1, 2, 3, 4]

Value at Row 2 Column 2: 6

In Python 3, there is no data structure called a "Matrix".

- All rows must have the same number of values
- All columns must have the same number of values
- All items in the 2D List must have the same data types
- Since indexing always starts at 0 ... row 1 is technically located at matrix_A[0]

__List Comprehension in Python 3__

List Comprehension is a concise method to create list in Python 3.

This technique is commonly used when:

The list is a result of some operations applied to all its items
It is a made from another sequence/iterable data
The list is member of another list/sequence/iterable data that satisfies a certain condition

This is where the _lambda_ function would be used

__List Comprehension Example 1__

```python3 # Old Method
squares = []
for i in range(10):
    squares.append(i ** 2)

print('Our result: %s' % squares)
```
Our result: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

```python 3 
# List Comprehension

squares = [i**2 for i in range(10)]

print('Our new result: %s' % squares)
```
Results are the same 

List comprehension consists of:

- A Square Bracket containing an expression that describes the list

- One or more For clause to explain its members

- Then a zero or more if clauses depending on the complexity of the list

__Lesson 2: Map & Filter__

_The Map Function_

The idea of a map function is to apply a function to an iterable data.

Formatting:

map(function_name, sequence)

-- function_name: any function (built-in or selfmade) that returns a desired value of choice

-- sequence: any iterable data type

```python 3
# Example
def square(num):
    ''' squares the given num argument '''
    return num ** 2
# end of square

array = list(range(1,11))
square_array = list(map(square, array))

print('Original Array:', array)
print('Array Squared:', square_array)
```
Original Array: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

Array Squared: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

One thing to note about the map function is that it doesn’t return a specific data type, but rather, an python iterable data. Therefore, after we apply the map function, we just execute a list function on it.
