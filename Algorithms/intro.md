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
	