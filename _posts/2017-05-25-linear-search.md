---
layout: post
title:  "Linear Search"
categories: c++ launchpad
src: https://www.youtube.com/embed/zq93im4zzI4?list=PLl4Y2XuUavmuDnf7r9Ij7MrdWtc1qvb05
img: 
---

Linear Search is simple algorithm used for searching a particular element in an array.

```c
#include<iostream>
using namespace std;

void  selectionSort(int a[],int n){
    for(int i=0;i<=n-2;i++){
    int smallest = i;

    //Find the smallest element
    for(int j=i+1;j<n;j++){
            if(a[j]<a[smallest]){
                smallest = j;
            }
    }
    int temp = a[i];
    a[i] = a[smallest];
    a[smallest] = temp;
   }

}

int main(){
int a[100];
int n;
cin>>n;
for(int i=0;i<n;i++){
    cin>>a[i];
}
selectionSort(a,n);

for(int i=0;i<n;i++){
    cout<<a[i]<<" ";
}
return 0;
}
```