---
layout: post
title:  "Quicksort - I : Working + Implementation"
categories: [Tutorial]
tags: c++ sorting 
vidId: "8isAsDxcXPo"
img: 
---


In this video, implementation of Quicksort algorithm is discussed.

#### Quicksort Code

```c
#include<iostream>
#include<ctime>
#include<cstdlib>
using namespace std;



int partition(int *a,int s,int e){

    int i=s-1;
    int j = s;
    int pivot = a[e];
    for( ;j<e;j++){
        if(a[j]<=pivot){
            i++;
            swap(a[i],a[j]);
        }
    }
    ///Bring the pivot element to its sorted position
    swap(a[i+1],a[e]);
    return i+1;
}

void quickSort(int *a,int s,int e){
    if(s>=e){
        return;
    }

    int p = partition(a,s,e);
    quickSort(a,s,p-1);
    quickSort(a,p+1,e);
}

int main(){

    int a[] = {3,4,2,5,1,6};

    int n = sizeof(a)/sizeof(int);



    quickSort(a,0,n-1);

    for(int i=0;i<n;i++){
        cout<<a[i]<<" ";
    }

return 0;
}


```



Thank you for Reading !

Keep Coding, Keep Building !

### For more such informative videos, subscribe us on [Youtube](http://youtube.com/c/codingblocksindia)

