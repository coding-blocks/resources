---
layout: post
title:  "Binary Search"
categories: c++ binarysearch
vidId: 8er8Bzd6uhs
img: 
---

### Binary Search Algorithm - Binary Search is simple yet efficient algorithm for searching an element is a sorted array. In this video, Prateek bhayia explains the logic and implementation of Binary Search.

```c
#include<iostream>
using namespace std;


int main(){

    ///Create an array and initialise
    int a[100] = {1,3,3,3,10,12};
    int n = 6; ///Given in the Question
    ///Input the key
    int key;
    cin>>key;

   ///Binary Search
   int s=0;
   int e = n-1;
   int mid;

   while(s<e){
        mid = (s+e)/2;

        if(a[mid]==key){
            cout<<"Found at index"<<mid;
            break;
        }
        else if(a[mid]>key){
            e = mid - 1;
        }
        else{
            s = mid + 1;
        }
   }
    if(s>e){
        cout<<"Element doesnt exist"<<endl;
    }

return 0;
}



```
