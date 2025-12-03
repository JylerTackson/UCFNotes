The Crank-Nicolson Method is a numerical technique for solving parabolic partial differential equations. This method is based on the trapezoidal rule for time integration, combining explicit and implicit methods.

Formula for a 1D heat equation:
$$
u_j^{n+1} = u_j^n+r\left[ \left(u_{j+1}^n - 2u_j^n + u_{j-1}^n\right) + \left(u_{j+1}^{n+1} - 2u_{j}^{n+1} + u_{j-1}^{n+1}\right) \right]
$$
Where:
- $r={\alpha}\;\frac{\Delta t}{\Delta x^2}$
- $j\to$ space index
- $i\to$ time index
This formula is **unconditionally stable** and **second-order accurate** in both time and space. This means it remains stable regardless of the choice of $\Delta t$ or $\Delta x$. However for nonlinear PDE's the stability depends on the problem setup.

**Example:**
Solve $\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}$ on the domain $[0,1]$ with $\Delta x = 0.1$, $\alpha=0.1$, $\Delta t = 0.05$

To begin you want to start by solving for $r$ using the equation and constants provided:
$$
r={\alpha}\;\frac{\Delta t}{\Delta x^2}={0.1}\frac{0.05}{0.1^2}=5
$$
