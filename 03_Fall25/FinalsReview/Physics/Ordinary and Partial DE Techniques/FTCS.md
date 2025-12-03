FTCS is a numerical method for solving partial differential equations. It combines the Forward Euler method for time discretization with the Central Difference method for spatial discretization.

Begin with the 1D heat equation
$$
u_j^{n+1}=u_j^n+r(u_{j+1}^n -2u_j^n+u_{j-1}^n)
$$
Where:
- $r={\alpha}\;\frac{\Delta t}{\Delta x^2}$
- $j\to$ space index
- $i\to$ time index

Steps:
1) Discretize the spatial domain into grid points with spacing $\Delta x$
2) Choose a time step $\Delta t$ such that the stability condition is met.
3) Initialize the solution $uj^n$ at all grid points
4) Use the FTCS formula to compute $u_{n+1}^i$ at each time step
5) Repeat until the desired final time is reached

Using FTCS solve the following 1D diffusion equation on the spatial domain $[0,1]$ with $\Delta x = 0.2$ and time step of $0.01$. Let $\alpha=0.5$.
$$
\frac{\partial u}{\partial t}=\alpha \frac{\partial^2 u}{\partial x^2}
$$
Given an initial condition of $u(x,0)=sin(\pi x)$, compute the value of $u$ at $t=0$ and $0.01$ seconds.