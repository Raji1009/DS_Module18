# Ex26: Prim’s Algorithm  
## DATE: 17.04.2024

## AIM:  
To write a C program to implement Prim's Algorithm for finding the Total Cost of the Minimum Spanning Tree (MST).

## Algorithm:

1. Start with an arbitrary vertex and mark it as visited.
2. Create a cost matrix from the given graph (replace 0s with a large number like 999 to avoid confusion with actual edges).
3. Select the edge with the minimum cost from the visited vertex set to an unvisited vertex.
4. Add the selected edge to the MST and mark the vertex as visited.
5. Repeat steps 3–4 until all vertices are included in the MST.
6. Finally, output the edges and the total cost.

## Program:

```c
/*
Program to implement Prim's Algorithm
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>

#define MAX 100
#define INF 9999

int main() {
    int cost[MAX][MAX];
    int visited[MAX] = {0};
    int n, i, j;
    int edges = 0, min, a = 0, b = 0, totalCost = 0;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            scanf("%d", &cost[i][j]);
            if (cost[i][j] == 0) {
                cost[i][j] = INF; // Replace 0 with infinity
            }
        }
    }

    visited[0] = 1;

    printf("\nEdges in MST:\n");

    while (edges < n - 1) {
        min = INF;
        for (i = 0; i < n; i++) {
            if (visited[i]) {
                for (j = 0; j < n; j++) {
                    if (!visited[j] && cost[i][j] < min) {
                        min = cost[i][j];
                        a = i;
                        b = j;
                    }
                }
            }
        }

        printf("%d - %d : %d\n", a, b, min);
        totalCost += min;
        visited[b] = 1;
        edges++;
    }

    printf("\nTotal cost of the Minimum Spanning Tree = %d\n", totalCost);

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/59459767-3a8d-4333-9e54-65d980039755)



## Result:
Thus, the C program to implement Prim's Algorithm for finding Total Cost of tree is implemented successfully.
