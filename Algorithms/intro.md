# Introduction to Algorithms Design

keywords: #algorithms #sort #insertionsort #introtoalgo #algodesign #algo

![[Pasted image 20210722230930.png]]

{Mike, Bob, Sally, Jill, Jan} or {154, 245, 743, 464, 659}

```
insertionSort() {
	int i, j;
	for(i = 1; i < n; i++) {
		j=i;
		while ((j > 0) && (s[j]  < s[j-1])) {
			swap(&s[j], &s[j-1]);
			j = j - 1;
		}
	}
}
```

An animation of the logical flow of this algorithm on a particular instance (the letters in the word “INSERTIONSORT”) is given in Figure 1.1

![[Pasted image 20210722231355.png]]


###  Robot Tour Optimization
![[Pasted image 20210722231558.png]]

Let’s consider a problem that arises often in manufacturing, transportation, and testing applications. Suppose we are given a robot arm equipped with a tool, say a soldering iron. In manufacturing circuit boards, all the chips and other components must be fastened onto the substrate. More specifically, each chip has a set of contact points (or wires) that must be soldered to the board. To program the robot arm for this job, we must first construct an ordering of the contact points so the robot visits (and solders) the first contact point, then the second point, third, and so forth until the job is done. The robot arm then proceeds back to the first contact point to prepare for the next board, thus turning the tool-path into a closed tour, or cycle. Robots are expensive devices, so we want the tour that minimizes the time it takes to assemble the circuit board. A reasonable assumption is that the robot arm moves with fixed speed, so the time to travel between two points is proportional to their distance. In short, we must solve the following algorithm problem:

Problem: Robot Tour Optimization 
Input: A set S of n points in the plane. 
Output: What is the shortest cycle tour that visits each point in the set S?

*sad attempt at solving this, please don't read*

takeaways:  
- robot arm moves in a constant speed v
- time = v/d 

The time to travel between two points is proportional to their distance so being as close to each other as possible is the fastest way and we can achieve that by sorting.

##### *actual solution*
Nearest-neighbor heuristic. Starting from some point p0, we walk first to its nearest neighbor p1. From p1, we walk to its nearest unvisited neighbor, thus excluding only p0 as a candidate. We now repeat this process until we run out of unvisited points, after which we return to p0 to close off the tour.

![[Pasted image 20210722235051.png]]

*pseudo code*
```
NearestNeighbor(P)
			Pick and visit an initial point P[0] from P
			P = P[0]
			i = 0
			While there are still unvisited points
				i++
				select p[i] to be closest unvisited point to p[i-1]
				Visit P[i]
			return to p[0] from p[n-1]
```

However, this algo doesn't actually find the shortest cycle 

This one does

	ClosestPair(P)
			Let n be the number of points in set P
			For i = 1 to n-1 do
					d = infinity
					For each pair of endpoints (s, t) from distinct vertex chains
							if dist(s, t) <= d then Sm = s, tm = t, and d = dist(s, t)
					Connect (sm, tm) by an edge
			Connect the two endpoints by an edge
		
This closest-pair rule does the right thing in the example in Figure 1.3. It starts by connecting ‘0’ to its immediate neighbors, the points 1 and −1. Subsequently, the next closest pair will alternate left-right, growing the central path by one link at a time. The closest-pair heuristic is somewhat more complicated and less efficient than the previous one, but at least it gives the right answer in this example.

enumerating all possible orderings of the set of points, and then select the ordering that minimizes the total length:

OptimalTSP(P)   
		d = ∞   
		For each of the n! permutations Pi of point set P   
				If (cost(Pi) ≤ d) then d = cost(Pi) and Pmin = Pi   
		Return Pmin  

This one works but it's slow so rip  
The guy in the book left us on a clifhanger there and we won't find a solution until we reach page 533. check out the catalog entry for the traveling salesman problem in Section 16.4 (page 533).

#### #Takehomelesson 
There is a fundamental difference between algorithms, which always produce a correct result, and heuristics, which may usually do a good job but without providing any guarantee.

### Selecting the right jobs
Now consider the following scheduling problem. Imagine you are a highly-indemand actor, who has been presented with offers to star in n different movie projects under development. Each offer comes specified with the first and last day of filming. To take the job, you must commit to being available throughout this entire period. Thus you cannot simultaneously accept two jobs whose intervals overlap. For an artist such as yourself, the criteria for job acceptance is clear: you want to make as much money as possible. Because each of these films pays the same fee per film, this implies you seek the largest possible set of jobs (intervals) such that no two of them conflict with each other. For example, consider the available projects in Figure 1.5. We can star in at most four films, namely “Discrete” Mathematics, Programming Challenges, Calculated Bets, and one of either Halting State or Steiner’s Tree. You (or your agent) must solve the following algorithmic scheduling problem: 

