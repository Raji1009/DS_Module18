# Ex28: Dijkstra’s Algorithm  
## DATE: 22.04.2025

## AIM:  
To write a C Program to implement Dijkstra's Algorithm to find the shortest path from a given source vertex to all other vertices in a weighted graph.

## Algorithm:

1. Initialize the `distance[]` array to infinity and `visited[]` to 0. Set the source distance to 0.
2. For each vertex:
    - Select the unvisited vertex with the minimum distance.
    - Mark it as visited.
    - Update the distances of its adjacent unvisited vertices if a shorter path is found.
3. Repeat step 2 until all vertices are visited.
4. Print the final shortest distance from the source to all other vertices.

## Program:

```c
/*
Program to implement Dijkstra's Algorithm 
Developed by: Rajalakshmi R
RegisterNumber: 212223110037
*/

#include <stdio.h>

#define MAX 100
#define INF 9999

void dijkstra(int graph[MAX][MAX], int n, int start) {
    int distance[MAX], visited[MAX] = {0};
    int i, j, count, minDist, nextNode;

    for (i = 0; i < n; i++) {
        distance[i] = graph[start][i];
    }
    visited[start] = 1;

    for (count = 1; count < n - 1; count++) {
        minDist = INF;
        for (i = 0; i < n; i++) {
            if (!visited[i] && distance[i] < minDist) {
                minDist = distance[i];
                nextNode = i;
            }
        }

        visited[nextNode] = 1;

        for (i = 0; i < n; i++) {
            if (!visited[i]) {
                if (minDist + graph[nextNode][i] < distance[i]) {
                    distance[i] = minDist + graph[nextNode][i];
                }
            }
        }
    }

    printf("\nShortest distances from source node %d:\n", start);
    for (i = 0; i < n; i++) {
        printf("To %d: %d\n", i, distance[i]);
    }
}

int main() {
    int graph[MAX][MAX], n, i, j, start;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix (use 9999 for no direct path):\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < n; j++) {
            scanf("%d", &graph[i][j]);
        }
    }

    printf("Enter the starting vertex: ");
    scanf("%d", &start);

    dijkstra(graph, n, start);
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/64fb4c05-8edc-4811-9b8f-589d98cdac8b)


## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.
