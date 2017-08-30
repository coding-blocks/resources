---
layout: post
title:  "Datatypes in Python"
categories: [Python]
tags: python hackerblocks competitive-coding
vidId: dUY1IFl_hhE
img: 
---


Datatypes in Python


Video Explanation by **Prateek Narang**

#### **Difficulty**: 
Easy

#### **Concepts Used**:
Basics

**Solution**


# DataTypes

```python
# Integers
a = 10
b = 20034L
c = 34.5
d  = 5 + 4j
e =  2 + 6j

print (a*a + b)
print type(b)
print type(c)
print type(d)

print d  + e

# String

name = "Coding Blocks"

lang = """We are learning python"""

print lang,"at",name

```

    20134
    <type 'long'>
    <type 'float'>
    <type 'complex'>
    (7+10j)
    We are learning python at Coding Blocks
    


```python
# Read only string, I can't update a string
myString = "Hello World"

print len(myString)

#myString[2] = 'm'
print myString[2]

# Slicing in Strings
print myString[0:3]
print myString[:2]
print myString[3:]


```

    11
    l
    Hel
    He
    lo World
    