Forward Euler is a technique for solving the initial value problems of Ordinary differential equations. It approximations the solution using a first-order Taylor Expansion:
$$
y_{n+1}\simeq y_n + f(x_n, y_n)\Delta t
$$
**Steps:**
1) Start with the initial values $x_0$ and $y_0$
2) Define your step size $h$.
3) Iterate using the following formulas:
$$
\begin{align}
\tag{Range}
y_{n+1}\simeq&\; y_n + hf(x_n, y_n)\Delta t\\\\
\tag{Domain}
x_{n+1} \simeq &\; x_n +  h
\end{align}
$$
4) Repeat until the desired $x$ value is reached
Forward Euler is a low accuracy, **first-order method**, that requires small step sizes.

---
Backwards Euler is an implicit numerical technique for solving ODE's, it operates by using the value of the function at the next time step to update the solution.
$$
y_{n+1}\simeq y_n + hf(x_{n+1}, y_{n+1})
$$
**Steps:**
1) Start with the initial values $x_0$ and $y_0$
2) Choose step size $h$
3) For each time step, solve the equation
$$
y_{n+1}\simeq y_n + hf(x_{n+1}, y_{n+1})
$$
4) Use a numerical method, such as newtons method, to computer $y_{n+1}$
Unconditionally stable, suitable for stiff equations, and provides more accurate solutions for larger time steps than the Forward Euler.