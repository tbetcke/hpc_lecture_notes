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
\end{pmatrix}.
$$

By multiplying out the matrix, you can see that each row of the matrix paired with one entry in the vector represents one of the simultaneous equations.

This is what I did in the lecture with the (more complicated) equations

$$
\begin{align*}
u_{i,j} &= 0&&\text{if the point is on the boundary},\\
\frac{4u_{i,j}-u_{i+1,j}-u_{i-1,j}-u_{i,j+1}-u_{i,j-1}}{h^2} &= 1&&\text{otherwise},
\end{align*}
$$

to get the matrix problem

$$
\mathrm{A}
\begin{pmatrix}
u_{0,0}\\
u_{1,0}\\
u_{2,0}\\
\vdots
u_{N,0}\\
u_{0,1}\\
u_{1,1}\\
u_{2,1}\\
\vdots
u_{N,N}\\
\end{pmatrix}
=\mathbb{b}.
$$
