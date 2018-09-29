# Complete Search

The Complete Search technique, also known as brute force or recursive backtracking, is a
method for solving a problem by traversing the entire (or part of the) search space to obtain
the required solution. During the search, we are allowed to prune (that is, choose not to
explore) parts of the search space if we have determined that these parts have no possibility
of containing the required solution.

In programming contests, a contestant should develop a Complete Search solution when
there is clearly no other algorithm available (e.g. the task of enumerating all permutations
of {0, 1, 2, . . .,N − 1} clearly requires O(N!) operations) or when better algorithms exist,
but are overkill as the input size happens to be small (e.g. the problem of answering Range
Minimum Queries as in Section 2.4.3 but on static arrays with N ≤ 100 is solvable with an
O(N) loop for each query).

In ICPC, Complete Search should be the first solution considered as it is usually easy
to come up with such a solution and to code/debug it. Remember the ‘KISS’ principle:
Keep It Short and Simple. A bug-free Complete Search solution should never receive the
Wrong Answer (WA) response in programming contests as it explores the entire search space.
However, many programming problems do have better-than-Complete-Search solutions as
illustrated in the Section 3.1. Thus a Complete Search solution may receive a Time Limit
Exceeded (TLE) verdict. With proper analysis, you can determine the likely outcome (TLE
versus AC) before attempting to code anything (Table 1.4 in Section 1.2.3 is a good starting
point). If a Complete Search is likely to pass the time limit, then go ahead and implement
one. This will then give you more time to work on harder problems in which Complete
Search will be too slow.

In IOI, you will usually need better problem solving techniques as Complete Search
solutions are usually only rewarded with very small fractions of the total score in the subtask
scoring schemes. Nevertheless, Complete Search should be used when you cannot come up
with a better solution—it will at least enable you to score some marks.
Sometimes, running Complete Search on small instances of a challenging problem can
help us to understand its structure through patterns in the output (it is possible to visualize
the pattern for some problems) that can be exploited to design a faster algorithm. Some
combinatorics problems in Section 5.4 can be solved this way. Then, the Complete Search
solution can also act as a verifier for small instances, providing an additional check for the
faster but non-trivial algorithm that you develop.

After reading this section, you may have the impression that Complete Search only works
for ‘easy problems’ and it is usually not the intended solution for ‘harder problems’. This is
not entirely true. There exist hard problems that are only solvable with creative Complete
Search algorithms. We have reserved those problems for Section 8.2.

In the next two sections, we give several (easier) examples of this simple yet possibly
challenging paradigm. In Section 3.2.1, we give examples that are implemented iteratively.
In Section 3.2.2, we give examples on solutions that are implemented recursively (with backtracking).
Finally, in Section 3.2.3, we provide a few tips to give your solution, especially
your Complete Search solution, a better chance to pass the required Time Limit.

## 3.2.1 Iterative Complete Search

**Iterative Complete Search (Two Nested Loops: UVa 725 - Division)**

Abridged problem statement: Find and display all pairs of 5-digit numbers that collectively
use the digits 0 through 9 once each, such that the first number divided by the second is
equal to an integer N, where 2 ≤ N ≤ 79. That is, abcde / fghij = N, where each letter
represents a different digit. The first digit of one of the numbers is allowed to be zero, e.g.
for N = 62, we have 79546 / 01283 = 62; 94736 / 01528 = 62.

