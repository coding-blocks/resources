---
layout: post
title:  "Search pivot in sorted rotated array | Interview Question"
categories: [Tutorial]
tags: c++ binarysearch
vidId: -MhI4Qtk4KQ
img: 
---

### In this video, you will learn how to use binary search to find pivot in a sorted & rotated array.This is also a popular interview problem.



```c
#include<iostream>
using namespace std;

int findPivot(int a[],int s,int e){
    if(s>e){
        return -1;
    }
    while(s<=e){
        int mid = (s+e)/2;

        ///Current Element is Mid
        if(mid<e&&a[mid]>a[mid+1]){
            return mid;
        }
        ///Prev of current element is mid
        if(mid>s&&a[mid]<a[mid-1]){
            return mid-1;
        }
        if(a[s]>=a[mid]){
            e = mid-1;
        }
        else{
            s = mid + 1;
        }

    }

    return -1;
}

int main(){

    int a[] = {4,5,1,2,3};
    int b[] = {5,6,0,1,2,3};

    cout<<findPivot(b,0,5)<<endl;


return 0;
}

```
