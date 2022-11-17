# Assignment 3 - Sparse matrices

This assignment makes up 30% of the overall marks for the course. The deadline for submitting this assignment is **5pm on Thursday 1 December 2022**.

Coursework is to be submitted using the link on Moodle. You should submit a single pdf file containing your code, the output when you run your code, and your answers
to any text questions included in the assessment. The easiest ways to create this file are:

- Write your code and answers in a Jupyter notebook, then select File -> Download as -> PDF via LaTeX (.pdf).
- Write your code and answers on Google Colab, then select File -> Print, and print it as a pdf.

Tasks you are required to carry out and questions you are required to answer are shown in bold below.

## The assignment

### Part 1: Implementing a CSR matrix

```
from scipy.sparse import LinearOperator


class CSRMatrix(LinearOperator):
    def __init__(self, coo_matrix):
        pass

    def __add__(self, other):
        """Add the CSR matrix other to this matrix."""
        pass

    def matvec(self, vector):
        """Compute a matrix-vector product."""
        pass
```

**Implement the methods `__init__`, `__add__` and `matvec`.**

**Write a test to check that `__add__` and `matvec` are correct.**

**Time `matvec`, compared to a dense matrix**. TODO: for which matrix?

### Part 2: Implementing a ... matrix
From that paper?
