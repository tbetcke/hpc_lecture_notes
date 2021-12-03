# Assignment 4 - Time-dependent problems

**Submission Deadline: We 15 December, 10am**

Consider a square plate with sides $[−1, 1] × [−1, 1]$. At time t = 0 we are heating the plate up
such that the temperature is $u = 5$ on one side and $u = 0$ on the other sides. The temperature
evolves according to $u_t = \Delta u$. At what time $t^*$ does the plate reach $u = 1$ at the center of the plate?
Implement a finite difference scheme and try with explicit and implicit time-stepping. By increasing
the number of discretisation points demonstrate how many correct digits you can achieve. Also,
plot the convergence of your computed time $t^*$ against the actual time. To 12 digits the wanted
solution is $t^* = 0.424011387033$.

A GPU implementation of the explicit time-stepping scheme is not necessary but would be expected for a very high mark beyond 80%.