Trapezoid rule is a numerical integration technique to approximate the integral of a function. It does this by dividing the interval into trapezoids and summing their areas.

Its important to recall the area of a trapezoid:
$$
A=\frac{b_1+b_2}{2}h
$$
The formula for one interval is:
$$
\int_a^b f(x)dx \simeq h\frac{[f(a)+f(b)]}{2}
$$
Where:
- $h=\frac{b-a}{n}$

**Steps:**
1) Divide the interval $[a,b]$ into $n$ subinterval's of width $h$
2) Evaluate the function at the endpoints of each subinterval
3) Approximate the integral as follows:
$$
\int_a^b f(x)\,dx \approx \frac{h}{2}\left[f(a) + 2\sum_{k=1}^{n-1} f(x_k) + f(b)\right]
$$
4) Increase $n$ for higher accuracy
Provides higher accuracy, second-order compared to rectangular rule.
