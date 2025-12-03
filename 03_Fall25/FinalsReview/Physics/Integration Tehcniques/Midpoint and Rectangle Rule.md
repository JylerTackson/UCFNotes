**The rectangle rule**, aka Riemann sum, is an integration technique that approximates the are under the curve using the area of a rectangle. The accuracy of this method increases with the number of rectangles employed.

**The Midpoint Rule** is an integration technique that approximates the integral of a function by using the value of the function at the midpoint of an interval to estimate the area under the curve.

Formula for one interval: 
$$
\int_a^b f(x)dx \approx (b-a)f\left(\frac{a+b}{2}\right)
$$
For multiple sub intervals, the method sums the areas of all sub intervals, to create a more general formula:
$$
\int_a^b f(x) dx \approx M_n = \Delta x 
\left[
f(\bar{x_1}) + f(\bar{x_2}) + ... + f(\bar{x_n})
\right]
$$
Where:
- $\Delta x = \frac{b-a}{n}$
- $\bar{x_i}=\frac{1}{2}(x_{i-1} + x_i)=$ midpoint of $[x_{i-1},x_i]$

**Steps:**
1) Divide the interval $[a,b]$ into $n$ subintervals of width $h=\Delta x$
2) Compute the midpoints of each subinterval
3) Evaluate the function at each midpoint
4) Approximate the integral as:
$$
\int_a^b f(x) dx \approx M_n = \Delta x 
\sum f (\text{midpoints})
$$
Provides higher accuracy, **second-order**, compared to rectangle rule.