---
layout: default
title: "Two sum"
---

- Let $A = \\{a_1, a_2, a_3, \ldots, a_n\\}$, and find indices $i, j$ such that $1 \le x, y \le n$ and $x \ne y$, where  $a[x] + a[y] = T$.

- Create a function $f: A \to [x, y]$ such that $f(A, T) \to [x, y]$.

- Create a hashmap $M$ such that $M = \\{T - x_i \mapsto i \mid \forall x_i \in A\\}$.

- For each $x_j \in A$, search for the complement $T - x_j$ in $M$:
  - If $T - x_j \in M$ and $M[T - x_j] \ne j$, then return $[M[T - x_j],\; j]$.
  - It is guaranteed that a solution exists.