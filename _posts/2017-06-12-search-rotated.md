---
layout: post
title:  "Search an element in sorted & rotated array"
categories: c++ binarysearch
vidId: ctW9Q6Y_Z8k
img: 
---


### Search in sorted & rotated array - interview problem.
### In this video, you will learn how to use binary search to find an element in an array which is sorted and rotated.

### Time Complexity is `O(LogN)`

```c

int search(int a[],int s,int e,int key){
    if(s>e){
        return -1;
    }

    int mid = (s+e)/2;

    if(arr[mid]==key){
        return mid;
    }

    ///Left Part is Sorted
        if(arr[s]<=arr[mid]){
            if(key>=arr[s]&&key<=arr[mid]){
                return search(arr,s,mid-1,key);
            }
            return search(arr,mid+1,e,key);
        }



    ///Right Part is Sorted
    if(key>=arr[mid]&&key<=arr[e]){
            return search(arr,mid+1,e,key);

    }
    else{
        return search(arr,s,mid,key);
    }

}

```
