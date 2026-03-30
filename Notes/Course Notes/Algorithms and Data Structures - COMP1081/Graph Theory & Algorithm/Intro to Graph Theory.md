### Graphs
- Represents objects as points (vertices) and the relations between pairs of them as connecting lines (edges)
- **Formal Definition:** A graph $G$ is a pair two sets $(V(G), E(G))$, where $V(G)$ is a non-empty set of vertices (or nodes) and $E(G)$ is a set of unordered pairs $\{u,v\}$ with $u,v \in V(G)$ and $u \ne v$, called the edges of $G$
#### Directed Graphs (Digraphs)
- A graph where the edges have directions assigned to them
- **Formal Definition:** Same as a graph, but $E(G)$ is a set of ordered pairs $\{u,v\}$
#### Graph Variations
- **Multi-graphs:** Graphs where multiple edges are allowed between pairs of vertices
- **Pseudo-graphs:** Graphs where edges of the form $uu$, called loops, are allowed
- **Weighted graphs:** Graphs where vertices and/or edges are assigned numerical weights
- **Simple graphs:** The default assumption for this module, these are graphs with no multiple edges and no loops
---
### Terminology
#### Endpoints, Adjacency & Incidence
- Let $G$ be a graph with the edge $uv$
- **Endpoint:** $u$ and $v$ are the endpoints of the edge $uv$
- **Adjacent:** The vertices $u$ and $v$ are neighbours/adjacent
- **Incident:** The edge $uv$ is incident to $u$ and $v$
---
#### Neighbourhood & Degree
###### Neighbourhood
- The set of all vertices that are incident to a particular vertex $v$
- **Formal Definition $N(v)$:** The neighbourhood of a vertex $x \in V$, denoted $N(v)$, is the set of neighbours of $v$: $N(v)=\{u \in V | uv \in E\}$ 
###### Degree
- **Formal Definition $deg(v)$:** The number of neighbours of $v$. $deg(v)=|N(v)|$
- **Notation:** $\delta(G)$ or $\delta$ denotes the smallest degree in $G$, and $\Delta(G)$ or $\Delta$ denotes the largest degree
- **Special Graphs:** A vertex with degree 0 is an **isolated vertex**. A vertex with degree 1 is an **end vertex** or a **pendant vertex**
---
### Subgraphs
- **Formal Definition:** A subgraph $G'=(V',E')$ of $G=(V,E)$ is a graph with $V' \subseteq V$ and $E' \subseteq E$
- **Proper Subgraph:** Where $G' \ne G$
	- A subgraph that consists of some, but strictly _**not all**_, of the vertices and edges from the original graph
- **Spanning Subgraph:** Where  $V' = V$
	- A subgraph that includes every single vertex from the parent graph, although it may not include all of the original edges
- **Induced Subgraph:** Where $E'$ contains all edges of $E$ between vertices of $V'$
	- A subgraph created by selecting a specific group of vertices and retaining every original edge that connects those chosen vertices to one another
