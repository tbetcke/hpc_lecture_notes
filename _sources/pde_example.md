# The need for sparse linear algebra - A PDE example

In modern applications we are dealing with matrices that have
hundreds of thousands to billions of unknowns. A typical feature
of these matrices is that they are highly sparse. Typically, by
sparsity we mean that a matrix mostly consists of zero elements so
that it is more economical not to store the whole matrix, but just
the nonzero entries. This makes necessary different types of storage
structures and algorithms to deal with these matrices and to efficiently
exploit the sparsity property.

Before we dive into sparse matrix storage format, we want to give a simple
example that demonstrates the necessity of sparse matrix formats and
algorithms to deal with them.

## Solving a Poisson problem on the unit square.

We consider the 