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
  
- Breadth-first Search, with Limited Steps and Restarts:\
  To reduce the memory usage and to speed up the computations, a second algorithm is proposed.
  - We build only one tree, starting from the suffled puzzle;
  - We expand the tree using breadth-first strategy, but we limit the tree size, using MAX_DEPTH     parameter.
  - If the solution is not reached in MAX_DEPTH steps, we evaluate the best configuartion among     the deepest node, using a specific function;
  - We build a new tree, starting from the best configuration found;
  - We repeat steps 3-4 until we find the solution (or until MAX_STEPS are reached, to stop the     algorithm eventually...)
    - If , while expanding the tree, we cannot reach a new configuration (not already visited),        we restart from step 1
