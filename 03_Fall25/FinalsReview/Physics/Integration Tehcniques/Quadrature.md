Gaussian Quadrature is a numerical integration technique that evaluates the integral of a function. It approximates the integral using a weighted sum of function values at specific points using the following form:
$$
\int_a^b f(x)dx\simeq \sum w_i f(x_i)
$$
The points $x_i$ and weights $w_i$ are chosen to maximize accuracy for polynomials up to degree $2n-1$

#### One-Point Quadrature
The simplest gaussian quadrature rule:
$$
\int_a^b f(x)dx\simeq c_1 f(x)
$$
Where:
- $c_1\to$ is a weight
- $x\to$ a quadrature point

One-Point Quadrature that is accurate for constant functions:
$$
\int_a^b f(x)dx\simeq(b-a)f\left(\frac{b+a}{2}\right)
$$
One-Point Quadrature is accurate for constant functions of degree $\leq 1$ and for general intervals $[a,b]$
#### Two-Point Quadrature
This method uses two Quadrature points and weights for better accuracy; the simplest rule:
$$
\int_{a}^b f(x)dx\simeq c_1 f(x_1) + c_2 f(x_2)
$$
The Two-Point Quadrature is accurate for polynomials up to degree $3(2n-1)$, for general intervals $[a,b]$

They both have high accuracy for polynomials of specified degrees and require fewer function evaluations compared to other methods.