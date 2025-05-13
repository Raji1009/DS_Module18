# Ex29: Travelling Salesman Problem  
## DATE: 22.04.2025

## AIM:  
To write a C Program to implement the Travelling Salesman Problem (TSP) for finding the shortest path that visits each city exactly once and returns to the starting city.

## Algorithm:

1. Create a cost matrix representing distances between all cities.
2. Generate all possible permutations of cities.
3. For each permutation:
   - Calculate the cost of the tour (including return to the start).
   - Track the minimum cost found.
4. Print the tour with the minimum cost.

## Program:

```c
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>
#include <limits.h>

#define MAX 10

int tsp(int graph[MAX][MAX], int visited[MAX], int pos, int n, int count, int cost, int start) {
    if (count == n && graph[pos][start]) {
        return cost + graph[pos][start];
    }

    int minCost = INT_MAX;

    for (int i = 0; i < n; i++) {
        if (!visited[i] && graph[pos][i]) {
            visited[i] = 1;
            int currCost = tsp(graph, visited, i, n, count + 1, cost + graph[pos][i], start);
            if (currCost < minCost)
                minCost = currCost;
            visited[i] = 0;
        }
    }

    return minCost;
}

int main() {
    int graph[MAX][MAX], visited[MAX] = {0}, n;

    printf("Enter number of cities: ");
    scanf("%d", &n);

    printf("Enter the cost matrix:\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);

    visited[0] = 1;
    int shortestPathCost = tsp(graph, visited, 0, n, 1, 0, 0);

    printf("\nMinimum cost of visiting all cities: %d\n", shortestPathCost);
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/f208cd59-7606-4afa-8815-53ca1680e2df)



## Result:
Thus, the C program to implement Travelling Salesman Problem for finding shortest path is implemented successfully.
