---
layout: post
title:  "Segment Tree Basics"
categories: [Tutorial]
tags: c++ launchpad segment-tree 
vidId: FR5d4V7Z9SE
img: 
---

Segment Tree is a tree like data structure, that allows querying over particular elements in the range. It is based on the idea of divide and conquer, and uses a array for its implementation. The Segment Tree supports the following operations -
    - Build
    - Update a Node
    - Update a Range
    - Query Over Range
The implementation of above functions has been discussed in the video on a specific problem which is called Range Minimum Query.

Note: Above doesn't cover the lazy propagation concept, will be covered in the next video on Segment Trees.


```c
#include<iostream>
#include<climits>
using namespace std;

int query(int *tree,int index,int s,int e,int qs,int qe){
    ///No Overlap
    if(qs>e || qe<s){
        return INT_MAX;
    }
    ///Complete Overlap
    if(qs<=s && qe>=e){
       return tree[index];
    }

    ///Partial Overlap
    int mid = (s+e)/2;
    int leftAns = query(tree,2*index,s,mid,qs,qe);
    int rightAns = query(tree,2*index+1,mid+1,e,qs,qe);

    return min(leftAns,rightAns);
}
void updateRange(int *tree,int index,int s,int e,int rs,int re,int inc){
    ///No Overlap
    if(re< s || rs>e){
        return ;
    }
    ///Leaf Node
    if(s == e){

        tree[index] += inc;
        return;
    }
    int mid = (s + e )/2;
    updateRange(tree,2*index,s,mid,rs,re,inc);
    updateRange(tree,2*index+1,mid+1,e,rs,re,inc);
    tree[index] = min(tree[2*index],tree[2*index+1]);
    return;
}

void updateNode(int *tree,int index,int s,int e,int i,int inc){
    if(i<s||i>e){
        return;
    }
    if(s==e){
        tree[index] += inc;
        return;
    }
    /// i is lying in the range s to e
    int mid = (s+e)/2;
    updateNode(tree,2*index,s,mid,i,inc);
    updateNode(tree,2*index+1,mid+1,e,i,inc);
    tree[index] = min(tree[2*index],tree[2*index+1]);
    return;
}

int queryRangeLazy(int *tree,int *lazy,int index,int s,int e,int rs,int re){
    /// Make pending updates, resolve lazy value first

    if(lazy[index]!=0){
            tree[index] += lazy[index];
            if(s!=e){
                lazy[2*index] += lazy[index];
                lazy[2*index+1] += lazy[index];
            }
            lazy[index] = 0;

    }

     ///No Overlap
    if(re<s || rs>e){
        return INT_MAX;
    }
    ///Complete Overlap
    if(s>=rs && e<=re){

        return tree[index];
    }
    ///Partial Overlap
    int mid = (s+e)/2;
    int left = queryRangeLazy(tree,lazy,2*index,s,mid,rs,re);
    int right = queryRangeLazy(tree,lazy,2*index+1,mid+1,e,rs,re);
    return min(left,right);
}


void updateRangeLazy(int *tree,int *lazy,int index,int s,int e,int rs,int re,int inc){
    /// Make pending updates, resolve lazy value first

    if(lazy[index]!=0){
            tree[index] += lazy[index];
            if(s!=e){
                lazy[2*index] += lazy[index];
                lazy[2*index+1] += lazy[index];
            }
            lazy[index] = 0;

    }
    ///No Overlap
    if(re<s || rs>e){
        return;
    }
    ///Complete Overlap
    if(s>=rs && e<=re){
        tree[index] += inc;
        if(s!=e){
            lazy[2*index] += inc;
            lazy[2*index+1] += inc;

        }
        return;
    }
    ///Partial Overlap
    int mid = (s+e)/2;
    updateRangeLazy(tree,lazy,2*index,s,mid,rs,re,inc);
    updateRangeLazy(tree,lazy,2*index+1,mid+1,e,rs,re,inc);
    tree[index] = min(tree[2*index],tree[2*index+1]);
    return;
}




void buildTree(int *tree,int *a,int index,int s,int e){
    ///Base Case
    if(s==e){
        tree[index] = a[s];
        return;
    }
    if(s>e){
        return;
    }

    ///Recursive Case
    int mid = (s+e)/2;
    buildTree(tree,a,2*index,s,mid);
    buildTree(tree,a,2*index+1,mid+1,e);
    tree[index] = min(tree[2*index],tree[2*index+1]);
}


int main(){

    int a[ ] = {1,-3,2,0,4,5};
    int n = sizeof(a)/sizeof(int);

    int *tree = new int[4*n+1];
    int *lazy = new int[4*n+1];

    ///Init lazy values as ZERO
    for(int i=0;i<4*n+1;i++){
        lazy[i] = 0;
    }

    buildTree(tree,a,1,0,n-1);

    int no_of_queries;
    cin>>no_of_queries;


    while(no_of_queries>0){

        int qs,qe;
        char ch;

        cin>>ch;
        if(ch=='q'){
            cin>>qs>>qe;
            cout<<queryRangeLazy(tree,lazy,1,0,n-1,qs,qe)<<endl;
        }
        else{
            int i,j,inc;
            cin>>i>>j>>inc;
            updateRangeLazy(tree,lazy,1,0,n-1,i,j,inc);
            cout<<"Range Updated "<<endl;
        }

    no_of_queries--;
    }

return 0;
}

```
