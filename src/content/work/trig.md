---
title: Automating Sequence Sums with Python
publishDate: 2024-05-14 00:00:00
img: /assets/trig.png
img_alt: Iridescent ripples of a bright blue and pink liquid
description: |
  Learn how to automate the calculation of arithmetic and geometric sequence sums using Python.
tags:
  - Learning
  - Dev
  - Python
---

---


### Introduction

During my trigonometry class today, we were learning how to find the sums of both arithmetic and geometric sequences. Most of the work involved using calculators, and after the 20th problem, I realized I could save a lot of time by writing a Python script to do the calculations for me. When I got home, I created a new Python file and started setting up my problem statements.

---

### Geometric Sequence Sum

The first problem statement focused on geometric sequence sums. The equation for finding the sum of a geometric sequence requires four variables: the first term, the second term, the number of terms in the sequence, and the common ratio. With these variables established, I started writing the script. The equation is as follows:

$ S_n = \frac{a(1 - r^n)}{1 - r} $

where \( S_n \) is the sum of the first \( n \) terms, \( a \) is the first term, \( r \) is the common ratio, and \( n \) is the number of terms.

Here's the code I wrote:

```python
import numpy

def sum_geometric_seq(first_num_in_seq, second_num_in_seq, num_of_terms):
    common_ratio = second_num_in_seq / first_num_in_seq
    numerator = first_num_in_seq * (1 - numpy.power(common_ratio, num_of_terms))
    denominator = 1 - common_ratio
    answer = numpy.round(numerator / denominator)
    return answer

first_num_in_seq = int(input("Give me the first number in your sequence: "))
second_num_in_seq = int(input("Give me the second number in your sequence: "))
num_of_terms = int(input("How many terms do you need to calculate? "))

print(sum_geometric_seq(first_num_in_seq, second_num_in_seq, num_of_terms))
```

After testing, I encountered an error because the `input` function returns a string by default, and you cant perform mathematical operations on strings. Casting the inputs to integers fixed this issue, and the script ran as intended.

---

### Arithmetic Sequence Sum

Next, I moved on to the arithmetic sequence script. This one was a bit more challenging because it required a value from an explicit formula to find the last number in the sequence before calculating the sum. Initially, I created two functions but realized this was unnecessary since the explicit formula was simple enough to include directly in the main function. Here are the two necessary equations:

The explicit formula to find the last term:
\[ l = a + (n - 1) \cdot d \]

The sum of the arithmetic sequence:
\[ S_n = \frac{n(a + l)}{2} \]

where \( l \) is the last term, \( a \) is the first term, \( n \) is the number of terms, and \( d \) is the common difference.

Heres the final script for the arithmetic sequence sum:

```python
def sum_arithmetic_seq(first_num_in_seq, second_num_in_seq, num_of_terms):
    common_dif = second_num_in_seq - first_num_in_seq
    ex_form = first_num_in_seq + (num_of_terms - 1) * common_dif
    answer = (num_of_terms * (first_num_in_seq + ex_form)) / 2
    return answer

print(sum_arithmetic_seq(first_num_in_seq, second_num_in_seq, num_of_terms))
