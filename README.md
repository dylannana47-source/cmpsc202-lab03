# Lab 3: Asymptotic Analysis

This lab focuses on understanding and analyzing the asymptotic behavior of algorithms. We will explore concepts such as Big-O, Big-$\Theta$, and Big-$\Omega$ notations, and apply them to various algorithmic problems to determine their efficiency and scalability.

**Instructions:** To complete this lab, you may work in groups, but you must write your solutions yourself. Once you have completed the lab, push your changes to your forked repository.

## Problem 1

Suppose $T(n)$ is the worst case running time of an algorithm with input size $n$, and we know that $T(n)$ is $\mathcal{O}(n^3)$ and $\Omega(n^2)$. For each of the following statements, determine whether it must be true, must be false, or could be either true or false. Give a brief justification for each. 

1. $T(n)$ is $\mathcal{O}(n^2)$.
2. $T(n)$ is $\Theta(n^3)$.
3. $T(n)$ is $\Omega(n)$.
4. $T(n)$ is $\Theta(n^{1.5})$.
5. $T(n)$ is $\mathcal{O}(n)$.
6. $T(n)$ is $\Theta(n^2 \log n)$.

### Solution

We know that $T(n)$ has an upper bound of $O(n^3)$ and a lower bound of $\Omega(n^2)$. These bounds do not determine one exact growth rate.

1. **Could be either.** $T(n)=n^2$ satisfies both given bounds and is $O(n^2)$, while $T(n)=n^3$ satisfies the given bounds but is not $O(n^2)$.
2. **Could be either.** $T(n)=n^3$ is $\Theta(n^3)$, while $T(n)=n^2$ also satisfies the given bounds and is not $\Theta(n^3)$.
3. **Must be true.** Since $n \le n^2$ for $n \ge 1$, a lower bound of $\Omega(n^2)$ also gives a lower bound of $\Omega(n)$.
4. **Must be false.** A function in $\Theta(n^{1.5})$ grows more slowly than $n^2$, so it cannot satisfy the given lower bound of $\Omega(n^2)$.
5. **Must be false.** A function in $O(n)$ cannot also be bounded below by a positive constant times $n^2$ for all sufficiently large $n$.
6. **Could be either.** $T(n)=n^2\log n$ satisfies both given bounds, but $T(n)=n^2$ also satisfies them and is not $\Theta(n^2\log n)$.


## Problem 2
Consider the following algorithm where $f(A, i, j)$ is an unknown algorithm that takes as input an array $A$ and two indicies $i$ and $j$ and returns a number. 

```
Mystery Algorithm
Input: An array of int $A$ of length $n$.
Output: int sum
    n = |A|
    sum = 0
    for i = 1 to n:
        for j = 1 to n:
            sum += f(A, i, j)
```

Without knowing anything about $f$, what can we say about the running time of the Mystery Algorithm in terms of $n$? Justify your answer.

### Solution

The nested loops make exactly $n^2$ calls to $f$. Assuming each call terminates and basic loop and arithmetic operations take constant time, the algorithm therefore takes at least $\Omega(n^2)$ time. Its total running time also depends on the cost of those calls: it is $\Theta(n^2)$ loop and call overhead plus the sum of the running times of all $n^2$ invocations of $f$. Since the running time of $f$ is unknown, we cannot give a tighter upper bound or a single asymptotic running time in terms of $n$ alone.