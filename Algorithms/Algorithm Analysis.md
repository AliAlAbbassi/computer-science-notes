# Algorithm Analysis
![[Pasted image 20210727032649.png]]

The best, worst, and average-case time complexities for any given algorithm are numerical functions over the size of possible problem instances. However, it is very difficult to work precisely with these functions, because they tend to: 

• Have too many bumps – An algorithm such as binary search typically runs a bit faster for arrays of size exactly n = 2k − 1 (where k is an integer), because the array partitions work out nicely. This detail is not particularly significant, but it warns us that the exact time complexity function for any algorithm is liable to be very complicated, with little up and down bumps as shown in Figure 2.2. 

• Require too much detail to specify precisely – Counting the exact number of RAM instructions executed in the worst case requires the algorithm be specified to the detail of a complete computer program. Further, the precise answer depends upon uninteresting coding details (e.g., did he use a case statement or nested ifs?). Performing a precise worst-case analysis like 

T(n) = 12754n2 + 4353n + 834 lg2 n + 13546

would clearly be very difficult work, but provides us little extra information than the observation that “the time grows quadratically with n.”

The formal definitions associated with the Big Oh notation are as follows: 

• f(n) = O(g(n)) means c · g(n) is an upper bound on f(n). Thus there exists some constant c such that f(n) is always ≤ c · g(n), for large enough n (i.e. , n ≥ n0 for some constant n0). 

• f(n) = Ω(g(n)) means c · g(n) is a lower bound on f(n). Thus there exists some constant c such that f(n) is always ≥ c · g(n), for all n ≥ n0. • f(n) = Θ(g(n)) means c1 · g(n) is an upper bound on f(n) and c2 · g(n) is a lower bound on f(n), for all n ≥ n0. Thus there exist constants c1 and c2 such that f(n) ≤ c1 ·g(n) and f(n) ≥ c2 ·g(n). This means that g(n) provides a nice, tight bound on f(n).

#Takehomelesson: The Big Oh notation and worst-case analysis are tools that greatly simplify our ability to compare the efficiency of algorithms.


### Stop and Think: Back to the Definition 

Problem: Is 2n+1 = Θ(2n)?

Solution: Designing novel algorithms requires cleverness and inspiration. However, applying the Big Oh notation is best done by swallowing any creative instincts you may have. All Big Oh problems can be correctly solved by going back to the definition and working with that. 

• Is 2n+1 = O(2n)? Well, f(n) = O(g(n)) iff (if and only if) there exists a constant c such that for all sufficiently large n f(n) ≤ c · g(n). Is there? The key observation is that 2n+1 = 2 · 2n, so 2 · 2n ≤ c · 2n for any c ≥ 2. 

• Is 2n+1 = Ω(2n)? Go back to the definition. f(n) = Ω(g(n)) iff there exists a constant c > 0 such that for all sufficiently large n f(n) ≥ c · g(n). This would be satisfied for

### Stop and Think: Hip to the Squares? 
Problem: Is (x + y)^2 = O(x^2 + y^2).

### Growth Rates
• All such algorithms take roughly the same time for n = 10. 
• Any algorithm with n! running time becomes useless for n ≥ 20. 
• Algorithms whose running time is 2n have a greater operating range, but become impractical for n > 40. 
• Quadratic-time algorithms whose running time is n2 remain usable up to about n = 10, 000, but quickly deteriorate with larger inputs. They are likely to be hopeless for n > 1,000,000. 
• Linear-time and n lg n algorithms remain practical on inputs of one billion items. 
• An O(lg n) algorithm hardly breaks a sweat for any imaginable value of n.

### Dominance Relations
n! ≫ 2n ≫ n3 ≫ n2 ≫ n log n ≫ n ≫ log n ≫ 1

[[duckweedProblem]]

#Takehomelesson: Although esoteric functions arise in advanced algorithm analysis, a small variety of time complexities suffice and account for most algorithms that are widely used in practice.

### Adding Functions
O(f(n)) + O(g(n)) → O(max(f(n), g(n)))   
Ω(f(n)) + Ω(g(n)) → Ω(max(f(n), g(n)))   
Θ(f(n)) + Θ(g(n)) → Θ(max(f(n), g(n)))  

This is very useful in simplifying expressions, since it implies that n3 + n2 + n +1= O(n3). Everything is small potatoes besides the dominant term. The intuition is as follows. At least half the bulk of f(n) + g(n) must come from the larger value. The dominant function will, by definition, provide the larger value as n → ∞. Thus, dropping the smaller function from consideration reduces the value by at most a factor of 1/2, which is just a multiplicative constant. Suppose f(n) = O(n2) and g(n) = O(n2). This implies that f(n) + g(n) = O(n2) as well.

### Efficiency

##### Selection Sort
code:   
selection_sort(int s[], int n) { 
		int i,j; /* counters */ 
		int min; /* index of minimum */ 
		for (i = 0; i < n; i++) {
				min  = i;
				for (j = i + 1; j < n; j++) {
						if (s[j] < s[min]) min = j;	
				swap(&s[i], &s[min]);
				}
		}

The outer loop goes around n times. The nested inner loop goes around n−i−1 times, where i is the index of the outer loop. The exact number of times the if statement is executed is given by: 
S(n) = n !−1 i=0 n !−1 j=i+1 1 = n !−1 i=0 n − i − 1

A way to think about it is in terms of upper and lower bounds. We have n terms at most, each of which is at most n − 1. Thus, S(n) ≤ n(n − 1) = O(n2). We have n/2 terms each that are bigger than n/2. Thus S(n) =≥ (n/2) × (n/2) = Ω(n2). Together, this tells us that the running time is Θ(n2), meaning that selection sort is quadratic.

##### Insertion Sort
code :

	for (i = 1; i  < n; i++) {
		j = i;
		while (( j > 0 ) && ( s[j] < s[j-1] )) {
				swap(&s[j], &s[j-1]);	
				j = j - 1;
		}
	}
	
How often does the inner while loop iterate? This is tricky because there are two different stopping conditions: one to prevent us from running off the bounds of the array (j > 0) and the other to mark when the element finds its proper place in sorted order (s[j] < s[j − 1]). Since worst-case analysis seeks an upper bound on the running time, we ignore the early termination and assume that this loop always goes around i times. In fact, we can assume it always goes around n times since i

### String Pattern Matching
Pattern matching is the most fundamental algorithmic operation on text strings. This algorithm implements the find command available in any web browser or text editor: 

Problem: Substring Pattern Matching 
Input: A text string t and a pattern string p.   
Output: Does t contain the pattern p as a substring, and if so where?

Code:

	int findmatch(char *p, char *t) { 
			int i,j; /* counters */ 
			int m, n; /* string lengths */ 
			m = strlen(p); 
			n = strlen(t); 
			for (i=0; i<=(n-m); i=i+1) { 
				j=0; 
				while ((j < m) && (t[i+j] == p[j])
						j = j + 1;
				if (j == m) return(i);
			}
				return(-1);
	   }
	 
	 
The worst-case running time of these two nested loops is the inner while loop goes around at most m times, and potentially far lass when the pattern match fails. The outer loops goes around at most n-m times. since no complete alignment is possible once we get too far to the right of ther text.