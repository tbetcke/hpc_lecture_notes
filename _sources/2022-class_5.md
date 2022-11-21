# Class 5 (Monday 14 November)

These tasks are designed to be worked on in the practical class on Monday 14 November.

## Using GMRES
You can create an identity matrix ($\mathrm{I}$) with Numpy by running:
```python
identity_matrix = np.eye(N)
```

Solve $\mathrm{I}\mathbf{x}=\mathrm{b}$ for a random vector $\mathbf{b}$ using GMRES (`scipy.sparse.linalg.gmres`).
Make a plot showing the number of iterations vs the size of the residual.

## Experimenting with GMRES
You can create a random matrix ($\mathrm{A}$) with Numpy by running:
```python
a_matrix = np.random.randn(N, N) / np.sqrt(N)
```

Solve $\mathrm{A}\mathbf{x}=\mathrm{b}$ for a random vector $\mathbf{b}$ using GMRES.
Make a plot showing the number of iterations vs the size of the residual.
Compare this plot to the plot for the identity matrix.

You can control the stopping criteria of GMRES by passing `tol` and `atol` parameters into GMRES (eg `scipy.sparse.linalg.solve(A, b, tol=1e-8, atol=1e-8)`).
Adjust these parameters so that GMRES gets to a lower residual than the default values. What is the lowest you can get the size of the residual to be?

Consider the matrix $\mathrm{A}+\alpha\mathrm{I}$ for some constant $\alpha$.
Solve $(\mathrm{A}+\alpha\mathrm{I})\mathbf{x}=\mathrm{b}$ for a random vector $\mathbf{b}$ using GMRES
for a range of values of $\alpha$.
Make a plot showing the number of iterations vs the size of the residual for the value of $\alpha$
that you chose. How is the value of $\alpha$ related to the performance of GMRES.

Have you considered what happens if $\alpha$ is negative? Or complex?

## Plotting eigenvalues
The performance of GMRES is related to the eigenvalues of the matrix. You can plot
the eigenvalues of a matrix `A` with the following code:

```python
from matplotlib import pyplot as plt
from scipy.linalg import eigvals

eigenvalues = eigvals(A)

plt.plot(np.real(eigenvalues), np.imag(eigenvalues), 'rx', markersize=1)
```

Plot the eigenvalues of the matrices you used in the previous section. What do you notice about the eigenvalues
when GMRES does not perform well? Based on your observations, pick a value of $\alpha$ for which you think
GMRES will perform badly, and a value for which you think it will perform well? Make plots
showing the number of iterations vs the size of the residual for these values of $\alpha$. Were your predictions correct?
