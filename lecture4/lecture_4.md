# Lecture 4: A=LU

[toc]

## A=LU

Before we talked about elimination and row exchange of matrix, now we know that matrix multiplication can achieve the same process. So suppose a good matrix $A_{3x3}$, we can eliminate matrix $A$ with exchange matrix use following form and finally get a upper triangular matrix $U$:
$$
E_{32}E_{31}E_{21}A=U
\tag{1}
$$
Easy to know exchange matrix must be invertible, so formula (1) can transform into:
$$
A=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}U
\tag{2}
$$
and $L=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$, thus $A=LU$.

## Why A=LU

Right now we have:
$$
\begin{cases}
EA=U \\
AL=U
\tag{3}
\end{cases}
$$
if seems $E$ is enough for elimination, why we still $L$, now let's look at a example.

### compare L with E

Still  a good matrix $A_{3x3}$, and $E_{32}=\left[\begin{matrix}1&0&0\\0&1&0\\0&-5&1\end{matrix}\right]$, $E_{21}=\left[\begin{matrix}1&0&0\\-2&1&0\\0&0&1\end{matrix}\right]$, $E_{31}=I$, solve the $L$.

Solution:
$$
A=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}U \\
E_{21}^{-1}=\left[\begin{matrix}1&0&0\\2&1&0\\0&0&1\end{matrix}\right] \text{ , }
E_{31}^{-1}=I \text{ , }
E_{32}^{-1}=\left[\begin{matrix}1&0&0\\0&1&0\\0&5&1\end{matrix}\right] \\
\text{ thus, } L=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}=\left[\begin{matrix}1&0&0\\2&1&0\\0&5&1\end{matrix}\right]
$$

Notice that elements of matrix $L$ are all from matrix $E_{21}$ and $E_{32}$, which means different with matrix $E=\left[\begin{matrix}1&0&0\\-2&1&0\\10&-5&1\end{matrix}\right]$, we can solve the matrix $L$ without doing matrix multiplication.

- $e_{31}$ in matrix $E$ is appear due to the multiplier of elimination.

**Formulation:**

​	Define $l_{ij}$: multiplier of eliminate $row_i$ use $row_j$, thus:
$$
row_i = row_i - l_{ij} \times row_j
\tag{4}
$$

​	and in matrix multiplication we use exchange matrix $E_{ij}$ represent this task.

​	Now we can write down the matrix $L=E^{-1}=\left[\begin{matrix}1&0&0\\l_{21}&1&0\\l_{31}&l_{32}&1\end{matrix}\right]$.

### Postscript

In book 《Linear Algebra》chapter2.3, it said:

>The special property of $L$  is that all the multipliers $l_{ij}$ fall into place. Those numbers are mixed up in $E$(forward elimination from $A$ to $U$ ). They are perfect in $L$ (undoing elimination, returning from $U$ to $A$ ). Inverting puts the steps and their matrices $E_{ij}^{-1}$ in the opposite order and that prevents the mixup.

In short is that using inverse of $E$ avoid the mixture of $l_{ij}$ while forward elimination do. An intuition explain is we minus eliminated row when we doing forward elimination(for example $row_3$ minus eliminated $row_2$ while eliminate element $a_{32}$).

## Application of A=LU--solution of Ax=b

This section is an advanced contents to show what $A=LU$ can do, if you find it's difficult to understand this section, please read after you finished the lecture 8.

Now we know $A=LU$, if we want to solve $Ax=b$, we can substitute $A=LU$ into it and we get $LUx=b$. 

- suppose $Ux=c$, we get $Lc=b$
- solve the $c$ and back substitute

Example, solve the equation $\begin{array}{rl}u+2v&=5\\4u+9v&=21\end{array}$.

1. Extract the coefficient to matrix $A=\left[\begin{matrix}1&2\\4&9\end{matrix}\right]$, $b=\left[\begin{matrix}5\\21\end{matrix}\right]$.

2. $l_{ij}=4$, $L=\left[\begin{matrix}1&0\\4&1\end{matrix}\right]$
   $$
   Lc=b \text{ ， }
   \left[\begin{matrix}1&0\\4&1\end{matrix}\right]
   \cdot
   \left[\begin{matrix}c\end{matrix}\right]
   =
   \left[\begin{matrix}5\\21\end{matrix}\right]
   \Longrightarrow
   c = \left[\begin{matrix}5\\1\end{matrix}\right]
   $$

3. back substitute to $Ux=c$：
   $$
   \left[\begin{matrix}1&2\\0&1\end{matrix}\right]
   \cdot
   \left[\begin{matrix}x\end{matrix}\right]
   =
   \left[\begin{matrix}5\\1\end{matrix}\right]
   \Longrightarrow
   x = \left[\begin{matrix}3\\1\end{matrix}\right]
   $$

In a word, solve $L$ is quicker than $E$.

## The complexity of elimination

Suppose multiple and substract for one element is one operation, and matrix $A_{n*n}$.

1. elimination

$$
a_{ij}-k \cdot a_{1j} \quad \text{while }2 \leq i \leq n,1 \leq j \leq n,\text{k is in}A_{i1}
$$

2. if $i=2$, there are $n-1$ rows need to substract the $row_1$ and every row has $n$ numbers need to multiple and substract, so there are $(n-1)*n$ times operation, nearly $n^2$.

3. if $i=n$, only $a_{nn-1}$ need to change

4. so the complexity of elimination should be:
   $$
   n^2+(n-1)^2+\dots+2^2+1^1\approx \frac{1}{3}n^2
   $$

5. if add one constant column  $b$, it will take
   $$
   (n-1)+(n-2)+\dots+2+1=\frac{n*(n-1)}{2}
   $$
   times operation, and if take back substitute into consideration, it will takes nearly $n^2$ times operation.

