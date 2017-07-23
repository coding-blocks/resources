---
layout: post
title:  "Dynamic Programming for beginners Online Webinar"
categories: c++ adhoc launchpad
vidId: X7SrnbgqHHs
img: 
---

Online Webinar on Dynamic Programming by Prateek Narang

### Problem Solving Techniques
- Brute Force/ Complete Search
- Divide and Conquer
- Greedy Techniques
- Dynamic Programming


# Dynamic Programming

#### “Those who cannot remember the past are condemned to repeat it.”

Dynamic Programing is all about remembering answers to the sub-problems
you’ve already solved and not solving it again.
```
Writes down "1+1+1+1+1+1+1+1 =" on a sheet of paper.
"What's that equal to?"
Counting "Eight!"
Writes down another "1+" on the left.
"What about that?"
"Nine!" " How'd you know it was nine so fast?"
"You just added one more!"
"So you didn't need to recount because you remembered the
re were eight! Dynamic Programming is just a fancy way to
say remembering stuff to save time later!"

```

#### Where do we need Dynamic Programming?

 - If you are given a problem, which can be broken down into smaller sub-problems.

- These smaller sub-problems can still be broken into smaller ones - and if you manage to find out that there are some over-lappping sub-problems.

- So Dynamic Programming helps us to solve a particular class of problems with the following properties:
  - Optimal Substructure
  - Overlapping Sub-problems


  **Overlapping Subproblems :**
  If a problem has subproblems which are overlapping/same in nature then this is a big hint for dynamic programming.

  **Optimal Substructure :**
  Optimal Substructure Property means if the optimal solution of the given problem can be formed  using optimal solutions of its sub-problems.

### DP Vs Recursion
- Same Problems can be solved with **Recursion** and are based on principle of **Mathematical Induction**. But if the problems have overlapping sub-problems then recursive solutions take more time


### Divide & Conquer VS Dynamic Programming

   We divide the problem in to non-overlapping subproblems and solve them independently. But in case of dynamic programming the subproblems are overlapping in nature.

   - Example of Divide and Conquer - Binary Search, Square Root of a number using Binary Search

   - Example of Dynamic Programming - Computing Nth Fibonacci Number

### DP vs Greedy
Lets discuss it through an example

##### Counting Money Problem
Suppose you want to count out a certain amount of money, using the fewest possible notes or coins.

**Greedy Approach:**
At each step, take the largest possible note or coin that does not
overshoot the sum of money and include it in the solution.

*Example*:
To make Rs 39 with fewest possible notes or coins in Indian Currency.

```Rs 10 note, to make 29
Rs 10 note, to make 29
Rs 10 note, to make 19
Rs 10 note, to make 9
Rs 5 note, to make 4
Rs 2 coin, to make 2
Rs 2 coin, to make 0
```
Total is 4 notes and 2 coins, which is the optimum solution.

**Note**:  For Indian currency, the greedy algorithm, even after demonetization always gives the optimum solution.

#### Is this true for any currency?
Now that Donald Trump is the new President of US, he decides to do
something extraordinary like PM Modi. So he decides to change all the currency notes to 1 dollars, 7 dollars and 10 dollars.
Suppose you went to US and used the same greedy approach to count
minimum numbers of notes and coins in exchange for a Burger which costs $15.

To make $15:

```1 $10 note
   5 $1 notes
   Total = 6 notes
```

####  Can we do better than 6?
$7 + $7 +$1 – Only 3 notes required!

### DP is used in Optimization Problems
Dynamic Programming is typically applied to optimization problems. In
such problems there can be many possible solutions. Each solution has
a value, and we wish to find a solution with the optimal (minimum or
maximum) value. We call such a solution an optimal solution to the
problem.



## Approaching Dynamic Programming

### Top Down Approach

```
I will be an amazing coder. How?

I will work hard like crazy. How?

I'll practice more and try to improve. How?

I'll start taking part in contests. How?

I'll practicing. How?

I'm going to learn programming.
```

This approach is similar to recursion but the computed solutions to subproblems are stored in a table/array so that the overlapping subproblem is not computed again.

####  Top down is Recursion + Memoization
- Dynamic programming is basically, recursion plus
**memoization**

- Recursion allows you to express the    value of a function in terms
of other values of that function.
If you implement your function in a way that the recursive calls
are done in advance, and stored for easy access, it will make
your program faster.
This is what we call **Memoization** - it is memorizing the results
of some specific states, which can then be later accessed to
solve other sub-problems.


### Bottom Up Approach
In Bottom Up, you start with the small solutions and then use these small solutions to build up larger solutions.

```
I'm going to learn programming.

Then, I will start practicing.

Then, I will start taking part in contests.

Then, I'll practice even more and try to improve.

After working hard like crazy,

I'll be an amazing coder.

```

Lets see an example.

### Let us discuss Problems
Multiple Approaches, different time and space complexities.

### Linear DP
1) **Nth Fibonacci Number**
        - Recursive Approach
        - Top Down Approach
        - Bottom Up Approach


2) **Ladders Problem**
      - Recursion
      - Top Down Approach
      - Bottom Up Approach

3) **Min Coins Needed**
      - Recursion
      - Bottom Up
      - DP vs  Greedy Solution


4) **Min Money Needed**
      - Dynamic Programming Approach
      - Solve on `HackerBlocks`

### Two dimensional DP

5) **0-1 Knapsack**
      - Recursion
      - Bottom Up
      - DP vs Greedy solution


6) **Unbounded Knapsack**
      - Recursion
      - Bottom Up


7) **Edit Distance**
     - Recursion
     - Bottom Up - Homework
     - Solve on `Spoj` - EDIST
     http://www.spoj.com/problems/EDIST/

