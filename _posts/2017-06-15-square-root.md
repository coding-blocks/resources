---
layout: post
title:  "Square Root Using Binary Search | Zomato & Amazon Interview Question"
categories: c++ binarysearch
src: https://www.youtube.com/embed/DY9mpb5YLZ4
img: 
---

### In this video, you will learn how to use binary search to find square root of number. Prateek Bhayia from Coding Blocks explains this algorithm along with the code.

### Time Complexity is `O(LogN+p)`
```c
#include<iostream>
using namespace std;

float binarySqRoot(int no,int p=2){

    int s=0,e=no;
    float ans;

    ///Binary Search for Integer Part
    while(s<=e){
        int mid = (s+e)/2;

        if(mid*mid==no){
            ans = mid;
            break;
        }

        if(mid*mid<no){
            s = mid+1;
            ans = mid;
        }
        else{
            e = mid - 1;
        }
    }


    ///Linear Search for the Precision part
    float inc = 0.1;

    for(int i=0;i<p;i++){

        while(ans*ans<=no){
            ans += inc;
        }
        ans  = ans - inc;
        inc = inc/10;
    }
    return ans;
}


int main(){

    // Complexity O(n)
    cout<<binarySqRoot(2,3)<<endl;
    cout<<binarySqRoot(3,3)<<endl;

return 0;
}

```