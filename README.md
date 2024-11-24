# CI2024_Lab03
Repository with code developed to solve the n-puzzle.\
The main file is `nPuzzle.ipynb`. The `Lab03.ipynb` file is a secondary file where two alternative strategies were developed, but they have shoved to be not the optimal ones.

## nPuzzle.ipynb
This file includes two different algorithm able to solve the **n puzzle**:
- Bi-Directional Search
  This algorithm grows two different trees:
  - A tree origination from the root node;
  - A tree originationg from the solution.
  The trees are expanded computing, for each node, all possible moves,
  unless they have already been visited once, in that tree.

  When a common configuration is found in both tress, the solution path is computed 
  concatenating the two trees on the common node (the one evolving from the solution is reversed,    in order to have a proper path, from the initial configuration to the solution).

  **_pros_:** This algorithm can found a solution made of minimal steps, since it computes all the  possible evolutions for all nodes, from both the initial configuration and the solution.

   **_cons_:** Since this strategy is *complete* it requires a lot of memory and computational time. The algorithm proved to be suited to solve efficently puzzle with dimension of **2** or **3**, in a short time. When the dimension grows, the time required becomes very large. 
