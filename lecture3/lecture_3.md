# Lecture 3: Matrix multiplication

[toc]

## different ways of matrix multiplication

Definition:
$$
A_{m*n} \cdot B_{n*p} = C_{m*p}
$$
where $c_{ij}=\sum_{k=1}^n a_{ik} \cdot b_{kj}$  is theelements of $C_{m*p}$ .

Normarlly, we do matrix multiplication like ablove, but let's look at in whole columns and rows.

- Consider columns of matrix $B$:

  we have $A \cdot b_{i} =c_{i} \text{, where }b_{i} \text{ is the column vector of }B\text{, and i is in range p}$, $c_{i}$ is the combination of the columns of $A$.

- Consider rows of matrix $A$:

  we have $a_{i} \cdot B = c_{i} \text{, where }a_{i} \text{ is the row vector of }A\text{, and i is in range m}$, $c_{i}$ is the combination of the rows of $B$.

- Or suppose all of the columns and rows:

  $A \cdot B = \text{sum of (cols of A) } \cdot \text{rows of B}$

- partitioned multiplication

## Inverses(square matrix)

For a square matrix $A$, if $A$ is invertible, then exist a unique matrix $A^{-1}$ satisfy that:
$$
A \cdot A^{-1} = I = A^{-1} \cdot A
$$

- Matrix $A$ must be a square matrix, if not, then matrix $A_{-1}$ on the left side and right side may have different size, it's aginst the unique casd.

Look at matrix $\left[ \begin{matrix}1&3 \\ 2&6 \end{matrix}\right]$, according to the value of determinant $\begin{vmatrix}1&3 \\ 2&6 \end{vmatrix} = 0$ we can know this matrix is inreversible. But let's see the columns of the matrix, vector$\left[ \begin{matrix}2 \\6 \end{matrix}\right]$

is the multiple of vector $\left[ \begin{matrix}1\\3 \end{matrix}\right]$, which means one of them insignificance to its linear combination.

Thus,
$$
\text{if exist a non-zero vector } x \text{, makes }Ax=0 \text{ then } A \text{ is invertible.}
$$

## solution

solve the inverse of matrix $\left[ \begin{matrix}1&3 \\ 2&7 \end{matrix}\right]$.

### Gauss-Jordan method

$$
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 3 \\
            2 & 7 \\
        \end{matrix}&
        \begin{matrix}
            1 & 0 \\
            0 & 1 \\
        \end{matrix}
	\end{array}
\right]
\Longrightarrow
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 3 \\
            0 & 1 \\
        \end{matrix}&
        \begin{matrix}
            1 & 0 \\
            -2 & 1 \\
        \end{matrix}
	\end{array}
\right]
\Longrightarrow
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 0 \\
            0 & 1 \\
        \end{matrix}&
        \begin{matrix}
            7 & -3 \\
            -2 & 1 \\
        \end{matrix}
	\end{array}
\right]
$$

use augmented matrix and do matrix exchange.

After some operations, matrix $\left[ \begin{matrix}1&3 \\ 2&7 \end{matrix}\right]$ become matrix $I$, in *Lecture 2* we know matrix multipliction can present this process, so we can suppose exist a exchange matrix $E$  makes $EA=I$ and $E$  is equal $A^{-1}$.

And matrix $I$ on the right side of the augmented matrix did the same operation then become $\left[ \begin{matrix}7&-3 \\ -2&1 \end{matrix}\right]$ can see as exchange matrix $EI=E=A^{-1}$, thus matrix $\left[ \begin{matrix}7&-3 \\ -2&1 \end{matrix}\right]$ is $A^{-1}$.