### Solutions

**Ladders Problem**

  ```c
  #include <iostream>
using namespace std;

// Recursion
int ways(int n){

    //Ground
    if(n==0){
        return 1;
    }
    if(n<0){
        return 0;
    }

    int ans = ways(n-1) + ways(n-2) + ways(n-3);
    return ans;

}
// Time O(k Power n)
int ways2(int n,int k){
    if(n==0){
        return 1;
    }
    if(n<0){
        return 0;
    }

    int ans = 0;
    for(int j=1;j<=k;j++){

        ans += ways2(n-j,k);
    }
    return ans;
}
// Top Down DP - Homework

// Bottom Up Dp O(nk)
int waysBU(int n,int k){

    int *dp = new int[n];

    dp[0] = 1;

    for(int step=1;step<=n;step++){
        dp[step] = 0;

        for(int j=1;j<=k;j++){
            if(step-j>=0){
            dp[step] += dp[step-j];
            }

        }
    }
    return dp[n];
}
// Can we do it in O(n) ?
// Try doing it at home.

int main() {
    int n = 4;
    cout<<ways(n)<<endl;
    cout<<ways2(3,2)<<endl;
    cout<<ways2(4,3)<<endl;

    cout<<ways2(5,4)<<endl;
    cout<<waysBU(5,4)<<endl;

return 0;
}



  ```

**Coin Change Problem**

```c
#include <iostream>
#include<climits>
using namespace std;



int coinsNeeded(int coins[],int amount,int n){
    //Base Case
    if(amount==0){
        return 0;
    }

    //Rec Case
    int ans = INT_MAX;

    for(int i=0;i<n;i++){
        // Think about it for 2 mins !
        if(amount-coins[i]>=0){
            int smallerAns = coinsNeeded(coins,amount-coins[i],n);
            if(smallerAns!=INT_MAX){
                ans = min(ans,smallerAns+1);
            }
        }
    }

     return ans;

}
// Bottom Up Dp
int coinsNeededDP(int coins[],int amount,int n){
    int *dp = new int[amount+1];

    for(int i=0;i<=amount;i++){
        dp[i] = INT_MAX;
    }



    dp[0] = 0;
    for(int rupay=1; rupay<=amount;rupay++){

        // Iterate Over Coins
        for(int i=0;i<n;i++){

            if(coins[i]<=rupay){

                int smallerAns = dp[rupay-coins[i]];
                if(smallerAns!=INT_MAX){
                    dp[rupay] = min(dp[rupay],smallerAns + 1);
                }

            }

        }
    }


    return dp[amount];

}



int main() {
    int us_coins[] = {1,7,10};
    int n = 3;
    int amount = 15; // Ans should be 3

    int indian_coins[] = { 1,2,5,10,50};
    int paise = 13;

    cout<<coinsNeeded(us_coins,amount,n)<<endl;
    cout<<coinsNeeded(indian_coins,paise,5)<<endl;

    cout<<"Using DP"<<endl;
    cout<<coinsNeededDP(indian_coins,paise,5)<<endl;
    cout<<coinsNeededDP(indian_coins,39,5)<<endl;




return 0;
}

```
**Knapsack Problem**

```c
#include<iostream>
using namespace std;

int knapsack(int wts[],int prices[],int N,int W){
    ///Base Case
    if(N==0||W==0){
        return 0;
    }

    ///Rec Case
    int inc= 0,exc=0;
    if(wts[N-1]<=W){
        inc = prices[N-1] + knapsack(wts,prices,N-1,W- wts[N-1]);
    }

    exc = knapsack(wts,prices,N-1,W);

    return max(inc,exc);
}

int knapsackDP(int wt[],int price[],int N,int W){
        int dp[100][100] = {0};


        for(int n=0;n<=N;n++){
            for(int w=0;w<=W;w++){

                if(n==0||w==0){
                    dp[n][w] = 0;
                }
                else{
                    int inc=0,exc = 0;
                    if(wt[n-1]<=w){

                        inc = price[n-1] + dp[n-1][w-wt[n-1]];
                    }
                        exc = dp[n-1][w];

                    dp[n][w] = max(inc,exc);

                }

            }
        }
        return dp[N][W];
}





int main(){

    int wts[] = {2, 7, 3, 4};
    int prices[ ] = {5,20,20,10};

    int N = 4;
    int W = 11;
    cout<<knapsack(wts,prices,N,W)<<endl;;

    cout<<knapsackDP(wts,prices,N,W)<<endl;

    return 0;
}

```

**Minimum Money Needed - HackerBlocks**
https://hack.codingblocks.com/contests/c/28/256

```c
#include <iostream>
#include <stdio.h>
using namespace std;
int main()
{
  //freopen("test.txt", "r", stdin);
  //freopen("output.txt", "w", stdout);
  int n,k,b;
  scanf("%d%d",&n,&k);
  b = k;
  int p[k +1];
  int i,j;
  for( i=1; i<=k; i++ )
   scanf("%d",&p[i]);
  int ans[k+1];
  for(i=1; i<=k; i++)
  {
    ans[i] = p[i];
  }
  for(i=2; i<=k; i++)
  {
   for(j=1; j<i; j++)
   {
    if(p[i-j] == -1  || ans[j] == -1)
     continue;
    if(ans[i] == -1)
     ans[i] = ans[j] + p[i-j];
    else
    ans[i] = min(ans[i], ans[j] + p[i-j]);

   }

  }
  if(k==0)
   printf("0\n");
  else
  printf("%d\n",ans[k]);
 return 0;
}

```

**Practice More Problems on www.hackerblocks.com**

![CODING BLOCKS](https://codingblocks.com/img/cb/cblogo.png)
