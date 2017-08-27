---
layout: post
title:  "Towers of Hanoi"
categories: [Hackerblocks]
tags: c++ hackerblocks competitive-coding
vidId: LN4Aa_1vScM
img: 
---


Towers of Hanoi Hacker Blocks Problem based on recursion.


Read and Try **Towers of Hanoi** first yourself.
[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/1001/72)


Video Solution by **Prateek Narang**

#### **Difficulty**: 
Easy

#### **Concepts Used**:
Recursion

**Solution**

```c
#include<iostream>
using namespace std;


void towerOfHanoi(int n, char src, char dest, char helper)
{
    if(n==0){
        return;
    }
    towerofHanoi(n-1,src,helper,dest);
    cout<<"Move "<<n<<" disk from "<<src<<" to "<<dest<<endl;
    towerofHanoi(n-1,helper,dest,src);
}


int main()
{ 
    int n; 
    cin>>n;
    towerofHanoi(n,'A','C','B');
    return 0;
}

```
