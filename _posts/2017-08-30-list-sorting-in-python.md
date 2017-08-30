---
layout: post
title:  "Lists and Sorting Python"
categories: [Python]
tags: python hackerblocks competitive-coding
vidId: hKDi3443q78
img: 
---


Lists and Sorting in Python


Video Explanation by **Prateek Narang**

#### **Difficulty**: 
Easy

#### **Concepts Used**:
Basics

**Solution**


```python
# Create a list

l1 = []
print type(l1)

l2 = [1,2,3]
print l2
# Acesss the ith element using l[i]
print l2[1]

l3 = [1,2,5,"Hello"]
l4 = l2 + l3
print l4

# We can the list contructor list is inbuilt class

mylist = list()
mylist.append("apple")
mylist.append("guava")
print len(mylist)
print mylist

# Sorting on lists
numbers = [1,2,4,3,5,6]

# sorted function returns a new list which gets printed, doesnt change the actual list
numbers2 = sorted(numbers)

print numbers2
print numbers

# sort function 
numbers.sort()

print "After sorting numbers", numbers


```

    <type 'list'>
    [1, 2, 3]
    2
    [1, 2, 3, 1, 2, 5, 'Hello']
    2
    ['apple', 'guava']
    [6, 5, 4, 3, 2, 1]
    [1, 2, 4, 3, 5, 6]
    After sorting numbers [1, 2, 3, 4, 5, 6]
    


```python
# Sorting on lists
numbers = [1,2,4,3,5,6]

print sorted(numbers,reverse=True)

# Nested lists 
a = [ 1,2,3,["Four",5,6],[2,3,4]]
print a
print type(a[3][0])   #behaves like a 2-d array

# Concatenations
b = [1,29.0]

print a + b 

b = b*3
print b

# Splicing

numbers = ["zero","one","two","three","four"]

print numbers[1:3]
print numbers[ : ]



```

    [6, 5, 4, 3, 2, 1]
    [1, 2, 3, ['Four', 5, 6], [2, 3, 4]]
    <type 'str'>
    [1, 2, 3, ['Four', 5, 6], [2, 3, 4], 1, 29.0]
    [1, 29.0, 1, 29.0, 1, 29.0]
    ['one', 'two']
    ['zero', 'one', 'two', 'three', 'four']
