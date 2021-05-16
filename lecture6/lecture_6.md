# Lecture 6: Column space and Null-space

 [toc]

## The intersection and union of subspace

Suppose two subspace $\mathbb{S}$ and ${\mathbb{T}}$,

- their intersection $\mathbb{S}\cap\mathbb{T}$ is also a subspace.
  $$
  \exist \boldsymbol{v},\boldsymbol{w} \in \mathbb{S}\cap\mathbb{T} \Rightarrow
  \begin{cases}
  \boldsymbol{v} \in \mathbb{S}, \boldsymbol{v} \in \mathbb{T} \\
  \boldsymbol{w} \in \mathbb{S}, \boldsymbol{w} \in \mathbb{T}
  \end{cases}
  \Rightarrow \\
  \boldsymbol{v + w} \in \mathbb{S} \text{ and } \in \mathbb{T},
  \boldsymbol{kv} \in \mathbb{S} \text{ and } \in \mathbb{T},
  \boldsymbol{kw} \in \mathbb{S} \text{ and } \in \mathbb{T}
  $$

- their union $\mathbb{S}\cup\mathbb{T}$ is not a subspace.

  Proof by contradiction, there are so many counter-example.

## Column space

Give a matrix $A=\left[\begin{matrix}1&1&2\\ 2&1&3\\ 3&1&4\\ 4&1&5 \end{matrix}\right]$, each column vector of $A$ is a subspace of $\mathbb{R}^4$, and all the linear combination of column vectors form a subspace called **column space**.

What we concern about is the scale of column space of a given matrix, and we can use a equation $Ax=b$ to represent this question.

####  Ax=b

Suppose $Ax=b$ like following:
$$
Ax=
\left[\begin{matrix}1&1&2\\ 2&1&3\\ 3&1&4\\ 4&1&5 \end{matrix}\right]
\left[\begin{matrix}x_1\\ x_2\\ x_3 \end{matrix}\right]
=
\left[\begin{matrix}b_1\\ b_2\\ b_3\\ b_4 \end{matrix}\right]
=b
$$
We can propose two question(actually is one):

- Does $Ax=b$ always has a solution for every b ?
- What $b$ can make $Ax=b$ have a solution ?

From forward lecture, we know that $Ax$ is the combination of column vectors of $A$:
$$
Ax=
\left[\begin{matrix}1&1&2\\ 2&1&3\\ 3&1&4\\ 4&1&5 \end{matrix}\right]
\left[\begin{matrix}x_1\\ x_2\\ x_3 \end{matrix}\right]
=
x_1\left[\begin{matrix}1\\ 2\\ 3\\ 4 \end{matrix}\right]
x_2\left[\begin{matrix}1\\ 1\\ 1\\ 1 \end{matrix}\right]
x_3\left[\begin{matrix}2\\ 3\\ 4\\ 5 \end{matrix}\right]
$$
or in other word, $Ax$ is represent the column space of $A$.

Obviously, three 4-dimension vectors can not full-fill $\mathbb{R}^4$, so $Ax$(which is the column space of $A$)  subspace of $\mathbb{R}^4$, it can only expression a part of 4-dimension vector $b$ that is $Ax=b$ doesn't have solution for every $b$.

And only $b$ is in $A$'s' column space, $Ax=b$ have solution.

## Null space

Null space of $A$: all solution of $Ax=0$.

### Solution of Ax=0

$$
Ax=
\left[\begin{matrix}1&1&2\\ 2&1&3\\ 3&1&4\\ 4&1&5 \end{matrix}\right]
\left[\begin{matrix}x_1\\ x_2\\ x_3 \end{matrix}\right]
=
\left[\begin{matrix}0\\ 0\\ 0\\ 0 \end{matrix}\right]
=0
$$

Solve the equation and $x=k\left[\begin{matrix}1\\ 1\\ -1\end{matrix}\right], k \in R.$

Check that solution of $Ax=0$ always give a subspace:
$$
\exist \boldsymbol{v}, \boldsymbol{w} \Rightarrow Av=0,Aw=0\\
\Rightarrow
\begin{cases}
A(v+w)=0\\
A(kv)=0\\
A(kw)=0
\end{cases}
$$

### Solution of Ax=b: explain from a space aspect

So for a special $b(b\ne0)$ the solutions of $Ax=b$ can't form a subspace: $x$ won't go through $\boldsymbol{0}$, and when $Ax=b$ exist solution, $b$ is in the column space of $A$,  all the solution of $Ax=b$ construct a plain that don't go through zero-point.

