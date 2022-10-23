# Assignment 2 - Solving a wave problem

This assignment makes up 20% of the overall marks for the course. The deadline for submitting this assignment is **5pm on Thursday 4 November 2022**.

Coursework is to be submitted using the link on Moodle. You should submit a single pdf file containing your code, the output when you run your code, and your answers
to any text questions included in the assessment. The easiest ways to create this file are:

- Write your code and answers in a Jupyter notebook, then select File -> Download as -> PDF via LaTeX (.pdf).
- Write your code and answers on Google Colab, then select File -> Print, and print it as a pdf.

Tasks you are required to carry out and questions you are required to answer are shown in bold below.

## The assignment

In this assignment, we want to compute the solution to the following (time-harmonic) wave problem:

$$
\begin{align*}
\frac{\mathrm{d}^2 u}{\mathrm{d}x^2} + k^2u &= 0&&\text{in }(0, 1),\\
u &= 0&&\text{if }x=0,\\
u &= 1&&\text{if }x=1,\\
\end{align*}
$$
with wavenumber $k=13\mathrm{\pi}/2$.

### Part 1: Solving with finite differences and sparse matrices
In this part, we will approximately solving this problem using the method of finite differences.
We do this by taking an evenly spaced values
$x_0=0, x_1, x_2, ..., x_N=1$
and approximating the value of $u$ for each value: we will call these approximations $u_i$.
To compute these approximations, we use the approximation

$$
\frac{\mathrm{d}^2u_{i}}{\mathrm{d}x^2} \approx \frac{
2u_i-u_{i-1}-u_{i+1}
}{h},
$$
where $h = 1/N$.

With a bit of algebra, we see that the wave problem can be written as

$$
(2+hk^2)u_i-u_{i-1}-u_{i+1} = 0
$$
if $x_i$ is not 0 or 1, and

$$
\begin{align*}
u_i &= 0
&&\text{if }x_i=0,\\
u_i &= 1
&&\text{if }x_i=1.
\end{align*}
$$

This information can be used to re-write the problem as the matrix-vector problem
$\mathrm{A}\mathbf{u}=\mathbf{f},$
where $\mathrm{A}$ is a known matrix, $\mathbf{f}$ is a known vector, and $\mathbf{u}$ is an unknown vector that we want to compute.
The entries of 
$\mathbf{f}$ and $\mathbf{u}$ are given by

$$
\begin{align*}
\left[\mathbf{u}\right]_i &= u_i,\\
\left[\mathbf{f}\right]_i &= \begin{cases}
1&\text{if }x_i=1,\\
0&\text{otherwise}.
\end{cases}
\end{align*}
$$
The rows of $\mathrm{A}$ are given by

$$
\left[\mathrm{A}\right]_i = 
\begin{cases}
1&\text{if }k=i,\\
0&\text{if }\text{otherwise},
\end{cases}
$$
if $i=0$ or $i=N$; and

$$
\left[\mathrm{A}\right]_{iN+j, k} = 
\begin{cases}
2+hk^2&\text{if }k=i,\\
-1&\text{if }k=i+1,\\
-1&\text{if }k=i-1.\\
0&\text{otherwise},
\end{cases}
$$
otherwise.

**Write a Python function that takes $N$ as an input and returns the matrix $\mathrm{A}$ and vector $\mathrm{f}$**.
You should use an appropriate sparse storage format for the matrix $\mathrm{A}$.

The function `scipy.sparse.spsolve` can be used to solve a sparse matrix-vector problem. Use this to **compute
the approximate solution for your problem for $N=10$, $N=100$, and $N=1000$**. Use `matplotlib` (or any other plotting library)
to **plot the solutions for these three values of $N$**.
You may wish to time your functions at this point, as you will need these timings later.

**Briefly (1-2 sentences) comment on your plots**: How different are they to each other? Which do you expect to be closest to the
actual solution of the wave problem?

### Part 2: Iterative method with GPU acceleration
The equation $(2+hk^2)u_i-u_{i-1}-u_{i+1} = 0$ (that we worked out above) can be rewritten as

$$
u_i=\frac{u_{i-1}+u_{i+1}}{2+hk^2}.
$$

We can use this to formulate an iterative method for computing an approximation of $u$. We first pick an "inital guess" for the values of
$u_i$:

$$
u^{(0)}_i = \begin{cases}
1&\text{if }i=N,\\
0&\text{otherwise}.
\end{cases}
$$
We then compute the next guess for the values of $u_i$ using

$$
u^{(n+1)}_i &=
\begin{cases}
0&\text{if }i=0,\\
1&\text{if }i=N,\\
\displaystyle\frac{u^{(n)}_{i-1}+u^{(n)}_{i+1}}{2+hk^2}&\text{otherwise}.
\end{cases}
$$

**Implement this iterative scheme in Python, using `numba.cuda` to parallelise your implementation on a GPU.**
You should think carefully about which values need to be copied between thread blocks, and which values can be kept in
local memory, and be careful not to copy data to/from the GPU when not needed.

You will need to pick a sensible number of iterations to complete to get your approximate solution:
too few iterations and your solution will be inaccurate; too many iterations and your solution will take longer to compute.
**Briefly (1-2 sentences) comment on how you pick the number of iterations or when you decide to stop iterating.**

**Compute the approximate solution for your problem for $N=10$, $N=100$, and $N=1000$**. Use `matplotlib` (or any other plotting library)
to **plot the solutions for these three values of $N$**.
You may wish to time your functions at this point, as you will need these timings later.

**Briefly (1-2 sentences) comment on your plots**: How do they compare to the plots from part 1?

### Part 3: Comparing errors and timings
The problem above was carefully chosen so that its exact solution is known: this solution is
$u_\text{exact}(x) = \sin(13{\pi}x/2)$. (You can check this by differentiating this twice and substituting, but you
do not need to do this part of this assignment.)

A possible approximate measure of the error in your solution can be found by computing

$$
\max_i\left|u_i-u_\text{exact}(x_i)\right|.
$$
**Compute this error for $N=10$, $N=100$, and $N=1000$ for your solutions computed in both parts 1 and 2**. On axes that both use log scales,
**plot $N$ against the error in your solution.**

**Measure the time taken to compute your approximations in parts 1 and 2**. On axes that both use log scales,
**plot $N$ against the time taken to compute a solution.**

We now want to compute an approximate solution for $N=1000$. By looking at your two plots, **decide which of the two methods you think would be best for this
larger computation**. **Briefly (2-3 sentences) explain why you think the method you have picked is the better choice.**

**Compute the approximate solution with $N=1000$ using the method your have picked**, and **add the time taken and the error of the solution to the two plots you
made**.
