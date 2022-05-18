# Dynamic Programming
keywords: #algorithms #advanceddesingandanalysistechniques

Index
- [[Dynamic Programming Exercises]]

### DP Four Step Sequence
- Characterize the structure of an optimal solution
- Recursively define the value of an optimal solution
- Compute the value of an optimal solution
- Construct an optimal solution from computed information

**Dynamic programming relies on subproblems being both independent and overlapping.**

### Elements of Dynamic Programming
In order for DP to apply, for an optimizatin problem, there must be optimal substructure and overlapping subproblems.
memoization might help us take advantage of the overlapping-subproblems property in a top-down recursive approach

##### Optimal Substructure
- First step: characterize the structure of an optimal solution
- A problem exhibits optimal substructure if an optimal solution to the problem contains within it optimal solutions to subproblems

common pattern in discovering optimal substructure:
- You show that a solution to the problem consists of making a choice, such as choosing an initial cut in a rod or choosing an index at which to split the matrix chain. Making this choice leaves one or more subproblems to be solved.
- You suppose that for a given problem, you are given the choice that leads to an optimal solution. You do not concern yourself yet with how to determine this choice. You just assume that it has been given to you.
- Given this choice, you determine which subproblems ensue and how to best characterize the resulting space of subproblems.
- You show that the solutions to the subproblems used within an optimal solution to the problem must themselves be optimal by using a “cut-and-paste” technique. You do so by supposing that each of the subproblem solutions is not optimal and then deriving a contradiction. In particular, by “cutting out” the nonoptimal solution to each subproblem and “pasting in” the optimal one, you show that you can get a better solution to the original problem, thus contradicting your supposition that you already had an optimal solution. If an optimal solution gives rise to more than one subproblem, they are typically so similar that you can modify the cut-and-paste argument for one to apply to the others with little effort.  

Optimal substructure varies across problem domains in two ways:
- how many subproblems an optimal solution to the original problem uses
- how many choices we have in determining which subproblem(s) to use in an optimal solution.

Dynamic programming often uses optimal substructure in a bottom-up fashion. That is, we first find optimal solutions to subproblems and, having solved the subproblems, we find an optimal solution to the problem. Finding an optimal solution to the problem entails making a choice among subproblems as to which we will use in solving the problem


##### Overlapping Subproblems 
The second ingredient that an optimization problem must have for dynamic programming to apply is that the space of subproblems must be “small” in the sense that a recursive algorithm for the problem solves the same subproblems over and over, rather than always generating new subproblems. Typically, the total number of distinct subproblems is a polynomial in the input size. When a recursive algorithm revisits the same problem repeatedly, we say that the optimization problem has overlapping subproblems. 4 In contrast, a problem for which a divide-andconquer approach is suitable usually generates brand-new problems at each step of the recursion.

Dynamic-programming algorithms typically take advantage of overlapping subproblems by solving each subproblem once and then storing the solution in a table where it can be looked up when needed, using constant time per lookup.

It may seem strange that dynamic programming relies on subproblems being both independent and overlapping. Although these requirements may sound contradictory, they describe two different notions, rather than two points on the same axis. Two subproblems of the same problem are independent if they do not share resources. Two subproblems are overlapping if they are really the same subproblem that occurs as a subproblem of different problems.

##### Reconstructing an optimal solution
As a practical matter, we often store which choice we made in each subproblem in a table so that we do not have to reconstruct this information from the costs that we stored.

We're basically caching subproblem solutions so we can reuse them instead of recomputing them every time inefficiently.

##### Longest Common Subsequence 
DNA: a string of molecules called "bases"
bases: adenine, guanine, cytosine, and thymine.
Language: {A, C, G, T} 

DNA strands:
S1: ACCGGTCGAGTGCGCGGAAGCCGGCCGAA 
S2: GTCGTTCGGAATGCCGTTGCTCTGTAAA

- DNA strands are similar if one is a substring of the other.
- Alternatively, we could say that two strands are similar if the number of changes needed to turn one into the other is small.
- Yet another way to measure the similarity of strands S1 and S2 is by finding a third strand S3 in which the bases in S3 appear in each of S1 and S2; these bases must appear in the same order, but not necessarily consecutively.

The longer the strand S3 we can find, the more similar S1 and S2 are. In our example, the longest strand S3 is GTCGTCGGAAGCCGGCCGAA.

Given two sequences X and Y , we say that a sequence Z is a common subsequence of X and Y if Z is a subsequence of both X and Y .