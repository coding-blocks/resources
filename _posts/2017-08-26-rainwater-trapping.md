---
layout: post
title:  "Rainwater Trapping"
categories: [Hackerblocks]
tags: c++ hackerblocks competitive-coding
vidId: Uog2Jmyb3iY
img: 
---


Help Ramu in Minimum Cost Problem


Read and Try **Rainwater Trapping** first yourself.
[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/1001/512)


Video Solution by **Prateek Narang**

#### **Difficulty**: 
Medium

#### **Concepts Used**:


**Solution**

```c
#include<iostream>
using namespace std;

int trapWater(int a[],int n){
    int *left = new int[n];
    int *right = new int[n];

    left[0] = a[0];
    for(int i=1;i<n;i++){
        left[i] = max(a[i],left[i-1]);
    }

    right[n-1] = a[n-1];

    for(int i=n-2;i>=0;i--){
        right[i] = max(a[i],right[i+1]);
    }

    int water = 0;
    for(int i=0;i<n;i++){
        water += min(left[i],right[i]) - a[i];
    }

    return water;
}

int main(){

    int b1[] = {1,0,3,2,0,1,2,0,1};
    int b2[] = {1,0,3,2,0,1,2,0,3};

    int n = sizeof(b1)/sizeof(int);

    cout<<trapWater(b2,n)<<endl;



return 0;
}


```