Problem: Movie Scheduling Problem 
Input: A set I of n intervals on the line. 
Output: What is the largest subset of mutually non-overlapping intervals which can be selected from I?

*sad attempt at solving this*

takeaways:
- accept jobs in non overlaping periods and make the most money possible
- each film pays pays the same fee per film so basically you need to take the maximum amount of jobs possible
- an interval is {start date, end date}
- set I is {{sd,ed}, {sd, ed},{sd, ed}}

![[Pasted image 20210723020929.png]]

*actual solution*
There's two kinds of solutions, Early job first and shortest job first heuristics.

EarliestJobFirst(I)  
			Accept the earlest starting job j from I which does not overlap any previously accepted job, and repeat until no more such jobs remain.  
			
*(This was actually my solution and it turned out to be not so correct cz taking the first job might prevent you from taking many other jobs if the earliest job was long)*

choosing the shortest jobs first

	ShortestJobFirst(I) 
		While (I ̸= ∅) do 
			Accept the shortest possible job j from I. 
			Delete j, and any interval which intersects j from I.

Again this idea makes sense, at least until we realize that accepting the shortest job might block us from taking two other jobs, as shown in Figure 1.6(r). While the potential loss here seems smaller than with the previous heuristic, it can readily limit us to half the optimal payoff.

![[Pasted image 20210724024807.png]]

The difference between our scheduling and robotics problems are that there is an algorithm which solves movie scheduling both correctly and efficiently. Think about the first job to terminate—i.e. the interval x which contains the rightmost point which is leftmost among all intervals. This role is played by “Discrete” Mathematics in Figure 1.5. Other jobs may well have started before x, but all of these must at least partially overlap each other, so we can select at most one from the group. The first of these jobs to terminate is x, so any of the overlapping jobs potentially block out other opportunities to the right of it. Clearly we can never lose by picking x. This suggests the following correct, efficient algorithm:

	OptimalScheduling(I) 
		While (I ̸= ∅) do 
			Accept the job j from I with the earliest completion date. 
			Delete j, and any interval which intersects j from I.

#### #Takehomelesson 
Reasonable-looking algorithms can easily be incorrect. Algorithm correctness is a property that must be carefully demonstrated.

### Reasoning about Correctness
one of the tools for determining the correctness of an algo is "proof"

A proof consists of:
- precise statement of what you are trying to prove
- set of assumptions that are assumed true
- there is a chain of reasoning which takes you from these assumptions to the statement you are trying to prove
- conclusion with a little square ( ) or QED
	
#### #Takehomelesson 
The heart of any algorithm is an idea. If your idea is not clearly revealed when you express an algorithm, then you are using too low-level a notation to describe it.

### Combinatorial Objects
• Permutations – which are arrangements, or orderings, of items. For example, {1, 4, 3, 2} and {4, 3, 2, 1} are two distinct permutations of the same set of four integers. We have already seen permutations in the robot optimization problem, and in sorting. Permutations are likely the object in question whenever your problem seeks an “arrangement,” “tour,” “ordering,” or “sequence.”

• Subsets – which represent selections from a set of items. For example, {1, 3, 4} and {2} are two distinct subsets of the first four integers. Order does not matter in subsets the way it does with permutations, so the subsets {1, 3, 4} and {4, 3, 1} would be considered identical. We saw subsets arise in the movie scheduling problem. Subsets are likely the object in question whenever your problem seeks a “cluster,” “collection,” “committee,” “group,” “packaging,” or “selection.”

• Trees – which represent hierarchical relationships between items. Figure 1.8(a) shows part of the family tree of the Skiena clan. Trees are likely the object in question whenever your problem seeks a “hierarchy,” “dominance relationship,” “ancestor/descendant relationship,” or “taxonomy.” 

• Graphs – which represent relationships between arbitrary pairs of objects. Figure 1.8(b) models a network of roads as a graph, where the vertices are cities and the edges are roads connecting pairs of cities. Graphs are likely the object in question whenever you seek a “network,” “circuit,” “web,” or “relationship.” 

• Points – which represent locations in some geometric space. For example, the locations of McDonald’s restaurants can be described by points on a map/plane. Points are likely the object in question whenever your problems work on “sites,” “positions,” “data records,” or “locations.” 

