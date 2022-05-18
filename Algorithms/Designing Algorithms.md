# Designing Algorithms
keywords: #algodesign #foundations  

### Incremental Approach
An incremental algorithm is **given a sequence of input**, and finds a sequence of solutions that build incrementally while adapting to the changes in the input. ... We define general incremental formulations of covering and packing problems, and give incremental algorithms for such classes of problems.

### Divide and Conquer
Many useful algorithms are recursive in structure: to solve a given problem, they call themselves recursively one or more times to deal with closely related subproblems.

divide and conquer algos running time is ez to anaylze

It is about dividing the problems into subproblem and deal with individually

The divide-and-conquer paradigm involves three steps at each level of the recursion:
- **Divide** the problem into a number of subproblems that are smaller instances of the same problem
- **Conquer** the subproblems by solving them recursively. If the subproblem sizes are small enough, however, just solve the subproblems in a straightforward manner
- **Combine** the solutions to the subproblems into the solution for the original problem.

### [[Designing Algorithms Exercises]]