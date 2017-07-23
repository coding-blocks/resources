---
layout: post
title:  "Sanjay's New Job - using STL Comparator"
categories: c++ hackerblocks competitive-coding
vidId: 4Gs-urq8UwE
img: 
---


Sanjay's New Job problem based on Sorting concepts.

Read and Try **Sanjay's New Job Problem** first yourself.
[Try now at **HackerBlocks**](https://hack.codingblocks.com/practice-section/p/66/90)


#### **Difficulty**: 
Easy

#### **Concepts Used**:
Sorting, STL, Comparator

#### **Statement**:
Given a list of employees and their salaries, we have to sort them in decreasing order of salaries and if two employees have same salary then they should be sorted lexicographically by name.



**Tester's Solution**
by Prateek Narang

```c
#include<iostream>
#include<algorithm>
#include<cstring>
using namespace std;

bool myCompare(pair<string,int> p1,pair<string,int> p2){
    ///first = Name, second = Salary
    /// Preference Salary > Name

    if(p1.second==p2.second){
        return p1.first < p2.first;
    }

    return p1.second > p2.second;
}

void Sort(emp[]){
    for(int i=0;i<n;i++){
        if( myCompare(emp[i],emp[i+1])){
            swap(emp[i],emp[i+1]);
        }

    }

}


int main(){
    int min_salary,n;
    pair<string,int>  emp[100005];
    cin>>min_salary;
    cin>>n;


    string name;
    int salary;

    for(int i=0;i<n;i++){
        cin>>name>>salary;
        emp[i].first = name;
        emp[i].second = salary;
    }

    sort(emp,emp+n,myCompare);

    ///Print
    for(int i=0;i<n;i++){

        if(emp[i].second>=min_salary){
        cout<<emp[i].first <<" "<<emp[i].second<<endl;
        }
    }




return 0;
}
```
