# Ex30: Finding Total Cost of Spanning Tree  
## DATE: 23.04.2025 

## AIM:  
To write a C Program to implement Prim's Algorithm for finding the total cost of a minimum spanning tree (MST).

## Algorithm:

1. Start with a weighted undirected graph represented as an adjacency matrix.
2. Choose an arbitrary vertex to start the MST.
3. Find the edge with the minimum weight that connects a vertex in the MST to one outside the MST.
4. Add that edge and its cost to the MST.
5. Repeat until all vertices are included in the MST.
6. Display the edges and compute the total cost.

## Program:

```c
/*
Program to implement Prim's Algorithm for finding Total Cost of Spanning Tree
Developed by: Rajalakshmi R
RegisterNumber: 212223110037
*/

#include <stdio.h>
#define INF 9999
#define MAX 20

int main() {
    int G[MAX][MAX], visited[MAX] = {0}, n;
    int i, j, min, u, v, ne = 1, total_cost = 0;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &G[i][j]);

    visited[0] = 1;

    printf("\nEdges in the Minimum Spanning Tree:\n");
    while (ne < n) {
        min = INF;
        for (i = 0; i < n; i++) {
            if (visited[i]) {
                for (j = 0; j < n; j++) {
                    if (!visited[j] && G[i][j]) {
                        if (G[i][j] < min) {
                            min = G[i][j];
                            u = i;
                            v = j;
                        }
                    }
                }
            }
        }

        visited[v] = 1;
        printf("Edge %d: (%d -> %d) cost = %d\n", ne++, u, v, min);
        total_cost += min;
    }

    printf("\nTotal cost of Minimum Spanning Tree = %d\n", total_cost);
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/400b7cc7-a4bd-428b-bd07-6aba17f7a95c)



## Result:
Thus the C program to implement Prim's Algorithm for finding Total Cost of spanning tree is implemented successfully.