---
### Euler's Handshaking Lemma
- **Definition:** Let $G=(V,E)$ be a graph. Then: $$\sum_{v\in V}deg(v)=2|E|$$
- **Explanation:** The sum of degrees is always twice the number of edges. This is because every edge has two endpoints and contributes one to each of their degrees
- **Effect:** In every undirected graph $G$, the number of vertices with an odd degree is even
---
## Classes of Graphs
#### Paths $(P_n)$:
- $P_n$ is the path on $n$ vertices, defined as a graph with a vertex set $V=\{v_1, v_2, ..., v_n\}$ and an edge set $E=\{v_1v_2, v_2v_3, ..., v_{n-1}v_n\}$. It contains exactly $n - 1$ edges
- **Visual Structure ($P_4$):** All nodes sit in a single, straight, unbranching line.
``` Plaintext
(v1) ----- (v2) ----- (v3) ----- (v4)
```
---
#### Cycles ($C_n$)
-  $C_n$ is the cycle on $n$ vertices, defined similarly to $P_n$ but with an additional edge connecting $v_n$ and $v_1$. It contains exactly $n$ edges.
- **Visual Structure ($C_4$):** Nodes form a closed geometric ring
```Plaintext
(v1) -------- (v2)
  |            |
  |            |
(v4) -------- (v3)
```
---
#### $k$-Regular Graphs
- A graph is $k$-regular (or simply regular) if every vertex in the graph has the exact same degree, $k$ (note that any letter could be used for $k$)
**Examples:**
- **Paths $(P_n)$** aren't regular as the end vertices always have a degree of $1$, while the internal vertices have a degree of $2$
- **Cycles $(C_n)$** are always **2-Regular** 
- **Complete Graphs $(K_n)$** are always **($n-1$)-Regular**, as each vertex is connected to $n-1$ nodes
- **Complete Bipartite Graphs $(K_{p,q})$** is regular only if $p=q$
- **Hypercubes $(Q_n)$** are always $n$-regular, as every binary string of length $n$ has exactly $n$ possible bit flips available, so every vertex has $n$ neighbours
---
#### Tournament Graphs
- A diagraph that models a competitive system (like a sports tournament), where the vertices are the teams and a directed edge from vertex $x$ to vertex $y$ indicates that team $x$ wins over (or dominates) team $y$
###### Absolute Winner:
- A team that dominates everyone else (an "unbeatable" team). Visually, this would be a node with outgoing edges pointing to every other vertex in the graph
###### Absolute Loser:
- A team that is dominated by everyone else. Visually, this would be a vertex with only incoming edges coming from every other vertex
###### Example: (Rock-Paper-Scissors)
``` Plaintext
       (Scissors)
        /      ^
       v        \
 (Paper) ---> (Rock)
```
---
#### Complete Bipartite Graphs ($K_{p,q}$)
- $K_{p,q}$ is a complete bipartite graph consisting of two disjoint sets of vertices $p$ and $q$. Every vertex in $p$ is connected to every vertex in $q$, but there are no vertices between edges in the same set
- It has exactly $pq$ edges
- **Visual Structure ($K_{2,3}$):** Nodes are strictly separated into two columns (or rows). Lines only cross between the groups, never within them
```Plaintext
      (p1)            (p2)
     /  |  \        /  |  \
   /    |    \    /    |    \
(q1)   (q2)   (q3)   (q1)   (q2)
```
##### Bipartite Graphs
- A graph is bipartite if and only if we can partition its vertex set into two disjoint vertex sets such that every edge has one endpoint in each set.
- Any subgraph of a complete bipartite graph $K_{p,q}$ is considered a standard bipartite graph
###### The Difference:
- A **Complete Bipartite** graph requires absolutely **_every_** possible cross-connection to exist
- A standard **Bipartite** graph simply requires that **_if_** an edge exists, it must cross between the two sets; it does not need to have all possible connections
---
#### The 2-Colouring Algorithm (Determine if a Graph is Bipartite)
1. **Initial Colour:** Pick any starting vertex and assign it **Colour 1**
2. **Colour Neighbours:** Look at all adjacent vertices and assign them **Colour 2**
3. **Traverse & Alternate:** Move to the newly coloured neighbours and colour all of **_their_** uncoloured neighbours with **Colour 1**
4. **Check for Conflicts:** If any two connected vertices are the same colour, then the graph is **_not Bipartite_**. Otherwise, the graph is **_Bipartite_**
5. **Completeness Check:** If the number of edges in a bipartite graph is exactly equal to $pq$, then the graph is a **Complete Bipartite Graph**
---
### Complete Graphs ($K_n$)
- $K_n$ is a graph that contains all the possible edges between any pair of vertices. The number of edges in a $K_n$ graph is $\binom{n}{2} = \frac{1}{2}n(n-1)$
- **Visual Structure ($K_4$)**: Forms a complete polygon with every possible internal diagonal connecting the nodes
```Plaintext
(v1) -------- (v2)
  |  \      /  |
  |    \  /    |
  |     X      |
  |    /  \    |
  |  /      \  |
(v4) -------- (v3)
```
---
### Hypercubes/n-cubes $(Q_n)$
- A graph where every vertex is represented by a binary string of length $n$ (like $001$, $101$, etc.). With vertices between two vertices only if their binary strings are identical except for one single flipped bit
- **Formal Definition:** The $n$-dimensional hypercube or $n$-cube $Q_n$ (where $n \ge 1$) is the graph with $V=\{(e_1,...,e_n) | e_i \in \{0,1\} (i=1,...,n)\}$, in which two vertices are neighbours if and only if the corresponding rows differ in exactly one entry
- **Visual Structure ($Q_3$):** Visually arranged as a perfect 3D geometric cube, clearly displaying how only one bit flips as you travel along any given edge
```Plaintext
          (010)-----------------(110)
           / |                   / |
         /   |                 /   |
       /     |               /     |
    (011)-----------------(111)    |
      |      |              |      |
      |    (000)------------|----(100)
      |    /                |    /
      |  /                  |  /
      |/                    |/
    (001)-----------------(101)
```
---
#### Proof: All n-cubes are bipartite
- **Goal:** We must give a bipartition of the vertex set of the $n$-cube.
1. **First Set:** Let $V_1$ contain all the vertices with an odd number of 1s in their binary string.
2. **Second Set:** Let $V_2$ contain all vertices with an even (possibly 0) number of 1s.
3. **Verify Partition:** This clearly creates a partition of $V$ into two completely disjoint sets.
4. **Verify Edges:** Because an edge only exists between vertices that differ by exactly one bit (changing a 0 to a 1, or a 1 to a 0), moving along an edge will always change the total count of 1s from odd to even, or from even to odd. Therefore, each edge has one endpoint in $V_1$ and one in $V_2$.
5. **Conclusion:** Because every edge connects $V_1$ to $V_2$, it proves that all $n$-cubes are bipartite.
---
$\underline{\textbf{Related Pages: }}$
- [[Shortest Paths, Cycles & Connectivity]]
- [[Trees & Isomorphism]]
- [[Breadth-First Search]]
