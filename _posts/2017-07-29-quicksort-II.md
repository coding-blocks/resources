---
layout: post
title:  "Quicksort - II : Randomized Quicksort"
categories: [Tutorial]
tags: c++ sorting 
vidId: "v15UqHWbbWk"
img: 
---


This is the continuation of last video on quicksort. In this video, Prateek Bhayia discusses Randomized QuickSort to improve the complexity of quicksort in the worst case to `O(n*Logn)`
    

#### Randomized Quicksort Code

```c
#include<iostream>
#include<ctime>
#include<cstdlib>
using namespace std;


void shuffle(int *a,int s,int e){

    srand(time(NULL));

    int i,j, temp;
    for(int i=e;i>0;i--){
        ///Create one random index
        j = rand()%(i+1);
        swap(a[i],a[j]);
    }
}

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

    int a[] = {1,2,3,4,5,6};

    int n = sizeof(a)/sizeof(int);
    shuffle(a,0,n-1);
    for(int i=0;i<n;i++){
        cout<<a[i]<<" ";
    }
    cout<<endl;


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

