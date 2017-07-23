---
layout: post
title:  "Binary Search"
categories: c++ binarysearch
vidId: hlPtqv0nU04
img: 
---

C++ for beginners **Bubble Sort** - The O(n^2) sorting algorithm explained with code.

```c
#include<iostream>
using namespace std;


int main(){
    int a[] = {5,4,3,2,1};
    int n = 5;

    ///Bubble Sort
    for(int times=1;times<=n-1;times++){

        ///Iteration from 0 to n-times-1 => Pairwise swapping
        for(int j=0;j<=n-1-times;j++){
            if(a[j]>a[j+1]){
                swap(a[j],a[j+1]);
            }
        }
    }

    ///Print the array
    for(int i=0;i<n;i++){
        cout<<a[i]<<" ";
    }

    return 0;
}


```