Quick analysis shows that fghij can only range from 01234 to 98765 which is at most
≈ 100K possibilities. An even better bound for fghij is the range 01234 to 98765 / N,
which has at most ≈ 50K possibilities for N = 2 and becomes smaller with increasing N. For
each attempted fghij, we can get abcde from fghij * N and then check if all 10 digits are
different. This is a doubly-nested loop with a time complexity of at most ≈ 50K×10 = 500K
operations per test case. This is small. Thus, an iterative Complete Search is feasible. The
main part of the code is shown below (we use a fancy bit manipulation trick shown in Section
2.2 to determine digit uniqueness):
```
for (int fghij = 1234; fghij <= 98765 / N; fghij++) {
int abcde = fghij * N; // this way, abcde and fghij are at most 5 digits
int tmp, used = (fghij < 10000); // if digit f=0, then we have to flag it
tmp = abcde; while (tmp) { used |= 1 << (tmp % 10); tmp /= 10; }
tmp = fghij; while (tmp) { used |= 1 << (tmp % 10); tmp /= 10; }
if (used == (1<<10) - 1) // if all digits are used, print it
printf("%0.5d / %0.5d = %d\n", abcde, fghij, N);
}
```

**Iterative Complete Search (Many Nested Loops: UVa 441 - Lotto)**

In programming contests, problems that are solvable with a single loop are usually considered
easy. Problems which require doubly-nested iterations like UVa 725 - Division above are more
challenging but they are not necessarily considered difficult. Competitive programmers must
be comfortable writing code with more than two nested loops.

Let’s take a look at UVa 441 which can be summarized as follows: Given 6 < k < 13
integers, enumerate all possible subsets of size 6 of these integers in sorted order.
Since the size of the required subset is always 6 and the output has to be sorted lexicographically
(the input is already sorted), the easiest solution is to use six nested loops as
shown below. Note that even in the largest test case when k = 12, these six nested loops
will only produce 12C6 = 924 lines of output. This is small.
```
for (int i = 0; i < k; i++) // input: k sorted integers
scanf("%d", &S[i]);
for (int a = 0 ; a < k - 5; a++) // six nested loops!
for (int b = a + 1; b < k - 4; b++)
for (int c = b + 1; c < k - 3; c++)
for (int d = c + 1; d < k - 2; d++)
for (int e = d + 1; e < k - 1; e++)
for (int f = e + 1; f < k ; f++)
printf("%d %d %d %d %d %d\n",S[a],S[b],S[c],S[d],S[e],S[f]);
```
**Iterative Complete Search (Loops + Pruning: UVa 11565 - Simple Equations)**

Abridged problem statement: Given three integers A, B, and C (1 ≤ A,B,C ≤ 10000),
find three other distinct integers x, y, and z such that x + y + z = A, x × y × z = B, and
x2 + y2 + z2 = C.

The third equation x2 + y2 + z2 = C is a good starting point. Assuming that C has
the largest value of 10000 and y and z are one and two (x, y, z have to be distinct), then
the possible range of values for x is [−100 ... 100]. We can use the same reasoning to get a
similar range for y and z. We can then write the following triply-nested iterative solution
below that requires 201 × 201 × 201 ≈ 8M operations per test case.

```
bool sol = false; int x, y, z;
for (x = -100; x <= 100; x++)
for (y = -100; y <= 100; y++)
for (z = -100; z <= 100; z++)
if (y != x && z != x && z != y && // all three must be different
x + y + z == A && x * y * z == B && x * x + y * y + z * z == C) {
if (!sol) printf("%d %d %d\n", x, y, z);
sol = true; }
```
Notice the way a short circuit AND was used to speed up the solution by enforcing a
lightweight check on whether x, y, and z are all different before we check the three formulas.
The code shown above already passes the required time limit for this problem, but we can
do better. We can also use the second equation x × y × z = B and assume that x = y = z
to obtain x × x × x < B or x < cbrt(B). The new range of x is [−22 ... 22]. We can also prune
the search space by using if statements to execute only some of the (inner) loops, or use
break and/or continue statements to stop/skip loops. The code shown below is now much
faster than the code shown above (there are a few other optimizations required to solve the
extreme version of this problem: UVa 11571 - Simple Equations - Extreme!!):

```
bool sol = false; int x, y, z;
for (x = -22; x <= 22 && !sol; x++) if (x * x <= C)
for (y = -100; y <= 100 && !sol; y++) if (y != x && x * x + y * y <= C)
for (z = -100; z <= 100 && !sol; z++)
if (z != x && z != y &&
x + y + z == A && x * y * z == B && x * x + y * y + z * z == C) {
printf("%d %d %d\n", x, y, z);
sol = true; }
```

