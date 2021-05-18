# Lecture 8: Complete solution of Ax=b

[toc]

## Solution of Ax=b

### Solvability of $Ax=b$

$$
\left[\begin{matrix}1&2&2&2 \\ 2&4&6&8 \\ 3&6&8&10 \end{matrix}\right]
\left[\begin{matrix}x_1 \\ x_2 \\ x_3\\ x_4 \end{matrix}\right]
=
\left[\begin{matrix}b_1 \\ b_2 \\ b_3 \end{matrix}\right]
$$

Use elimination with augment matrix:
$$
\left[\begin{array}{c:c}
\begin{matrix}1&2&2&2 \\ 2&4&6&8 \\ 3&6&8&10 \end{matrix} &
\begin{matrix}b_1 \\ b_2 \\ b_3 \end{matrix}
\end{array}\right]
\Longrightarrow
\left[\begin{array}{c:c}
\begin{matrix}1&2&2&2 \\ 0&0&2&4 \\ 0&0&0&0 \\\end{matrix} &
\begin{matrix}b_1 \\ b_2-2b_1 \\ b_3-b_2-b_1 \end{matrix}
\end{array}\right]
$$
Back substitution row 3 into $Ax=b$ we can get $0=b_3-b_2-b_1$, thus $b_3=b_1+b_2$, which means the third element of $b$ is equal to the plus of first and second element. Reflect on the matrix $A$ is that row 3 is equal to row 1 plus row 2. Combine with the conclusion of lecture 7, we can know the condition of the solution:

- in column consider:
  - $b$ is in the column space of $A$ or,
  - $b$ is the combination of the columns of $A$.
- in row consider: if the combination of rows of $A$ gives zero-row, the same combination of $b$ should also be real number $0$.

### Solution: $x_{general}$

Suppose $b=\left[\begin{matrix}1 \\ 5 \\ 6 \end{matrix}\right]$, then eliminated augment matrix:
$$
\left[\begin{array}{c:c}
\begin{matrix}1&2&0&-2 \\ 0&0&1&2 \\ 0&0&0&0 \end{matrix} &
\begin{matrix}-2 \\ \frac{3}{2} \\ 0 \end{matrix}
\end{array}\right]
$$
General solution is all the solutions satisfy the equation, usually express as a infinite solution form. We already know that $Ax_{nullspace} \equiv 0$ and we can solve a $x_{practice}$ for a specific $b(b \in \mathbb R^{column space})$, so the definition is as following:

$x_{general}$: all the solutions satisfy the equation, general include two part $x_{particular}$ and $x_{nullspace}$.

From the eliminated augment matrix, we can solve the $x_{particular}=\left[\begin{matrix}-2 \\ 0 \\ \frac{3}{2} \\ 0 \end{matrix}\right]$.

And set the augment column zero we can solve the $x_{nullspace}=k_1\left[\begin{matrix}-2 \\ 1 \\ 0 \\ 0 \end{matrix}\right]+k_2\left[\begin{matrix}2 \\ 0 \\ -2 \\ 1 \end{matrix}\right](k_1,k_2 \in R)$.

So the $x_{general}=x_{nullspace}+x_{particular}=k_1\left[\begin{matrix}-2 \\ 1 \\ 0 \\ 0 \end{matrix}\right]+k_2\left[\begin{matrix}2 \\ 0 \\ -2 \\ 1 \end{matrix}\right]+\left[\begin{matrix}-2 \\ 0 \\ \frac{3}{2} \\ 0 \end{matrix}\right](k_1,k_2 \in R)$

## Solution cases for a $A_{m*n}$

Suppose a matrix $A_{m*n}$ and rank $r(A)=r$, debate its solution cases:

- full rank of column: r=n<m

  after elimination we will get reduced matrix $R=\left[\begin{matrix}I \\ 0 \end{matrix}\right]$, r=n means there aren't free variables, the solution of $Ax=b$ if exist(when $b \in \mathbb R^{column space}$), then is the only $X_{particular}$.

- full rank of row: r=m<n

  after elimination we will get reduced matrix $R=\left[\begin{matrix}I&F \end{matrix}\right]$, there are n-r free variables, so there always have solution for $Ax=b$.

- full rank of matrix: square matrix, r=n=m

  after elimination we will get reduced matrix $R=\left[\begin{matrix}I \end{matrix}\right]$, null space only $0$, exist only solution for every $b$.

- r<m and r<n, $R=\left[\begin{matrix}I&F \\ 0&0 \end{matrix}\right]$, it depends on $b$, zero solution or infinite solutions.