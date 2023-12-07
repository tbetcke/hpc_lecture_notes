# Assignment 4 - Time-dependent problems

This assignment makes up 30% of the overall marks for the course. The deadline for submitting this assignment is **5pm on 14 December 2023**.

Coursework is to be submitted using the link on Moodle. You should submit a single pdf file containing your code, the output when you run your code, and your answers
to any text questions included in the assessment. The easiest ways to create this file are:

- Write your code and answers in a Jupyter notebook, then select File -> Download as -> PDF via LaTeX (.pdf).
- Write your code and answers on Google Colab, then select File -> Print, and print it as a pdf.

Consider a square plate with sides $[−1, 1] × [−1, 1]$. At time t = 0 we are heating the plate up
such that the temperature is $u = 5$ on one side and $u = 0$ on the other sides. The temperature
evolves according to $u_t = \Delta u$. At what time $t^*$ does the plate reach $u = 1$ at the center of the plate?
Implement a finite difference scheme and try with explicit and implicit time-stepping. Numerically investigate the stability of your schemes.
By increasing the number of discretisation points demonstrate how many correct digits you can achieve. Also,
plot the convergence of your computed time $t^*$ against the actual time. To 12 digits the wanted
solution is $t^* = 0.424011387033$.

A GPU implementation of the explicit time-stepping scheme is not necessary but would be expected for a very high mark beyond 80%.
