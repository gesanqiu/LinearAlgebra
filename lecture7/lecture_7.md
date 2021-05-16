# Lecture 7: Solving the Ax=0

[toc]

## Elimination

Suppose matrix $A=\left[\begin{matrix}1&2&2&2\\ 2&4&6&8\\ 3&6&8&10 \end{matrix}\right]$, solve the null space of $x$ from $Ax=0$.
$$
\left[\begin{matrix}1&2&2&2\\ 2&4&6&8\\ 3&6&8&10 \end{matrix}\right]
\left[\begin{matrix}x_1\\ x_2\\ x_3\\ x_4 \end{matrix}\right]
=0
$$


Elimination:
$$
\left[\begin{matrix}1&2&2&2\\ 2&4&6&8\\ 3&6&8&10 \end{matrix}\right]
\rightarrow
\left[\begin{matrix}\color{#F00}{1}&2&2&2\\ 0&0&2&4\\ 0&0&2&4 \end{matrix}\right]
\rightarrow
\left[\begin{matrix}\color{#F00}{1}&2&2&2\\ 0&0&\color{#F00}{2}&4\\ 0&0&0&0 \end{matrix}\right]
$$
After elimination we get two pivots: 1 and 2, the number of pivot is equal to the rank of the matrix.

For free column we could free choice, and figure out the pivot columns by back substitution:

- two pivot columns and two free columns:
  - choose value for free variable, $\left[\begin{matrix}x_2 \\x_4 \end{matrix}\right] = \left[\begin{matrix}1 \\0 \end{matrix}\right]$ or $\left[\begin{matrix}x_2 \\x_4 \end{matrix}\right] = \left[\begin{matrix}0 \\1 \end{matrix}\right]$, other value will be the linear combination of $\left[\begin{matrix}1 \\0 \end{matrix}\right]$ and $\left[\begin{matrix}0 \\1 \end{matrix}\right]$
  - solve the $\left[\begin{matrix}x_1 \\x_3 \end{matrix}\right] = \left[\begin{matrix}-2 \\0 \end{matrix}\right]$ or $\left[\begin{matrix}x_1 \\x_3 \end{matrix}\right] = \left[\begin{matrix}2 \\-0 \end{matrix}\right]$
  - two special solution: $\left[\begin{matrix}-1\\ 1\\ 0\\ 0\end{matrix}\right]$ and $\left[\begin{matrix}2\\ 0\\ -2\\ 1\end{matrix}\right]$
- all the linear combinations of special solutions form all the solution of $A$ called null space:$k_1\left[\begin{matrix}-1\\ 1\\ 0\\ 0\end{matrix}\right] + k_2\left[\begin{matrix}2\\ 0\\ -2\\ 1\end{matrix}\right]$

## Reduced echelon matrix R

Reduce the eliminated matrix and we will got:
$$
\left[\begin{matrix}\color{#F00}{1}&2&2&2\\ 0&0&\color{#F00}{2}&4\\ 0&0&0&0 \end{matrix}\right]
\rightarrow
\left[\begin{matrix}\color{#F00}{1}&2&0&-2\\ 0&0&\color{#F00}{2}&4\\ 0&0&0&0 \end{matrix}\right]
\rightarrow
\left[\begin{matrix}\color{#F00}{1}&2&0&-2\\ 0&0&\color{#F00}{1}&2\\ 0&0&0&0 \end{matrix}\right]
\rightarrow
\left[\begin{matrix}\color{#F00}{1}&0&2&-2\\ 0&\color{#F00}{1}&0&2\\ 0&0&0&0 \end{matrix}\right]
=R
$$
and concerned of the pivot columns and free columns dividedly:
$$
I=\left[\begin{matrix}\color{#F00}{1}&0\\ 0&\color{#F00}{1} \end{matrix}\right],
F=\left[\begin{matrix}2&-2\\ 0&2 \end{matrix}\right] \\
\Rightarrow R=\left[\begin{matrix}I&F\\ 0&0 \end{matrix}\right] \\
$$
where $I$ is a $r*r$ size matrix represent the pivot columns and $F$ is $r*(n-r)$ size matrix represent the free columns.

Solving the $Ax=0$ becomes to solve $Rx=0$, suppose null-space matrix $N$--all the special solution of $Ax=0$, we can infer that:
$$
Ax=Rx=\left[\begin{matrix}I&F\\ 0&0 \end{matrix}\right]
\left[\begin{matrix}x_{pivot}\\ x_{free}\end{matrix}\right]
=RN=0
$$

$$
\left[\begin{matrix}I&F \end{matrix}\right]
\left[\begin{matrix}x_{pivot}\\ x_{free}\end{matrix}\right]
=0
\Longrightarrow
I \cdot x_{pivot} + F \cdot x_{free}=0
\Longrightarrow
x_{pivot} = -F \cdot x_{free}
$$

Usually we choose the column of $I$ as the value of $x_{free}$, so $x_{pivot} = -F$, thus $N=\left[\begin{matrix}-F\\ I_{(n-r)*(n-r)}\end{matrix}\right]$.

So back to the example $R=\left[\begin{matrix}\color{#F00}{1}&0&2&-2\\ 0&\color{#F00}{1}&0&2\\ 0&0&0&0 \end{matrix}\right]$, we can solve the $N=\left[\begin{matrix}-2&2 \\ 0&-2\\ 1&0\\ 0&1\end{matrix}\right]$.

Notice that we did a column exchange when reduce the matrix, this will change the null space, so we need to exchange the row 2 and row 3 to clear the influence and get the special solutions : $\left[\begin{matrix}-1\\ 1\\ 0\\ 0\end{matrix}\right]$ and $\left[\begin{matrix}2\\ 0\\ -2\\ 1\end{matrix}\right]$.