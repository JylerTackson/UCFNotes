**Forward Difference** is a numerical method for approximating the derivative of a function. It is based on the definition of a derivative taught in Calc 1:
$$
f^\prime (x) \approx \frac{(f(x+h)-f(x))}{h}
$$
**Steps:**
1) Initialize a step size $h$
2) Evaluate the function $f(x)$ at both $x$ and $x+h$
3) Compute the derivative approximation using the forward difference scheme:
 $$
f^\prime (x) \approx \frac{(f(x+h)-f(x))}{h}
$$
Error is proportional to the step size $h$ and this scheme provides **first-order** accuracy.
---
**Backward Difference** is a numerical method for approximating the derivative of a function. This method uses the function value at the POI and the point before it:
$$
f^\prime (x) \approx \frac{f(x)-f(x-h)}{h}
$$
**Steps:**
1) Initialize a step size $h$
2) Evaluate the function $f(x)$ at both $x$ and $x-h$
3) Compute the derivative approximation using the backward difference scheme:
 $$
f^\prime (x) \approx \frac{f(x)-f(x-h)}{h}
$$
Error is proportional to the step size $h$ and this scheme provides **first-order** accuracy.
---
Centered Difference is a numerical method for approximating the derivative of a function. This method uses points on both sides of the POI.
$$
f^\prime (x) \approx \frac{f(x+h)-f(x-h)}{2h}
$$**Steps:**
1) Initialize a step size $h$
2) Evaluate the function $f(x)$ at both $x+h$ and $x-h$
3) Compute the derivative approximation using the backward difference scheme:
 $$
f^\prime (x) \approx \frac{f(x+h)-f(x-h)}{2h}
$$
This method provides **second-order** accuracy meaning it is more accurate then both Forward and backwards difference.