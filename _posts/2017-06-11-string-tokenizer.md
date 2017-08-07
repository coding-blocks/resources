---
layout: post
title:  "String Tokenizer-I"
tag: [Tutorial]
categories: c++ strings
vidId:: 5laM0Qwzpq8
img: 
---

### This post is about STL String Tokenizer - strtok() function, which separates a given a string about some given delimiters. The strtok() function internally maintains a static variable to store the the state of string.

```c
#include<iostream>
#include<cstring>
using namespace std;



int main(){

    char str[] = "Hi, I am teaching about strings, in C++!";
    char *ptr;

    ptr = strtok(str," ,");

    while(ptr!=NULL){

        cout<<ptr<<endl;
        ptr = strtok(NULL," ,!");
    }

return 0;
}

```
