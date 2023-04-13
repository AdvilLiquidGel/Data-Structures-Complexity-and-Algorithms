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

__The Map Function__

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

__Filter Function__

The idea of the filter function is to filter out items from a data set that meets a certain condition.

Formatting:

filter(bool_returning_function, sequence)

-- function: The function name we provide for filter() must be return a boolean value ... should also be able handle the items inside the sequence as its arguments

-- sequence: any iterable data type

```python 3
# Example 3

def isOdd(x):
    ''' isOdd() returns True if x is odd.'''
    return x % 2 != 0

array = list(range(1,101))
odds = list(filter(isOdd, array))

print('Odd Numbers from 1 to 100:', odds)
```
Odd Numbers from 1 to 100: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53, 55, 57, 59, 61, 63, 65, 67, 69, 71, 73, 75, 77, 79, 81, 83, 85, 87, 89, 91, 93, 95, 97, 99]

It is true that this can be done differently, but this was a simplistic use of filter to show we can filter out variables that satisfies condition… aka the condition is True.

__Example Problem: List of Palindromic Numbers__

Our goal in this example program is to create a list of palindromic numbers (numbers that are palindromes) from 1 to 10,000.

```python 3
# Palindromic Numbers from 1 to 10000

def isPalindrome(x):
    ''' isPalindrome returns True if string X is a palindrome.'''
    return x == x[::-1]

array = list(range(1,10000))

palindromic_numbers = list(map(int, filter(isPalindrome, map(str, array))))
print('Palindromic Numbers from 1 to 10,000', palindromicNumbers)
```
Palindromic Numbers from 1 to 10,000 [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 22, 33, 44, 55, 66, 77, 88, 99, 101, 111, 121, 131, 141, 151, 161, 171, 181, 191, 202, 212, 222, 232, 242, 252, 262, 272, 282, 292, 303, 313, 323, 333, 343, 353, 363, 373, 383, 393, 404, 414, 424, 434, 444, 454, 464, 474, 484, 494, 505, 515, 525, 535, 545, 555, 565, 575, 585, 595, 606, 616, 626, 636, 646, 656, 666, 676, 686, 696, 707, 717, 727, 737, 747, 757, 767, 777, 787, 797, 808, 818, 828, 838, 848, 858, 868, 878, 888, 898, 909, 919, 929, 939, 949, 959, 969, 979, 989, 999, 1001, 1111, 1221, 1331, 1441, 1551, 1661, 1771, 1881, 1991, 2002, 2112, 2222, 2332, 2442, 2552, 2662, 2772, 2882, 2992, 3003, 3113, 3223, 3333, 3443, 3553, 3663, 3773, 3883, 3993, 4004, 4114, 4224, 4334, 4444, 4554, 4664, 4774, 4884, 4994, 5005, 5115, 5225, 5335, 5445, 5555, 5665, 5775, 5885, 5995, 6006, 6116, 6226, 6336, 6446, 6556, 6666, 6776, 6886, 6996, 7007, 7117, 7227, 7337, 7447, 7557, 7667, 7777, 7887, 7997, 8008, 8118, 8228, 8338, 8448, 8558, 8668, 8778, 8888, 8998, 9009, 9119, 9229, 9339, 9449, 9559, 9669, 9779, 9889, 9999]

_Explanation_

Function Composition Breakdown

1. string version of the array --> map(str, array)
2. filter out the palindrome --> filter(isPalindrome, string version of the array)
3. remap all values back to integers --> map(int, palindromes)
4. turn the mapped integers iterable back inside a list --> list(palindromicIterables)

How it would looked with multiple defined variables:

array = list(range(1,10000))

str_array = map(str, array)

palindromes = filter(isPalindrome, str_array)

palindromics = map(int, palindromes)

palindromic_numbers = list(palindromes)

__Composition of Functions__

Composition of Functions is the idea of using functions within a function call or apply one function to the result of another function.

__Lesson 3: Tuples__

__What are Tuples?__
Strings and Lists are basic iterable data types that are very similar with key differences:

Strings only allow alphanumeric characters and special symbols to represent text
Lists allow all data types as its items/members
Strings are immutable whereas Lists are mutable
These significant differences cause a headache when you require the following data structure:

It must be immutable
It must allow different datatypes as items
It must be iterable
It must be nestable (much like a list within a list)
All of these are solved with a data structure called: Tuple.

How to use Tuples in Python 3
- Tuples are declared with parenthesis … aka round brackets
- () is an empty tuple
- (50,) is a singleton tuple; the comma is required
- Tuples are sliceable; therefore, indexable using square brackets
- A singleton is an iterable data structure with only single item.

