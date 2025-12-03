Bisection Method is a numerical method for finding roots of a real-valued function. This method requires an interval $[a,b]$  where $f(a)$ and $f(b)$ have opposite signs. The interval is halved iteratively until the root is approximated.

**Steps:**
1) Choose $x_a$ and $x_b$ as two guesses for the root s.t. $f(x_a)f(x_b)<0$, or in other words, $f(x)$ changes sign between $x_a$ and $x_b$
2) Estimate the root $x_r$ of the equation $f(x)=0$ as the mid point between $a,b$
$$
x_r=\frac{x_a+x_b}{2}
$$
3) Check for the following cases:
	1) If $f(x_\ell)f(x_m) < 0$ then the root lies between $x_\ell$ and $x_m$.  
	   Update bounds: $x_\ell = x_\ell,\; x_u = x_m.$
	
	2) If $f(x_\ell)f(x_m) > 0$ then the root lies between $x_m$ and $x_u$.  
	   Update bounds: $x_\ell = x_m,\; x_u = x_u.$
	
	3) If $f(x_\ell)f(x_m) = 0$ then the root is $x_m$.  
	   Stop the algorithm if this occurs.
4) Find the new estimate of the root:
5) Compare error