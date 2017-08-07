---
layout: post
title:  "Upper & Lower Bound | Amazon Interview Question"
categories: [Tutorial]
tags: c++ binarysearch
vidId: dupq6N2U2DI
img: 
---

### In this video, you will learn how to use binary search to find upper and lower bound of a number in a sorted array. This is a popular interview question asked in companies like Amazon.

### Time Complexity is `O(LogN)`

```c
#include<iostream>
using namespace std;

///Compute the first occurence of key
int firstOcc(int a[],int n,int key){
    int s = 0;
    int e = n - 1;

    int ans = -1;

    while(s<=e){
        int mid = (s+e)/2;

        if(a[mid]==key){
            ///Slight change from binary search ( e = mid - 1 ) because we want to find in left part.
            ans = mid;
            e = mid - 1;
        }
        else if(a[mid]>key){
            e = mid - 1;
        }
        else{
            s = mid + 1;
        }
    }
    return ans;
}

///Compute the first occurence of key
int lastOcc(int a[],int n,int key){
    int s = 0;
    int e = n - 1;

    int ans = -1;

    while(s<=e){
        int mid = (s+e)/2;

        if(a[mid]==key){
            ///Slight change from binary search ( e = mid - 1 ) because we want to find in left part.
            ans = mid;
            s = mid + 1;
        }
        else if(a[mid]>key){
            e = mid - 1;
        }
        else{
            s = mid + 1;
        }
    }
    return ans;
}


int main(){

    int a[] = {1,2,2,2,2,4,4};
    int n = 7;
    int key = 2;

    int ans = firstOcc(a,n,2);
    cout<<"First occ of 2 is  "<<ans<<endl;
    cout<<"Last occ of 2 is "<<lastOcc(a,n,2)<<endl;


    cout<<"First occ of 3 is  "<<firstOcc(a,n,3)<<endl;



return 0;
}
```