__Tuple Example 1__
```python 3
tup = ('C', ' Java', 'Python')
empty_tup = ()
single_tup = ('Park',)

print(tup)
print(empty_tup)
print(single_tup)
```
('C', ' Java', 'Python')
()
('Park',)

__Tuple Operators__
```python 3
# Concatenation: Joining two tuples
a = (1,2,3)
b = (4,5,6)
concat_result = a + b
print('a+b:', concat_result)


# Repetition: Repeating a list multiple times
c = ('Hi!',)
repet_result = c * 3
print('c*3', repet_result)

# Membership: Check if a value exists in a tuple
d = a + b + c
print('d:', d)
print('\'Hi!\' in d:', 'Hi!' in d)
print('7 in d:', 7 in d)
```
a+b: (1, 2, 3, 4, 5, 6)
c*3 ('Hi!', 'Hi!', 'Hi!')
d: (1, 2, 3, 4, 5, 6, 'Hi!')
'Hi!' in d: True
7 in d: False

__Tuples are Iterable, Indexable, and Sliceable__
```python 3 
# Iteration
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Tuple example items:')
for language in example:
    print(language)
print('--')

# Indexing
print('Index 1:', example[1])
print('Last Value:', example[-1])

# Slicing
print('Backwards:', example[::-1])
print('Every other:', example[::2])
print('From 1 to end:', example[1:])
print('From 1 to 3:', example[1:3])
```
Tuple example items:
C

Java

Python

C#

JavaScript
--
Index 1: Java

Last Value: JavaScript

Backwards: ('JavaScript', 'C#', 'Python', 'Java', 'C')

Every other: ('C', 'Python', 'JavaScript')

From 1 to end: ('Java', 'Python', 'C#', 'JavaScript')

From 1 to 3: ('Java', 'Python')

__Built-in Functions with Tuple__
```python 3
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Length:', len(example))
print('Minimum value:', min(example))
print('Maximum value:', max(example))
print('--')

word = 'Hello'
array = [1,2,3,4]
array_array = [[1],[2,3],[4]]

print('String to Tuple:', tuple(word))
print('List to Tuple:', tuple(array))
print('2D array to Tuple:', tuple(array_array))
print('--')

array_array[0][0] = 'p'
print(array_array)

# Note: don't have mutable data type as items in a tuple ...
```
Length: 5

Minimum value: C

Maximum value: Python
--
String to Tuple: ('H', 'e', 'l', 'l', 'o')

List to Tuple: (1, 2, 3, 4)

2D array to Tuple: ([1], [2, 3], [4])
--
[['p'], [2, 3], [4]]

__Tuple Comprehension__
```python 3
# Tuple of Even values from 1 to 100
even_tup = tuple(i for i in range(1,101) if i % 2 == 0)

print(even_tup)
```
(2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98, 100)

The parentheses were taken for a different functionality in python; therefore, we have to do comprehension like this.

The general format is the exactly the same as list comprehension.

__Tuple & Python: Packing and Unpacking__
```python 3
# Examine the following code

# Packing
var_1 = 2
var_2 = 3
var_3 = 5

prime = var_1, var_2, var_3

print('Packed prime values:', prime)

# Unpacking and Repacking
fib = (0, 1, 1, 2, 3, 5, 8)

fib_0, fib_1, fib_n = fib[0], fib[1], fib[2:]
print('fib_0:', fib_0)
print('fib_1:', fib_1)
print('fib_n:', fib_n)
Packed prime values: (2, 3, 5)
fib_0: 0
fib_1: 1
fib_n: (1, 2, 3, 5, 8)
```
Explanation:

Packing collect multiple variable’s values and assign it to a single variable

Unpacking help us assign certain values from a tuple to different variables

This becomes very useful skill when combined with variable arguments for Function Definition and Function Calls

__Lesson 4: Sets__

__Sets in Python 3

A set is an unordered collection with no duplicate elements in Python 3.

Set is a mathematical way to describe collection of different unique objects.

By following the operations and characteristics of the mathematical set, we can utilizie such data structure in our Python code.

__Using Sets in Python 3__
_How to define a set_
```python 3
# Set definition examples:
example_set1 = {1, 2, 3}
example_set2 = {'h','e','l','l','o'}

print('example_set1:', example_set1)
print('example_set2:', example_set2) # Notice there is only 1 'l'; Also notice the order of the values outputted
print('--')

singleton_set = {7}
empty_set = set() # this is because {} is reversed for a different feature in python 3.

print('Singleton:', singleton_set)
print('Empty Set:', empty_set)
```
example_set1: {1, 2, 3}
example_set2: {'o', 'e', 'h', 'l'}
--
Singleton: {7}
Empty Set: set()

