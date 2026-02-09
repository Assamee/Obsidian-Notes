# Standard Maclaurin Expansions

**Maclaurin Series** = A Taylor series expansion of a function $f(x)$ about the point $a=0$. It is given by the power series $\sum_{n=0}^{\infty}{{\frac{f^{(n)}(0)}{n!}}{x^n}}$

- Simple Explanation: A way of turning functions into an infinite sum of simple powers of $x (1,x,x^2,...)$ all centred at zero. 
***
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
***
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
***
### Algebraic Operations:
For questions like $(\frac{sin(x)}{1-3x})$ that combine multiple series:
- Treat the original function as a product of multiple functions $f(x)g(x)$
	- Find the series expansion for each sub-function individually and multiply them together
***
# General Taylor Series
- To be used when the question asks for an expansion "about $x =a$" (where $a \neq 0$)
**Complex Definition:**
- Let $f$ be indefinitely differentiable at $a$. 
- The Taylor Series of $f$ about $a$ is the power series $\sum_{n=0}^{\infty}{{\frac{f^{(n)}(a)}{n!}}{(x-a)^n}}$
**Simple Explanation:**
- A method to approximate a curve near a specific point $a$ (the "base point") rather than zero.
- Instead of powers of $x$, we use powers of the distance from the base point $(x-a)$
***
### Formula:
The Taylor Series of $f$ about point $a$:
$$f(x) \approx f(a) + f'(a)(x-a) + {\frac{f''(a)}{2!}}{(x-a)^2} + \dots + {\frac{f^{(N)}(a)}{N!}}{(x-a)^N}$$
###### Example:
For $f(x) = \ln(x)$ about $a=1$ (degree 2):
- $f(x) = \ln(x) \rightarrow f(1) = 0$
- $f'(x) = 1/x \rightarrow f'(1) = 1$
- $f''(x) = -1/x^2 \rightarrow f''(1) = -1$
**Result:** $P_2(x) = 0 + 1(x-1) + \frac{-1}{2}(x-1)^2$
Note that $P_2(x)$ means the polynomial (degree 2) with respect to $x$
***
### Langrage Remainder (Error Analysis):
- The Taylor polynomial $P_N(x)$ is just an approximation
- The "Remainder" $(R_{N+1})$ is the exact error difference between the approximation and the real function
#### The Theorem:
$$f(x) = P_{N,a}(x) + R_{N+1,a}(x)$$
$f(x) =$ (Taylor Polynomial of Degree $N$ centred at $a$) + (Remainder Term)
#### The Lagrange Form Formula:
$R_{N+1}(x)$ is the $N$th **remainder term**
$$R_{N+1}(x) = \frac{f^{(N+1)}(\xi)}{(N+1)!}(x-a)^{N+1} \text{ for some } \xi \, \in \, (x,a)$$
for some value $\xi$ in the interval between $a$ and $x$
- The error in the approximation $(R)$ is determined by the **next derivative** $f^{(N+1)}$ at some unknown point $(\xi)$, multiplied by the distance from the centre $(x-a)$, and divided by a huge factorial number
- We cannot calculate the exact value of $\xi$, instead we assume the **worst-case scenario** (the maximum possible value the derivative could have between $a$ and $x$)
#### Bounding the Error ('Worst-Case Scenario'):
Since we cannot calculate the exact value of $\xi$, we find the **maximum possible error** (an upper bound). 
1. **Write the Formula:** Write down $R_{N+1}(x)$, leaving $\xi$ inside the derivative
2. **Maximise the Derivative:** After differentiating $f^{N+1}$, look at the term $|f^{(N+1)}(\xi)|$. Find the maximum value $(M)$ this term could possibly take for any number $\xi$ in the integral $(a,x)$. 
	- *Tip:* For $\sin(\xi)$ or $\cos(\xi)$, the max is always $1$.
	- *Tip:* For increasing functions like $e^{\xi}$, the max is at the larger end of the interval
3. **Substitute and Solve:** Replace $f^{(N+1)}(\xi)$ with $M$ to form the inequality:
$$|R_{N+1}(x)| \leq \frac{M}{(N+1)!}|x-a|^{N+1}$$
 



