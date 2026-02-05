# Standard Maclaurin Expansions

**Maclaurin Series** = A Taylor series expansion of a function $f(x)$ about the point $a=0$. It is given by the power series $\sum_{n=0}^{\infty}{{\frac{f^{(n)}(0)}{n!}}{x^n}}$

- Simple Explanation: A way of turning functions into an infinite sum of simple powers of $x (1,x,x^2,...)$ all centred at zero. 

### Standard Maclaurin Expansions to Memorise:
#### Geometric Series:
$$\frac{1}{1-x} = 1 + x + x^2 + x^3 + \text{ } ... \text{ } = \sum_{n=0}^{\infty}{x^n} \text{ for } |x| \lt 1$$
	Geometric Series (General Form):
	$$\text{Sum } = \frac{a}{1-r} = a + ar + ar^2 + ... =\sum_{n=0}^{\infty}{ar^n}$$$$a = \text{ first term, } r = \text{ common ratio (The common ratio normally includes an }x \text)$$
#### Exponential Function:
$$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \text{ }... \text{ for all } x$$
#### Sine (Odd powers, alternating signs):
$$sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \text{ } ... \text{ for all } x$$
#### Cosine (Even powers, alternating signs):
$$cos(x) = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \text{ } ... \text{ for all } x$$
#### Logarithms:
$$\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \text{ } ... \text{ for } |x| \lt 1 $$
### Substitution:
For functions that are similar to standard forms you can use substitution e.g. $\left( e^{-3x} \right)$
**Example: Finding the series for $e^{-3x}$**
- **Standard Series:** $e^u = 1 + u + \frac{u^2}{2!} + \dots$
- **Substitute:** Let $u = -3x$:
$$e^{-3x} = 1 + (-3x) + \frac{(-3x)^2}{2!} + \frac{(-3x)^3}{3!} + \dots$$
- **Calculate Powers:**
$$e^{-3x} = 1 - 3x + \frac{9x^2}{2} - \frac{27x^3}{6} + \dots$$
**Note on Limits:**
- If the original series converges for $| x | \lt 1$, the new series converges for $| u | \lt 1$
- *Example:* $\frac{1}{1 + w^2}$ converges when $| -w^2 | \lt 1$, which simplifies to $| w | \lt 1$
### Algebraic Operations:
For questions like $(\frac{sin(x)}{1-3x})$ that combine multiple series:
- Treat the original function as a product of multiple functions $f(x)g(x)$
	- Find the series expansion for each sub-function individually and multiply them together
# General Taylor Series