__Basic built-in functions with sets__
```python 3
# Basic Built-in Functions w/ Sets

example_set = set('hello') # set() turns an iterable into a set
print('example_set:', example_set)
print('--')

print('Number of Values:', len(example_set)) # length function
print('Minimum Value:', min(example_set)) # min function
print('Maximum Value:', max(example_set)) # max function
print('--')

# tuple to set
tup = (2,3,5,7)
print('tup to set:', set(tup))

# list to set
array = ['orange']*2 +  ['watermelon', 'apple'] + ['kiwi'] * 10
print('Original Array:', array)
print('list to set:', set(array))
```
example_set: {'o', 'e', 'h', 'l'}

Number of Values: 4

Minimum Value: e

Maximum Value: o

tup to set: {2, 3, 5, 7}

Original Array: ['orange', 'orange', 'watermelon', 'apple', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi']

list to set: {'watermelon', 'orange', 'apple', 'kiwi'}

__Basic Membership Operators__

Membership is one of the key operations with set because:

- A set has no duplicates
- A set’s membership operation is one of the fastest operations compared to strings, lists, or tuples this will be covered more when we look at the concept of: complexity
- By using membership operator, we can be certain a target exists or does not exist in our data
```python 3
# Membership Example
example_set = set('hello')

print("Membership of: \'h\'", 'h' in example_set)
print("Non-Membership of: \'z\'", 'z' not in example_set)
```
Membership of: 'h' True

Non-Membership of: 'z' True

__Accessing Values in a Set__

- Due to its unordered nature of a set, there is no concept of indexing or slicing with a set.
- Set is however iterable.

__Set Comprehension__
```python 3 
# Set Comprehension Example
def isPalindrome(x):
    ''' isPalindrome() returns True if string X is a palindrome '''
    return x == x[::-1]

nums = list(range(1,10000))
palindromic_set = {num for num in nums if isPalindrome(str(num))}

print('Palindromic Numbers Set from 1 to 10000:')
print(palindromic_set)
```
__Ending Notes on sets for Python__
- Sets aren’t sliceable nor indexable
- Sets cannot have sets inside them
- Sets do not have order; nor order of insertion
- Sets cannot guarantee that their values will be in order
- Sets do not record a value’s position

__Lesson 5: Dictionary__

__Dictionary in Python 3__

Dictionary (Associative Array, map, symbol table) is a data type that stores a collection of (key, value) pairs, such that each possible key appears at most once in the collection.

_Common Operations:_

- Adding a pair
- Removing a pair
- Modify an existing pair
- Lookup of a value associated with a particular key

__Defining a Dictionary in Python 3__

Dictionaries also use {} like sets; however, their individual item format is very different.

Each item in a dictionary be a pair of key: value.
```python 3
# Dictionary Example
sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

# There are 3 items: each with their unique addresses and value
# Accessing
print('Sammy dict:', sammy)
print('Username:', sammy['username'])
print('Online Status:', sammy['online'])
print('Follower Count:', sammy['followers'])
```
Sammy dict: {'username': 'sammy', 'online': True, 'followers': 42}

Username: sammy

Online Status: True

Follower Count: 42

__Dictionary Properties__

Each item in a dictionary is a key, value pair.

__Keys__

Keys are unique address for a dictionary value’s location

_Key Properties:_

- Must be immutable (strings, numbers, tuples, frozenset)
- Unique; therefore, two same key values cannot exist in a single dictionary
- NEWEST CREATED ITEM with a duplicate KEY superceeds the previous declaration

__Values__

Values of a dictionary within a key can be any data type.

__Updating a Dictionary__

- We can modify existing values by referencing the key
- We can add new values to a dictionary by creating a new key
- We can overwrite a value at an existing key by referencing and recreating the value for it
```python 3 
# Update Example

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

sammy['followers'] += 10 # We are adding 10 to the value located at key: 'followers'
sammy['verified'] = True # We added a new value at a new key: 'verified'
sammy['username'] = 'SammySammy'

print('Sammy Dict:', sammy)
```
__dict() Constrcutor Dictionary Comprehension__

We can turn other data types to dictionaries.

Also similar to lists, tuples, and sets, dictionaries also support comprehension.

_Note:_

We must specify where the keys are and where the values.
```python 3
# dict() Example

example_data = [
    ('one', 3),
    ('two', 3),
    ('three', 5)
]

data_dict = dict(example_data)
print('data_dict:', data_dict)
print('--')

# Dictionary Comprehension
# Goal: Take string numerals and assign them with their integer square
# - keys : string numerals
# - values: integer squares

example_data2 = ['1', '2', '3', '4', '5']

data2_dict = {x : int(x)**2 for x in example_data2}

print('data2_dict:', data2_dict)
```
data_dict: {'one': 3, 'two': 3, 'three': 5}

data2_dict: {'1': 1, '2': 4, '3': 9, '4': 16, '5': 25}