** Iterative Complete Search (Permutations: UVa 11742 - Social Constraints) **

Abridged problem statement: There are 0 < n ≤ 8 movie goers. They will sit in the front
row in n consecutive open seats. There are 0 ≤ m ≤ 20 seating constraints among them, i.e.
movie goer a and movie goer b must be at most (or at least) c seats apart. The question is
simple: How many possible seating arrangements are there?

The key part to solve this problem is in realizing that we have to explore all permutations (seating arrangements). Once we realize this fact, we can derive this simple O(m × n!) ‘filtering’ solution. We set counter = 0 and then try all possible n! permutations. We increase the counter by 1 if the current permutation satisfies all m constraints. When all n! permutations have been examined, we output the final value of counter. As the maximum n is 8 and maximum m is 20, the largest test case will still only require 20 × 8! = 806400 operations—a perfectly viable solution.

If you have never written an algorithm to generate all permutations of a set of numbers (see Exercise 1.2.3, task 7), you may still be unsure about how to proceed. The simple C++ solution is shown below.
```
#include <algorithm> // next_permutation is inside this C++ STL
// the main routine
int i, n = 8, p[8] = {0, 1, 2, 3, 4, 5, 6, 7}; // the first permutation
do { // try all possible O(n!) permutations, the largest input 8! = 40320
... // check the given social constraint based on ‘p’ in O(m)
} // the overall time complexity is thus O(m * n!)
while (next_permutation(p, p + n)); // this is inside C++ STL <algorithm>
```

** Iterative Complete Search (Subsets: UVa 12455 - Bars) **

Abridged problem statement1: Given a list l containing 1 ≤ n ≤ 20 integers, is there a subset of list l that sums to another given integer X?

We can try all 2n possible subsets of integers, sum the selected integers for each subset in O(n), and see if the sum of the selected integers equals to X. The overall time complexity is thus O(n × 2n). For the largest test case when n = 20, this is just 20 × 2^20 ≈ 21M. This is ‘large’ but still viable (for reason described below).

If you have never written an algorithm to generate all subsets of a set of numbers (see Exercise 1.2.3, task 8), you may still be unsure how to proceed. An easy solution is to use the binary representation of integers from 0 to 2^n − 1 to describe all possible subsets.

If you are not familiar with bit manipulation techniques, see Section 2.2. The solution can be written in simple C/C++ shown below (also works in Java). Since bit manipulation operations are (very) fast, the required 21M operations for the largest test case are still doable in under a second. Note: A faster implementation is possible (see Section 8.2.1).
```
// the main routine, variable ‘i’ (the bitmask) has been declared earlier
for (i = 0; i < (1 << n); i++) { // for each subset, O(2^n)
sum = 0;
for (int j = 0; j < n; j++) // check membership, O(n)
if (i & (1 << j)) // test if bit ‘j’ is turned on in subset ‘i’?
sum += l[j]; // if yes, process ‘j’
if (sum == X) break; // the answer is found: bitmask ‘i’
}
```
Exercise 3.2.1.1: For the solution of UVa 725, why is it better to iterate through fghij and not through abcde?

Exercise 3.2.1.2: Does a 10! algorithm that permutes abcdefghij work for UVa 725?

Exercise 3.2.1.3*: Java does not have a built-in next permutation function yet. If you are a Java user, write your own recursive backtracking routine to generate all permutations! This is similar to the recursive backtracking for the 8-Queens problem.
 
Exercise 3.2.1.4*: How would you solve UVa 12455 if 1 ≤ n ≤ 30 and each integer can be as big as 1000000000? Hint: See Section 8.2.4.

## 3.2.2 Recursive Complete Search

** Simple Backtracking: UVa 750 - 8 Queens Chess Problem **

[TODO]
