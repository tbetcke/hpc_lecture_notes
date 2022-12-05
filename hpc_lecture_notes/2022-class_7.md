# Class 7 (Monday 5 December)

These tasks are designed to be worked on in the practical class on Monday 5 December.

## LU for a tridiagonal matrix
In Friday's lecture, we computed the LU factorisation of a dense matrix.
The code we wrote during Friday's lecture can be found [at this link](https://gist.github.com/mscroggs/7c1b4440942fa48fe4a8cab0b9cb4a49).
In today's class, we are going to compute the LU decomposition of a tridiagonal matrix.

We will use the following $n$ by $n$ matrix:

$$
\mathrm{A}=\begin{pmatrix}
a_0&-1&0&0&\cdots&0\\
-1&a_1&-1&0&\cdots&0\\
0&-1&a_2&-1&\cdots&0\\
0&0&-1&a_3&\cdots&0\\
\vdots&\vdots&\vdots&\vdots&\ddots&\vdots\\
0&0&0&0&\cdots&a_{n-1}\\
\end{pmatrix},
$$
where $a_0$ to $a_{n-1}$ are random decimal values between 5 and 10.

Write a function that takes $n$ as an input and returns the matrix $\mathrm{A}$ stored in a sparse format of your choice.

Using [the code we wrote in Friday's lecture](https://gist.github.com/mscroggs/7c1b4440942fa48fe4a8cab0b9cb4a49) as a template,
write a function that computes the LU decomposition of $\mathrm{A}$, and returns the factors $\mathrm{L}$ and $\mathrm{U}$ in a 
sparse format of your choice. Due to the structure of the matrix, you should not need to do any permuting of the rows.

For a range of values of $n$, compute the LU decomposition using your function and measure the time this takes.
Convert each matrix to a dense matrix and compute the LU decomposition using the code we wrote in Friday's lecture, timing
this too.
Plot these timings on log-log axes. What do you notice?
