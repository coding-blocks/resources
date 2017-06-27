---
layout: post
title:  "Read the Pages - Google Interview Problem"
categories: c++ hackerblocks competitive-coding binarysearch
src: https://www.youtube.com/embed/Ss9ta1zmiZo?list=PLl4Y2XuUavmuDnf7r9Ij7MrdWtc1qvb05
img: 
---



Read and Try **Read Min Pages Problem** first yourself.
[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/66/408)


#### **Difficulty**: 
Intermediate-Advanced

#### **Concepts Used**:
Binary Search

#### **Statement**:
You are given N books, ith of which has Pi pages (Pi <= Pj, if i < j). You have to assign these N books to M students, such that each student has subsegment of books and the maximum number of pages assigned to a student is minimized.
You have to find the maximum number of pages, a student can have in this assignment of books.

**Tester's Solution**
by - Prateek Narang

```c
#include<iostream>
using namespace std;

#define ll long long int

bool isValidConfig(ll books[],ll n,ll k,ll ans){
        
    int students=1;
    ll current_pages = 0;
    
    for(int i=0;i<n;i++){
        
        if(current_pages+books[i]>ans){
            current_pages = books[i];
            students++;
            if(students>k){
                return false;
            }
            
        }
        else{
            current_pages += books[i];
            
        }
    }
    return true;
}

ll binarySearchBooks(ll books[],ll n,ll k){
    
    ll total_pages = 0;
    ll s=0,e=0;
    for(int i=0;i<n;i++){
        total_pages += books[i];
    }
    s = books[n-1];
    
    e = total_pages;
    int finalAns = s;
    
    while(s<=e){
        ll mid = (s+e)/2;
        
        if(isValidConfig(books,n,k,mid)){
            ///true
            finalAns = mid;
            e = mid-1;
            
        }
        else{
            //FALSE
            s = mid + 1;
        }
        
        
    }
    
    return finalAns;
    
}

int main(){
    
    ll n;
    ll k;
    
    cin>>n>>k;
    
    ll books[100005];
    
    for(int i=0;i<n;i++){
        cin>>books[i];
    }
    cout<<binarySearchBooks(books,n,k)<<endl; 
}


```


**Setters's Solution**
by - Nishant Nahata
```c
#include <bits/stdc++.h>
#define ff first
#define se second
#define pb push_back
#define nn 200100
#define mt make_tuple
#define mp make_pair
#define ll long long int
#define db double
#define ldb long double
#define inf 1000000000000000000ll
#define logn 20
#define mod 341550071728321ll
#define mod1 mod
#define mod2 3825123056546413051ll
#define sqr(a) a*1ll*a
#define nullp mp(-1,-1)
#define set0(a) memset(a,0,sizeof a)
#define init(a) memset(a,-1,sizeof a)
#define cmp 1e-11
#define pll pair<ll,ll>
#define pbc pop_back
 
using namespace std;
const ldb pi=3.141592653589793238462643383;

ll p[nn];

int main()
{
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    #ifndef ONLINE_JUDGE
    freopen("input1.txt","r",stdin);
    freopen("output1.txt","w",stdout);
    #endif
    int n,m;
    cin>>n>>m;
    ll l=1,r=0,mid;
    for(int i=0;i<n;i++)
    {
        cin>>p[i];
        r+=p[i];
        l=max(l,p[i]);
    }
    ll sum=r;
    while(l<r)
    {
        mid=l+r>>1;
        int cnt=0;
        ll tmp=0;
        for(int i=0;i<n;i++)
        {
            if(tmp+p[i]>mid)
            {
                cnt++;
                tmp=0;
            }
            tmp+=p[i];
        }
        if(tmp>0)
            cnt++;
        if(cnt<=m)
            r=mid;
        else
            l=mid+1;
    }
    cout<<l<<endl;
    return 0;
}



```



