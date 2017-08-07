---
layout: post
title:  "Incredible Hulk- Bitmasking"
categories: [Hackerblocks]
tags: c++ hackerblocks bitmasking
vidId: OQ8WvxOHZo8
img: 
---


Incredible Hulk Problem from HackerBlocks.
Try this Question Now - 
https://hack.codingblocks.com/practice-section/p/66/135



**Solution** 
```c
#include<iostream>
using namespace std;

int computeBits(int n){
    
    int ans = 0;
    while(n>0){
        ans++;
        n = n&(n-1);
    }
    return ans;
    
}


int main() {
    int t,n;
    cin>>t;
    
    while(t--){
        cin>>n;
        cout<<computeBits(n)<<endl;
        
    }
    
        
	return 0;
}


```

Complexity is `O(No of Set Bits)`
