# Lab 2: Welcome to Python! + Data Structures

## Overview

Welcome to your first (or perhaps second) lab! Labs in CS41 are designed to be your opportunity to experiment with Python and gain hands-on experience with the language.

The primary goal of the first half is to ensure that your Python installation process went smoothly, and that there are no lingering Python installation bugs floating around.

The second half focuses more on using data structures to solve some interesting problems.

You're welcome to work in groups or individually. Remember to have some fun! Make friends and maybe relax a little too. If you want to cue up any songs to the playlist, let us know!

**Note: These labs are *designed* to be long! You shouldn't be able to finish all the problems in one class period. Work through as much as you can in the time allotted, but also feel free to skip from question to question freely. The extra problems are intended to be extra practice, if you want to hone your Python skills even more.**

Above all, have fun playing with Python! Enjoy.

## Warming Up

### Hello World

If you haven’t already, write a Hello World program which consists of getting Python to print `"Hello, World!"` to the console. First, write this program using the interactive interpreter. Next, put the body of the program into a file named `hello.py`, and run the Hello World program as a Python script.

### Printing

Write a program using `print()` that, when run, prints out a tic-tac-toe board.

```
  |  |
--------
  |  |
--------
  |  |  
```

*Hint: you may find the optional arguments to `print` useful. You can read about them [here](https://docs.python.org/3.4/library/functions.html#print)*

### Printing #2 (challenge)

Write a program that, when run, prints out a SUPER tic-tac-toe board.

```
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
========+========+========
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
========+========+========
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
```

You'll find that there may be many ways to solve this problem. Which do you think is the most 'pythonic?' Talk to someone next to you about your approach to this problem. Remember the Zen of Python!

### Fizz, Buzz, FizzBuzz!
If we list all of the natural numbers under 41 that are a multiple of 3 or 5, we get

```
 3,  5,  6,  9, 10, 12, 15,
18, 20, 21, 24, 25, 27, 30,
33, 35, 36, 39, 40
```

The sum of these numbers is 408.

Find the sum of all the multiples of 3 or 5 below 1001.

### Collatz Sequence
Depending on who you took CS106A from, you may have seen this problem before.

The *Collatz sequence* is an iterative sequence defined on the positive integers by:

```
n -> n / 2    if n is even
n -> 3n + 1   if n is odd
```

For example, using the rule above and starting with 13 yields the sequence:

```
13 -> 40 -> 20 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1
```

It can be seen that this sequence (starting at 13 and finishing at 1) contains 10 terms. Although unproven, it it hypothesized that all starting numbers finish at 1.

What is the length of the longest chain which has a starting number under 1000?

*NOTE: Once the chain starts the terms are allowed to go above one thousand.*

Challenge: Same question, but for any starting number under 1,000,000 (you may need to implement a cleverer-than-naive algorithm)

### Fahrenheit-to-Celsius converter
Write a program to convert degrees Fahrenheit to degrees Celcius by (1) asking the user for a number (not necessarily integral) representing the current temperature in degrees Fahrenheit, (2) converting that value into the equivalent degrees Celsius, and (3) printing the final equivalent value.

For example, your program should be able to emulate the following sample run:

```
Temperature F? 212
It is 100.0 degrees Celsius.

Temperature F? 98.6
It is 37.0 degrees Celsius.

Temperature F? 10
It is -12.222222222222221 degrees Celsius.
```

Want to be fancy (challenge)? Try to print the final temperature to two decimal places. *Hint: Take a look at the [`round()`](https://docs.python.org/3.4/library/functions.html#round) function. Isn't Python great?*


## Investigating Data Structures

*[Optional Reading on Standard Types - check out Sequence types and Mapping types](https://docs.python.org/3.4/library/stdtypes.html)*

### Lists
Type the following lines at your Python interactive interpreter and see if they match what you expect:

```
s = [0] * 3
s[0] += 1
print(s)

s = [''] * 3
s[0] += 'a'
print(s)

s = [[]] * 3
s[0] += [1]
print(s)
```

Why is this happening? Consider using the `id` function to investigate further. What happens when we replace the second-to-last line with `s[0] = s[0] + [1]`?

### Tuples

Write a function to compute the [GCD](https://en.wikipedia.org/wiki/Greatest_common_divisor) of two numbers.

```
def gcd(a, b):
    pass  # Your implementation here
    
gcd(10, 25) # => 5
gcd(14, 15) # => 1
gcd(3, 9) # => 3
gcd(1, 1) # => 1
```

You can assume that `a < b` if you'd like.

You should be able to reasonably accomplish this in three lines of Python code (fewer if you're really clever). Try to exploit tuple packing and unpacking!

*Note: don't use the `gcd` in the standard library!*

### Dictionaries
In class, we saw a (naive) implementation of a dictionary comprehension that swaps the keys and values in a dictionary:

```
{value: key for key, value in dictionary.items()}
```

However, this approach will fail when there are two keys in the dictionary with the same value.

Write a function that properly reverses the keys and values of a dictionary - each key (originally a value) should map to a set of values (originally keys) that mapped to it. For example,

```
flip_dict({"CA": "US", "NY": "US", "ON": "CA"})
# => {"US": {"CA", "NY"}, "CA": {"ON"}}
```

### Comprehensions

*Read*

Predict the output of each of the following list comprehensions. After you have written down your hypothesis, run the code in an interactive interpreter to see if you were correct. If you were incorrect, discuss with a partner why Python returns what it does.

```
[x for x in [1, 2, 3, 4]]
[n - 2 for n in range(10)]
[k % 10 for k in range(41) if k % 3 == 0]
[s.lower() for s in ['PythOn', 'iS', 'cOoL'] if s[0] < s[-1]]

# Something is fishy here. Can you spot it?
arr = [[3,2,1], ['a','b','c'], [('do',), ['re'], 'mi']]
[el.append(el[0] * 4) for el in arr]  # What does this return?
# What is the content of `arr` at this point?

[letter for letter in "pYthON" if letter.isupper()]
{len(w) for w in ["its", "the", "remix", "to", "ignition"]}
```

*Write*

Write a comprehension to transform the input data structure into the output data structure

```
[0, 1, 2, 3] -> [1, 3, 5, 7]
[3, 5, 9, 8] -> [True, False, True, False]
["TA_sam", "TA_guido", "student_poohbear", "student_htiek"] -> ["sam", "guido"]

['apple', 'orange', 'pear'] -> ['A', 'O', 'P']
['apple', 'orange', 'pear'] -> ['apple', 'pear']
['apple', 'orange', 'pear'] -> [('apple', 5), ('orange', 6), ('pear', 4)]

['apple', 'orange', 'pear'] -> {'apple': 5, 'orange': 6, 'pear': 4}
```

### Cyclone Phrases (challenge)

Cyclone words are words that have a sequence of characters in alphabetical order when following a cyclic pattern. 

For example:

![Image](http://i.stack.imgur.com/4XBV3.png)


Write a function that to determine whether an entire phrase passed into a function is made of cyclone words. You can assume that all words are made of only alphabetic characters, and are separated by whitespace.

```
is_cyclone_phrase("adjourned") # => True
is_cyclone_phrase("settled") # => False
is_cyclone_phrase("all alone at noon") # => True
is_cyclone_phrase("by myself at twelve pm") # => False
is_cyclone_phrase("acb") # => True
is_cyclone_phrase("") # => True
```

### Pascal’s Triangle
Write a function that generates the next level of Pascal’s triangle given a list that represents a valid row of Pascal’s triangle.

```
generate_pascal_row([1, 2, 1]) -> [1, 3, 3, 1]
generate_pascal_row([]) -> [1]
generate_pascal_row([1, 4, 6, 4, 1]) -> [1, 5, 10, 10, 5, 1]
```

*Hint: you may find the `zip` function discussed briefly in lecture useful, along with some cleverness.*

### Triangle Numbers
The nth term of the sequence of triangle numbers is given by 1 + 2 + ... + n = n(n+1) / 2. For example, the first ten triangle numbers are: `1, 3, 6, 10, 15, 21, 28, 36, 45, 55, ...`

By converting each letter in a word to a number corresponding to its alphabetical position and adding these values we form a word value. For example, the word value for SKY is `19 + 11 + 25 = 55` and 55 is a triangle number. If the word value is a triangle number then we shall call the word a triangle word.

Using either `/usr/share/dict/words` or `http://stanfordpython.com/words`, a 2.5M text file containing over 200 thousand English words, which are triangle words? As a sanity check, we found 16303 distinct triangle words.

*Hint: you can use `ord(ch)` to get the integer ASCII value of a character*

## Challenge Problems

*Only attempt to solve these challenge problems if you've finished the rest of the lab.*

### Polygon Collision

Given two polygons in the form of lists of 2-tuples, determine whether the two polygons intersect.

```
def polygon_collision(poly1, poly2):
    pass
```

Formally, a polygon is represented by a list of (x, y) tuples, where each (x, y) tuple is a vertex of the polygon. Edges are assumed to be between adjacent vertices in the list, and the last vertex is connected to the first. For example, the unit square would be represented by

```
square = [(0,0), (0,1), (1,1), (1,0)]
```

**Note: this is a *hard* problem. Really hard.**

## Done Early?

Skim [Python’s Style Guide](https://www.python.org/dev/peps/pep-0008/), keeping the Zen of Python in mind. Feel free to skip portions of the style guide that cover material we haven't yet touched on in this class, but it's always good to start with an overview of good style.

## Submitting Labs

Alright, you did it! There's nothing to submit for this lab. You're free to leave as soon as you've finished this lab.

*Credit to Puzzling.SE, ProjectEuler and InterviewCake for several problem ideas*

> With <3 by @sredmond