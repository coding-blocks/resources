---
layout: post
title:  "N-Queen using Backtracking "
categories: [Tutorial]
tags: c++ recursion bitmasking
vidId: "jFwREev_yvU"
img: 
---


In this video, implementation of N-Queen Problem Backtracking has been discussed.


#### Normal Backtracking Code To Print One Configuration

```c
#include<iostream>
using namespace std;


bool canPlace(char board[][100],int row,int col,int n){

    ///Row mein queen to nahi h
    for(int i=0;i<n;i++){
        if(board[row][i]=='Q'){
            return false;
        }
    }
    ///Col mein queen to nahi h
    for(int i=0;i<n;i++){
        if(board[i][col]=='Q'){
            return false;
        }
    }
    /// Diagonals
    ///Top Left
    int i=row,j=col;
    while(i>=0&&j>=0){
        if(board[i][j]=='Q'){
            return false;
        }
        i--;
        j--;
    }
    ///Top Right
    i=row,j=col;
    while(i>=0 && j<n){
        if(board[i][j]=='Q'){
            return false;
        }
        i--;
        j++;
    }

    return true;
}



bool solveNQueen(char board[][100],int n,int row){
    if(row==n){
        ///Print the board
        for(int x=0;x<n;x++){
            for(int y=0;y<n;y++){
                cout<<board[x][y]<<" ";
            }
            cout<<endl;

        }

        return true;
    }

    ///Rec Case

    ///Try to place the queen in the current row

    for(int pos=0;pos<n;pos++){

            if(canPlace(board,row,pos,n)){
                    board[row][pos]='Q';

                    bool agliQueenRakhPayeKya = solveNQueen(board,n,row+1);
                    if(agliQueenRakhPayeKya==true){
                        return true;
                    }

                    board[row][pos]='.';
            }

    }
    ///Backtracking
    return false;
}

int main(){

    char board[100][100];

    int n;
    cin>>n;

    for(int x=0;x<n;x++){
            for(int y=0;y<n;y++){
                board[x][y]='.';
            }

        }
    solveNQueen(board,n,0);


return 0;
}


```



Thank you for Reading !

Keep Coding, Keep Building !

### For more such informative videos, subscribe us on [Youtube](http://youtube.com/c/codingblocksindia)

