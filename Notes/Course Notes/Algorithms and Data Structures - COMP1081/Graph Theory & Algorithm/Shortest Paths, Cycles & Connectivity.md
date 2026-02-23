### Definitions
#### Walk
- A walk in graph $G$ is a sequence of edges $(v_0v_1, v_1v_2, ..., v_{n-1}v_n)$. We also say that $(v_0, v_1, ..., v_n)$ is a walk in $G$
#### Paths
- A walk where no vertices are repeated
- **Formal Definition:** A walk $(v_0v_1, ..., v_{n-1}v_n)$ in $G$ is a path if all vertices $v_j$ are distinct
##### Circuits (Closed Walks)
- A walk where you start and end at the same vertex
- **Formal Definition:** A walk $v_0, v_1, ..., v_n$ with $v_0=v_n$ 
#### Cycle
- A loop through the graph: Start and end at the same vertex, but don't repeat any other vertices
- **Formal Definition:** A closed walk is a cycle (or simple circuit) if all $v_j$'s in it are distinct except $v_0=v_n$
---
#### Length, Distance & Diameter
###### Length: 
- The length of a path or a cycle is the number of edges in it.
##### Distance ($dist(u,v)$):
- The length of a shortest path from $u$ to $v$ if such a path exists, and $\infty$ otherwise.
###### Diameter:
- The largest distance between two vertices in a graph
---
### Shortest Path Problem
- Finding the path from a given vertex $u$ and a destination vertex $v$ with the smallest possible length (or weight)
---
### Connectivity & Connected Components
#### Undirected Connectivity
- A graph is connected if there is a possible path connecting all possible pairs of vertices
- **Formal Definition:** A graph $G=(V,E)$ is connected if, between every pair of vertices $u, v$, there exists at least one path in $G$
- **Connected Component:** A maximal connected subgraph of $G$
---
#### Theorem: Minimum Number of Components
- **Theorem:** Every graph $G=(V,E)$ contains at least $|V|-|E|$ connected components
- **Usage:** If $G = (V,E)$ is connected then $|E| \geqslant |V| -1$
---
### Eulerian Circuits & Hamiltonian Cycles
#### Eulerian Circuits
- A circuit in graph $G$ where you travel along the edges, starting and finishing at the same vertex, and traverse **_each edge_** exactly once
- Computationally easy to detect Eulerian circuits
#### Hamiltonian Circuits
- A cycle in graph $G$ where you travel along the edges, start and finish at the same vertex, and visit **_each vertex_** exactly once
- Computationally hard to determine Hamiltonian cycles
---
### Travelling Salesman Problem (TSP)
- Where you must visit cities $(c_1, c_2, ..., c_n)$ in some order, visiting each city exactly once and return to the starting point. A positive integer cost $d(i,j)$ is assigned between each neighbouring pair of cities, and the goal is to find the optimal (cheapest) route
#### Reductions: Connecting TSP to Hamiltonian Cycles
1. Let $G$ be a graph with a set of vertices $V$ (where each city is a vertex and the number of vertices is $n$) and a set of edges $E$
2. For every pair of distinct vertices $u$ and $v$, set the travel cost $d(c_u, c_v) = 1$ if there is an edge between them in the original graph, and a cost of $2$ if there is no edge
3. Detecting a Hamiltonian cycle in $G$ can now be viewed as a TSP. If $G$ has a Hamiltonian Cycle, the salesman's route will have a total cost of exactly $n$
4. If there is a route of cost $n$, it means the salesman never had to use a "fake" road with a cost of 2. Therefore, they only travelled along real edges of $G$, perfectly outlining a Hamiltonian cycle
---
$\underline{\textbf{Related Pages: }}$
- [[Intro to Graph Theory]]