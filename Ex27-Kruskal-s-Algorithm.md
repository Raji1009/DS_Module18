# Ex27: Kruskal’s Algorithm  
## DATE: 19.04.2024  

## AIM:  
To write a C program to implement Kruskal's Algorithm for finding the Minimum Cost of a Spanning Tree.

## Algorithm:

1. Create an edge list of all edges from the input graph.
2. Sort the edge list in ascending order of weights.
3. Initialize a parent array for Union-Find operations to detect cycles.
4. For each edge (u, v):
    - If `find(u)` ≠ `find(v)` (i.e., no cycle), include the edge in MST.
    - Perform union of `u` and `v`.
5. Repeat step 4 until MST has (V - 1) edges.
6. Print the edges included and total minimum cost.

## Program:

```c
/*
Program to implement Kruskal's Algorithm
Developed by: Rajalakshmi R
Register Number: 212223110037
*/

#include <stdio.h>

#define MAX 30

typedef struct {
    int u, v, w;
} Edge;

Edge edgeList[MAX], result[MAX];
int parent[MAX];
int n, e;

int find(int i) {
    while (parent[i])
        i = parent[i];
    return i;
}

int unionSets(int i, int j) {
    if (i != j) {
        parent[j] = i;
        return 1;
    }
    return 0;
}

void kruskal() {
    int i, j, u, v, count = 0, totalCost = 0;

    for (i = 0; i < e - 1; i++) {
        for (j = 0; j < e - i - 1; j++) {
            if (edgeList[j].w > edgeList[j + 1].w) {
                Edge temp = edgeList[j];
                edgeList[j] = edgeList[j + 1];
                edgeList[j + 1] = temp;
            }
        }
    }

    for (i = 0; i < e; i++) {
        u = find(edgeList[i].u);
        v = find(edgeList[i].v);

        if (unionSets(u, v)) {
            result[count++] = edgeList[i];
            totalCost += edgeList[i].w;
        }

        if (count == n - 1)
            break;
    }

    printf("\nEdges in the Minimum Spanning Tree:\n");
    for (i = 0; i < count; i++) {
        printf("%d - %d : %d\n", result[i].u, result[i].v, result[i].w);
    }
    printf("\nMinimum cost = %d\n", totalCost);
}

int main() {
    int i;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter number of edges: ");
    scanf("%d", &e);

    printf("Enter edges (u v w):\n");
    for (i = 0; i < e; i++) {
        scanf("%d %d %d", &edgeList[i].u, &edgeList[i].v, &edgeList[i].w);
    }

    kruskal();
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/8aa5c50e-3ae9-4830-9b14-b244ab91771a)




## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.
