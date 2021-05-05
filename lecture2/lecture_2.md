# Lecture 2: Elimination

[toc]

This lecture mainly introduced how to solve equations with elimination.

## Solve the Ax=b with elimination

In short, elimination is doing row operation to a given matrix until the matrix become an upper triangular matrix.

### elimination

Suppose we have following equations:
$$
\left\{
	\begin{array}{rl}
	x + 2y + z &=& 2 \\
	3x + 8y + z &=& 12 \\
	 4y + z &=& 2
	\end{array}
\right.
$$
transform it to a $Ax=b$ format:
$$
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		3 & 8 & 1 \\
		0 & 4 & 1
	\end{matrix}
\right]
\left[
	\begin{matrix}
		x \\
		y \\
		z
	\end{matrix}
\right]
=
\left[
	\begin{matrix}
		2 \\
		12 \\
		2
	\end{matrix}
\right]
$$
following is the detail steps of elimination:
$$
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		3 & 8 & 1 \\
		0 & 4 & 1
	\end{matrix}
\right]
\stackrel{E_{21}}
\Longrightarrow
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		0 & 2 & -2 \\
		0 & 4 & 1
	\end{matrix}
\right]
\stackrel{E_{32}}
\Longrightarrow
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		0 & 2 & -2 \\
		0 & 0 & 5
	\end{matrix}
\right]
$$
where the $E_{21}$ and $E_{32}$ are permutation matrix.

### solution

To solve the equations, we need add the vector $b$ in the matrix $A$, they form a augment matrix like this:
$$
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 2 & 1 \\
            3 & 8 & 1 \\
            0 & 4 & 1
        \end{matrix}&
        \begin{matrix}
            2 \\
            12 \\
            2
        \end{matrix}
	\end{array}
\right]
$$
Now, we do elimination:
$$
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 2 & 1 \\
            3 & 8 & 1 \\
            0 & 4 & 1
        \end{matrix}&
        \begin{matrix}
            2 \\
            12 \\
            2
        \end{matrix}
	\end{array}
\right]
\stackrel{E_{21}}
\Longrightarrow
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 2 & 1 \\
            0 & 2 & -2 \\
            0 & 4 & 1
        \end{matrix}&
        \begin{matrix}
            2 \\
            6 \\
            2
        \end{matrix}
	\end{array}
\right]
\stackrel{E_{21}}
\Longrightarrow
\left[
	\begin{array}{c:c}
        \begin{matrix}
            1 & 2 & 1 \\
            0 & 2 & -2 \\
            0 & 0 & 5
        \end{matrix}&
        \begin{matrix}
            2 \\
            6 \\
            -10
        \end{matrix}
	\end{array}
\right]
$$
then back substitute the coefficients to the equations:
$$
\left\{
	\begin{array}{rl}
	x + 2y + z &=& 2 \\
	2y - z &=& 6 \\
	5z &=& -10
	\end{array}
\right.
$$
finally we got the solution is $\left[\begin{matrix}2 \\1 \\-2\end{matrix}\right]$.

## Elimination matrix

### row vector multiple a matrix

Above is an simple raw exchange example for elimination so that you can have a intuitional understand of elimination, here we will show a more systematic way about exchange matrix.

We know that matrix multiple a vector(specific a column vector) is about columns' combination of the matrix in lecture 1, but we do raw operation in elimination, so let's consider how about vector(specific a row vector) multiple a matrix:
$$
\left[
	\begin{matrix}
		1 & 2 & 7
	\end{matrix}
\right]
\left[
	\begin{matrix}
		? & ? & ? \\
		? & ? & ? \\
		? & ? & ?
	\end{matrix}
\right]
=
\text{the combinations of the row of the matrix}
$$

### elimination matrix

**elimination matrix:** format the row operations of one matrix to a matrix multiplication form.

Look at the elimination process in section 1:
$$
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		3 & 8 & 1 \\
		0 & 4 & 1
	\end{matrix}
\right]
\stackrel{E_{21}}
\Longrightarrow
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		0 & 2 & -2 \\
		0 & 4 & 1
	\end{matrix}
\right]
\stackrel{E_{32}}
\Longrightarrow
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		0 & 2 & -2 \\
		0 & 0 & 5
	\end{matrix}
\right]
$$
It takes two steps to finish the elimination work:

- row2 minus three times row1, so the $E_{21}=\left[\begin{matrix} 1&0&0 \\ -3&1&0 \\ 0&0&1\end{matrix}\right]$
- then, row3 minus two times row2, so the $E_{32}=\left[\begin{matrix}1&0&0 \\ 0&1&0 \\ 0&-2&1\end{matrix}\right]$

which is:
$$
\left[\begin{matrix} 1&0&0 \\ 0&1&0 \\ 0&-2&1\end{matrix}\right]
\cdot
\left[\begin{matrix} 1&0&0 \\ -3&1&0 \\ 0&0&1\end{matrix}\right]
\cdot
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		3 & 8 & 1 \\
		0 & 4 & 1
	\end{matrix}
\right]
=
\left[
	\begin{matrix}
		1 & 2 & 1 \\
		0 & 2 & -2 \\
		0 & 0 & 5
	\end{matrix}
\right]
$$
Summary,
$$
E_{32}
\cdot
E_{21}
\cdot
A
=
U
\text{(an upper triangular matrix)}
$$

## inverse matrix

Now we know how to use matrix multiplication to do matrix exchange, we consider a inverse process: how to get the original matrix $A$ from the eliminated matrix $U$?

Answer: use inverse matrix.

Define: if exist a matrix satisfy that,
$$
A \cdot A^{-1} = I = A^{-1} \cdot A
$$
we call matrix $A^{-1}$ is the inversion of matrix $A$ and matrix $A$ is invertible.

