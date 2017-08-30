---
layout: post
title:  "Variables in Python"
categories: [Python]
tags: python hackerblocks competitive-coding
vidId: 1dzylMGzvs4
img: 
---


Variables in Python


Video Explanation by **Prateek Narang**

#### **Difficulty**: 
Easy

#### **Concepts Used**:
Basics

**Solution**


```python
# You can init multiple variable in a single line
a,b,c = 1,2.0, "hello"

print a
print b
print c

```

    1
    2.0
    hello
    


```python
"""This is a multi-line 
comment. Blah blah! 
"""

# You can have a string spread across multiple lines
x = """This is a string and multiline comment 
which i am going to print"""

print x
```

    This is a string and multiline comment 
    which i am going to print
    


```python

a = 10
b = a # b is a referece to a, a is also a reference to integer object which is storing 10

# id of a gives me the address of a
b = b + 1    # b is reference to int object object which is storing 11

print a
print b

print id(a)
print id(b)

myVar = 1

x = y = z = 1
print id(x)
print id(y)
print id(z)
print id(myVar)



```

    10
    11
    37191724
    37191712
    37191832
    37191832
    37191832
    37191832
