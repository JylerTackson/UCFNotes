Simpsons rule is a numerical integration technique that approximates the integral of a function by using parabolic segments to approximate the area under the curve.

Formula for one segment:
$$
\begin{align}
\int_{x_2}^{x_4}f(x)dx\simeq&\; \frac{(x_4-x_2)}{6}\left[ f(x_2) + 4f\left(\frac{x_2+x_4}{2}\right) + f(x_4) \right]\\
\simeq&\; \frac{(x_4-x_2)}{6}\left[ f(x_2) + 4f(x_3) + f(x_4) \right]
\end{align}
$$
When using Simpsons rule for multiple segments, the method divides the interval into an even number of sub-intervals creating a more general formula:
$$
S_n \simeq \frac{\Delta x}{3} 
\left(
f(x_0) + 4f(x_1) + 2f(x_2) + 4f(x_3) + 2f(x_4) + ... + 2f(x_{n-2}+ 4f(x_{n-1}) + f(x_n)
\right)
$$
**Steps:**
1) Divide the interval $[a,b]$ into $n$ subintervals of width $h=\frac{b-a}{n}$
2) Evaluate the function at the endpoints of each subinterval
3) Approximate the integral as:
$$
\int_a^b f(x)dx \simeq \frac{h}{3} \left\{ [f(a)+f(b)] + ... 4\sum f(\text{odd midpoints}) + 2\sum f(\text{even midpoints}) \right\}
$$
4) Increase $n$ for higher accuracy
