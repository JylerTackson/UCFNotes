**Linear Interpolation** is a method for estimating the value of a function at a point between two known points, assuming the function is linear.

Linear Interpolation uses the following formula:
$$
\begin{matrix}
y=y_1+m(x-x_1)&&&m=\frac{y_2-y_1}{x_2-x_1}
\end{matrix}
$$
**Steps:**
1) Identify your known points domain: $(x_2, x_1)$ and range: $(y_2, y_1)$ around your target $x$ value.

2) Substitute the values into the interpolation formula:
$$
y=y_1+m(x-x_1)
$$
3) Compute $y$
4) Repeat for more points.

---
**Bilinear Interpolation** is a method for estimating the value of a function at a point within a 2D grid, using both the direction of $x$ and $y$, using the following formula:
$$
f(x,y)\simeq Q_{11}(1-w_x)(1-w_y) + ... + Q_{21}w_x(1-w_y) + Q_{12}w_y(1-w_x) + Q_{22}w_xw_y
$$
- $Q_{11}\to$ function value at the bottom-left corner $(x_1, y_1)$
- $Q_{21}\to$ function value at the bottom-right corner $(x_2, y_1)$
- $Q_{12}\to$ function value at the top-left corner $(x_1, y_2)$
- $Q_{22}\to$ function value at the top-right corner $(x_2, y_2)$
Where:
$$
\begin{matrix}
w_x=\frac{x-x_1}{x_2-x_1}
&&&
w_y=\frac{y-y_1}{y_2-y_1}
\end{matrix}
$$
**Steps:**
1) Identify the four grid points $(x_{1\to 4}, y_{1\to 4})$ surround the target point $(x,y)$
2) Compute the weights using the formulas:
$$
\begin{matrix}
w_x=\frac{x-x_1}{x_2-x_1}
&&&
w_y=\frac{y-y_1}{y_2-y_1}
\end{matrix}
$$
3) Use the bilinear interpolation formula to estimate your point:
$$
f(x,y)\simeq Q_{11}(1-w_x)(1-w_y) + ... + Q_{21}w_x(1-w_y) + Q_{12}w_y(1-w_x) + Q_{22}w_xw_y
$$