• Polygons – which represent regions in some geometric spaces. For example, the borders of a country can be described by a polygon on a map/plane. Polygons and polyhedra are likely the object in question whenever you are working on “shapes,” “regions,” “configurations,” or “boundaries.” 

• Strings – which represent sequences of characters or patterns. For example, the names of students in a class can be represented by strings. Strings are likely the object in question whenever you are dealing with “text,” “characters,” “patterns,” or “labels.”

![[Pasted image 20210725231658.png]]

#Takehomelesson : Modeling your application in terms of well-defined structures and algorithms is the most important single step towards a solution.

### Recursive Objects
• Permutations – Delete the first element of a permutation of {1,...,n} things and you get a permutation of the remaining n − 1 things. Permutations are recursive objects.

• Subsets – Every subset of the elements {1,...,n} contains a subset of {1,...,n − 1} made visible by deleting element n if it is present. Subsets are recursive objects. 

• Trees – Delete the root of a tree and what do you get? A collection of smaller trees. Delete any leaf of a tree and what do you get? A slightly smaller tree. Trees are recursive objects. 

• Graphs – Delete any vertex from a graph, and you get a smaller graph. Now divide the vertices of a graph into two groups, left and right. Cut through all edges which span from left to right, and what do you get? Two smaller graphs, and a bunch of broken edges. Graphs are recursive objects. 

• Points – Take a cloud of points, and separate them into two groups by drawing a line. Now you have two smaller clouds of points. Point sets are recursive objects. 

• Polygons – Inserting any internal chord between two nonadjacent vertices of a simple polygon on n vertices cuts it into two smaller polygons. Polygons are recursive objects. 

• Strings – Delete the first character from a string, and what do you get? A shorter string. Strings are recursive objects.

## Exercises

### Finding counterexamples

1.1) Show that a + b can be less than min(a, b).
answ: (-1) + (-2) = -3 < -2

1.2) Show that a × b can be less than min(a, b).
anws: (-1) x 2 = -2 < -1

1.3) Design/draw a road network with two points a and b such that the fastest route between a and b is not the shortest route.
ans: 
a ----------- c ----------- b
   \                         			   /
    \--------- d ---------- /
	
If the distance from a to b going through d is less than the distance from _a_ to _b_ going through _c_ but there is a busy traffic intersection at _d_ with a stop sign that is always backed up, then the route from _a_ to _b_ through _c_ is faster, but the route through _d_ is shorter.
 
 For example,

dist(a,c)=10 miles

dist(c,b)=5 miles

So the distance from _a_ to _b_ through _c_ is 15 miles. Assuming you drive 30 miles per hour, the time to travel this would be 30 minutes


dist(a,d)=5 miles

dist(c,b)=5 miles

So the distance from _a_ to _b_ through _d_ is 10 miles. Assuming you drive 30 miles per hour, the time to travel this would be 20 minutes, but due to the busy intersection at _d_, you are delayed 15 minutes, the total time would be 35 minutes.

Another possible solution: You have a longer route with a higher speed and a shorter route with a lower speed. By choosing the numbers appropriately, you can make the longer route be the winner. The speed may be due to law, or due to traffic jam, or because of pot holes on the road :-)

Suppose road of length l1 has speed limit s1 and another road of length l2 has speed limit l2. The shorter route is determined by comparing l1 with l2. The faster route is determined by comparing l1/s1 with l2/s2. With positive numbers, if l1 > l2 but l1 < l2 * s1 / s2, then the faster route differs from the shorter route.

1.4) Design/draw a road network with two points a and b such that the shortest route between a and b is not the route with the fewest turns.

anws: 

the road from a to b, through c,  is shorter in distance than the road from a to b, through d but road through c has way more turns

1-5. [4] The knapsack problem is as follows: given a set of integers S = {s1, s2,...,sn}, and a target number T, find a subset of S which adds up exactly to T. For example, there exists a subset within S = {1, 2, 5, 9, 10} that adds up to T = 22 but not T = 23. Find counterexamples to each of the following algorithms for the knapsack problem. That is, giving an S and T such that the subset is selected using the algorithm does not leave the knapsack completely full, even though such a solution exists.

(a) Put the elements of S in the knapsack in left to right order if they fit, i.e. the first-fit algorithm. 

(b) Put the elements of S in the knapsack from smallest to largest, i.e. the best-fit algorithm. 

(c) Put the elements of S in the knapsack from largest to smallest.