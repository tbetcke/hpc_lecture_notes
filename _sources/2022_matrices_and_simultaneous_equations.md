# Matrices and simultaneous equations
It is common to rewrite systems of sumultaneous equations as a matrix-vector problem. For example, the equations

$$
\begin{align*}
4a_0 + 3a_1 &= 2\\
a_0 - a_3 &= 1\\
-a_2 - a_3 &= 0\\
2a_0 &= 1
\end{align*}
$$

can be written as the matrix-vector problem

$$
\begin{pmatrix}
4&3&0&0\\
1&0&-1&0\\
0&0&-1&-1\\
2&0&0&0
\end{pmatrix}
\begin{pmatrix}
a_0\\a_1\\a_2\\a_3
\end{pmatrix}
=
\begin{pmatrix}
2\\1\\0\\1
\end{pmatrix}
$$
