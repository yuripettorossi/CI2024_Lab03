# CI2024_Lab03
Repository with code developed to solve the n-puzzle.\
The main file is `nPuzzle.ipynb`. The `Lab03_tests.ipynb` file is a secondary file where two alternative strategies were developed, but they have showed to be not the optimal ones; you can inspect it, but I suggest you to start with the main one.

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
  - Only one tree is built, starting from the suffled puzzle;
  - The tree is expaned, using breadth-first strategy. The tree depth is limited, setting *MAX_DEPTH* parameter;
  - If the solution is not reached in *MAX_DEPTH* steps, the best configuration, among all the deepest node, is evaluated using a specific *heuristic* function;
  - A new tree is then built, starting from the best configuration found;
  -Steps 3-4 are repeated, until the solution is found (or until MAX_STEPS are reached, to stop the algorithm, eventually);
    - If , while expanding the tree, is not possible to reach a new configuration (not already visited), algorithm restarts from step 1.
    
  This algorithm does not find an optimal solution in term of steps performed (moves computed), but it is designed to try to be time efficent.

  **_pros_:** This algorithm is able to solve the puzzle in a relative short time, when the dimension is lower than 5.

  **_cons_:** This is not a *complete* algorithm, so it is not guaranteed that it finds the solution all the times; for this reason random resets are implemented. When is not possible to find next node, it restart from initail configuration, even if this is not optimal for the computational time.
  Even if the tree depth is limited, the *tree size*, when puzzle dimension is greater than 4,
  is still large, and so the algorithm is still resources demanding.
  The number of moves of the computed solution is way larger than the optimal one.

## Lab03_tests.ipynb
This file includes two alternative algorithms:
- A* Search
- Depth-first Search\

They both showed to be able to solve the puzzle when the dimension is 3. Again, when the puzzle grows in size, they are slow in finding the solution.
These two solution were uploaded in a separated file, just to show the work done, since the *Bi-directional search* compute a solution with lower moves and the *Bredth-first search* is faster when d>=4.
## Edit
After receiving suggestion from reviewer and looking for improvements, the heuristic function, used to estimate the goodness of a puzzle configuration, was improved. Now both the **Bi-Directional Search** and the **A-Star Search** are able to solve the puzzle in a reasonable time. The results achieved using Bi-Directional Search, Limited Depth Breadth-First Search and A* Search are reported in the following section. 

## Results
The table below shows the results achieved by different search algorithms. 
For puzzle with dimension lower than 4, the results are computed as an average of different simulations.
|Algorithm|Puzzle Dimension|Moves|Evaluated States|Execution Time|
|----|----|----|----|----|
|Bi-Directional Search   |d=2 |3 |4 |0.02 s |
|Bi-Directional Search   |d=3 |23  |2395   |0.924 s |
||
|BF Search   |d=2  |4 |6   |0.005 s |
|BF Search   |d=3  |43 |1037   |0.457 s |
|BF Search   |d=4 |90 |19557 |50 s|
|BF Search   |d=5  |357  |----   |---- s|
||
|A* Search|d=2  |3  |3  |0.001 s |
|A* Search|d=3  |21  |190   |0.003 s |
|A* Search|d=4  |80  |8854   |0.364 s |
|A* Search|d=5  |154  |57604   |113 s |
