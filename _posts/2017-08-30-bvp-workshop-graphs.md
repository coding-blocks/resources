---
layout: post
title:  "Bhartiya Vidyapeeth Workshop Codes"
categories: [Workshop]
tags: c++ bvp Workshop
image: graphs.jpg
---

Codes from Workshop held at BVP on Graphs, Breadth First Search, Depth First Search and Snakes and Ladder Game

### **Solving Snakes and Ladders using Breadth First Search - Shortest Path Algorithm**
C++ Program to Solve Snakes and Ladders Game
```c
#include<iostream>
#include<list>
#include<queue>
using namespace std;

class Graph{
    int V;
    list<int> *l;

public:
    Graph(int v){
        V = v;
        l = new list<int>[V];
    }

    void addEdge(int u,int v,bool bidir=true){
            l[u].push_back(v);
            if(bidir){
                l[v].push_back(u);
            }
    }
    void printAdjList(){
        for(int i=0;i<V;i++){
            cout<<i<<"->";
            for(int node:l[i]){
                cout<<node<<",";
            }
            cout<<endl;
        }
    }
    void bfs(int src){

        queue<int> q;
        int *dist = new int[V];

        for(int i=0;i<V;i++){
            dist[i] = INT_MAX;
        }

        ///Algorithm
        dist[src] = 0;
        q.push(src);

        while(!q.empty()){
            int node = q.front();
            cout<<node<<" ";
            q.pop();

            for(int child : l[node]){
                if(dist[child]==INT_MAX){
                    dist[child] = dist[node] + 1;
                    q.push(child);
                }
            }
        }

        ///Print Src to All Node Distances
        for(int i=0;i<V;i++){
            cout<<"Dist of "<<i<<" is "<<dist[i]<<endl;
        }

    }
    void bfsPath(int src,int dest){

        queue<int> q;
        int *dist = new int[V];
        int *parent = new int[V];

        for(int i=0;i<V;i++){
            dist[i] = INT_MAX;
            parent[i] = -1;
        }

        ///Algorithm
        dist[src] = 0;
        q.push(src);

        while(!q.empty()){
            int node = q.front();
            //cout<<node<<" ";
            q.pop();

            for(int child : l[node]){
                if(dist[child]==INT_MAX){
                    dist[child] = dist[node] + 1;
                    parent[child] = node;
                    q.push(child);
                }
            }
        }

        ///Print Src to All Node Distances
        int currentNode = dest;
        while(currentNode!=-1){
            cout<<currentNode<<"<--";
            currentNode = parent[currentNode];
        }

    }
};

int main(){

    Graph g(7);
    g.addEdge(1,0);
    g.addEdge(1,2);
    g.addEdge(3,2);
    g.addEdge(3,6);
    g.addEdge(6,0);
    g.addEdge(3,5);
    g.addEdge(4,5);
    g.addEdge(2,4);

    //g.printAdjList();

    //g.bfs(1);
    //g.bfsPath(1,5);
    cout<<endl;
    //g.bfsPath(5,1);

    int board[50] = {0};
    board[2]= 13;
    board[5] = 2;
    board[9] = 18;
    board[18] = 11;
    board[17] = -13;
    board[20] = -14;
    board[24] = -8;
    board[25] = 10;
    board[32] = -2;
    board[34] = -22;

    Graph game(37);
    for(int u=0;u<36;u++){
        for(int dice=1;dice<=6;dice++){
            int v = u  + dice + board[u+dice];
            if(v<=36){
                game.addEdge(u,v,false);
            }
        }
    }

    game.bfsPath(0,36);



return 0;
}


```
### The Snakes and Ladder Game
![SnakeLadder](https://s26.postimg.org/b0eec5fqx/snake.jpg)


### **Depth First Search - Shortest Path Algorithm Code**

```c
#include<iostream>
#include<list>
#include<queue>
using namespace std;

class Graph{
    int V;
    list<int> *l;

public:
    Graph(int v){
        V = v;
        l = new list<int>[V];
    }

    void addEdge(int u,int v,bool bidir=true){
            l[u].push_back(v);
            if(bidir){
                l[v].push_back(u);
            }
    }
    void printAdjList(){
        for(int i=0;i<V;i++){
            cout<<i<<"->";
            for(int node:l[i]){
                cout<<node<<",";
            }
            cout<<endl;
        }
    }

    void dfsHelper(int node,bool *visited){
        cout<<node<<" ";
        visited[node] = true;

        for(int child:l[node]){
            if(!visited[child]){
                dfsHelper(child,visited);
            }
        }

    }
    void dfs(){
        bool *visited = new bool[V]{0};

        for(int i=0;i<V;i++){
            if(!visited[i]){

                dfsHelper(i,visited);
                cout<<endl;
            }
        }

    }

};

int main(){

    Graph g(8);
    g.addEdge(0,1);
    g.addEdge(6,7);
    g.addEdge(2,1);
    g.addEdge(5,1);
    g.addEdge(2,3);
    g.addEdge(2,4);
    g.addEdge(4,5);

    g.dfs();




return 0;
}

```

