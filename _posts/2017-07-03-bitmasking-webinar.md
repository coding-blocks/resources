---
layout: post
title:  "Bitmasking LIVE Webinar"
categories: c++ hackerblocks bitmasking codechef codeforces
vidId: "wEZfc6cPC4w"
img: 
---


Concepts of Bitmasking Webinar on Youtube Live taken by **Prateek Narang**. Here are the codes and practice problems from the webinar.


## **_Questions for Practice_** 
(Hints discussed in video)

#### **Unique Number-I** .

[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/66/462)

#### **Unique Number-II** .

[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/66/463)

#### **Unique Number-III** .

[Try now at **HackerBlocks**](https://hack.codingblocks.com/contests/c/66/458)

#### **Tavas and SaDDas**.
[Try now at **CodeForces**](http://codeforces.com/contest/535/problem/B)

#### **Paying Up**.
[Try now at **CodeChef**](https://www.codechef.com/problems/MARCHA1/)





## **_Codes from the Webinar_**:

#### **Count Set Bits** 

Code to count no of set bits in a number.
```c
// Time which is O(No of bits)
int countBits(int n){
    
    int count=0;
    while(n>0){
        count += (n&1);
        n = n>>1;
    }
    return count;
    
}
```

#### **Count Set Bits - Efficient ( n&(n-1) Hack )** 

Code to count no of set bits in a number in O(No of Set Bits).

```c
int countBitsFast(int n){
    
    int count=0;
    while(n){
        count++;
        n = n & (n-1);
    }
    return count;
}

```

#### XOR Swapping

Swap two numbers using XOR

```c
    a = a^b;
    b = a^b;
    a = a^b;
    
```

#### **Get Bit, Set Bit and Clear Bit**


Code to get ith Bit, Set ith Bit and Clear ith Bit efficently using masks.

```c
int getIthBit(int n,int i){
    return (n & (1<<i))!=0?1:0;
}

//Change ith bit of no to 1
void setIthBit(int &n,int i){
    int mask = 1<<i;
    n = (n|mask);
    
}
//Clear the ith bit of no to 0
void clearBit(int &n,int i){
    int mask = ~(1<<i);
    n = n & mask;
}

```

#### **Subset/Subsequece Generation using Bitmasking**

Time Complexity is `O(N*2^N)`

```c
    void filterChars(char *a,int no){
    /// a = "abc" no = 5 -- Output should ac.
    
    int i=0;
    while(no>0){
        (no&1)?cout<<a[i]:cout<<"";
        i++;
        no = no>>1;
    }
    cout<<endl;
    
}
void generateSubsets(char *a){
    //Generate a range of numbers from 0 to 2^n -1
    int n = strlen(a);
    int range = (1<<n) - 1;
    
    for(int i=0;i<=range;i++){
        filterChars(a,i);
    }
    
}

int main(){
    char a[] = "abc";
    generateSubsets(a);

return 0;
}


```

#### **Unique Number-II  HackerBlocks Practice Problem**
Given 2n + 2 numbers where every number is occuring twice except two unique numbers. We have to find the unique numbers efficiently.

```c
void findUnique2(int *a,int n){
    
    int res=0;
    for(int i=0;i<n;i++){
        res = res^a[i];
    }
    // find the rightmost set bit in res
    int i=0;
    int temp=res;
    while(temp>0){
        if(temp&1){
            break;
        }
        i++;
        temp = temp>>1;
    }
    
    int mask = (1<<i);
    
    int firstNo = 0;
    for(int i=0;i<n;i++){
        if((mask&a[i])!=0){
            firstNo = firstNo^a[i];
        }
    }
    
    int secondNo = res^firstNo;
    cout<<firstNo<<endl;
    cout<<secondNo<<endl;
    
}


int main(){
    
    int n,i;
    int a[] = {1,3,5,6,3,2,1,2};
    n = sizeof(a)/sizeof(int);
    findUnique2(a,n);
    
    
    return 0;
    
    
}


```



Thank you for Reading !

Keep Coding, Keep Building !

### For more such informative videos, subscribe us on [Youtube](http://youtube.com/c/codingblocksindia)

