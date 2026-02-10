# Choosing the Right Test
### $\textbf{Step 1: Divergence Test}$
- $\text{Take the Limit of the term }(a_k)\text{ as }k \rightarrow \infty$
- $\text{Limit} \neq0 \rightarrow \textbf{Divergent}$
- $\text{Limit} = 0 \rightarrow \text{Test is \textbf{Inconclusive} (Move onto the next step)}$
$\textbf{Example:}$
$$\sum_{k=0}^\infty{\frac{k}{k+1}} \rightarrow \lim_{k \rightarrow \infty}{\frac{k}{k+1}} = 1 \ne 0 \therefore \text{The Series Diverges}$$
## $\textbf{Step 2: The ``Standard Series" Check}$
- $\text{Check if the series fits a ``memorised" pattern}$
- $\textbf{Geometric Series: } (\sum{ar^n})$
	- $\textbf{Converges} \text{ if } \left| {r} \right| \lt 1$
	-  $\textbf{Diverges} \text{ if } \left| {r} \right| \gt 1$
- $\textbf{P-Series: } (\sum{\frac{1}{n^p}})$
	- $\textbf{Converges} \text{ if } \left| {p} \right| \gt 1$
	-  $\textbf{Diverges} \text{ if } \left| {p} \right| \leqslant 1$
## $\textbf{Step 3: Deciding which Test to Use}$
- $\text{If the series isn't a Standard Form, look at the algebra of term } a_n \text{, to pick the right test}$

| $\text{If you see this in }a_n$                                                        | $\text{Use this Test}$           | $\text{Reasoning}$                                                                                                                                                                      |
| :------------------------------------------------------------------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Factorials $k!$ or Exponentials $(3^k)$                                                | Ratio Test                       | Ratio Test cancels out factorials perfectly<br>$\left( \text{e.g. } \frac{(n+1)!}{n!} = n +1 \right)$                                                                                   |
| Entire term raised to the  $n^{th}$  power $(...)^k$                                   | Root Test                        | The  $n^{th}$ root $\sqrt[n]{a_n}$  removes the power                                                                                                                                   |
| Rational Functions (Polynomial over Polynomial)<br><br>$\text{e.g. }\frac{n}{n^3 + 1}$ | Limit Comparison (Quotient Test) | The Ratio Test usually fails here (results in 1)<br>So we compare it to a 'similar' P-Series, based of the highest powers<br>$\left( \text{e.g. }\frac{k}{k^3} = \frac{1}{k^2} \right)$ |
| Logarithms $(ln(k))$or simple decreasing functions                                     | Integral Test                    | Use **only** if we can easily integrate the function                                                                                                                                    |
| Oscillating Term $(\sin k, \cos k)$                                                    | Direct Comparison Test           | Limits don't exist for Oscillating terms<br>So we replace them with their mix/max values<br>$\left( \text{e.g. } \cos k \leqslant 1 \right)$ to build an inequality                     |
| Alternating Signs $(-1^n)$                                                             | Alternating Sign Test            | This test is designed for series with negative terms                                                                                                                                    |

# Tests:
## $\textbf{1. The Ratio Test:}$
- $\text{Best for Factorials } (k!) \text{ and Exponentials } (3^k)$
#### $\text{Formula:}$ 
- $\text{Calculate the limits of the ``next term divided by the current term"}$
$$\rho = \lim_{k \rightarrow \infty}{\left| \frac{a_{k+1}}{a_k} \right|}$$
#### $\text{Results:}$ 
- $\rho \lt 1: \text{The series \textbf{converges} (Absolutely)}$
- $\rho \gt 1: \text{The series \textbf{diverges}}$
- $\rho = 1: \text{\textbf{Test Inconclusive} (Try a different test)}$
## $\textbf{2. The } n^{th} \textbf{ Root Test:}$
- $\text{Best for Entire terms raised to the } (k^{th}) \text{ power e.g.} (...)^k$
#### $\text{Formula:}$ 
- $\text{Calculate the } k^{th} \text{ root of the absolute term (get rid of the power)}$
$$\rho = \lim_{k \rightarrow \infty}{\left| a_k \right|^{\frac{1}{k}}}$$
#### $\text{Results:}$ 
- $\rho \lt 1: \text{The series \textbf{converges} (Absolutely)}$
- $\rho \gt 1: \text{The series \textbf{diverges}}$
- $\rho = 1: \text{\textbf{Test Inconclusive} (Try a different test)}$
## $\textbf{3. The Limit Comparison Test (Quotient Test):}$
- $\text{Best for Rational Functions (polynomials over polynomials)}$
#### $\text{Method:}$ 
1. $\text{Create a simplified comparison series by keeping only the highest powers of }k$
2. $\text{Calculate the limit ratio}$
$$\rho = \lim_{k \rightarrow \infty}{\frac{a_k}{b_k}}$$
#### $\text{Rules:}$ 
- $\text{If } 0 \lt \rho \lt \infty \text{ (Finite and non-zero): Both series behave the same}$
	- $\text{If } \sum{b_k} \text{ converges} \rightarrow \sum{a_k} \text{ converges}$
	- $\text{If } \sum{b_k} \text{ converges} \rightarrow \sum{a_k} \text{ converges}$
- $\text{If } \rho = 0:$
	- $\text{If } \sum{b_k} \text{ converges} \rightarrow \sum{a_k} \text{ converges}$
- $\text{If } \rho = \infty:$
	- $\text{If } \sum{b_k} \text{ converges} \rightarrow \sum{a_k} \text{ converges}$
## $\textbf{4. Direct Comparison Test:}$
- $\text{Best for Oscillating terms } (\sin k, \cos k)$
#### $\text{Method:}$ 
- $\text{Find a simple series } \sum{b_k} \text{ that is strictly larger or smaller than the original series} \sum{a_k}$
#### $\text{Rules:}$ 
- $\text{The ceiling Rule } \textbf{(Convergence):}$
	- $\text{If } 0 \leqslant a_k \leqslant b_k \text{, and } \sum{b_k} \text{ converges} \rightarrow \sum{a_k} \textbf{ converges}$
- $\text{The Floor Rule } \textbf{(Divergence):}$
	- $\text{If } 0 \leqslant b_k \leqslant a_k \text{, and } \sum{b_k} \text{ diverges} \rightarrow \sum{a_k} \textbf{ diverges}$
#### $\text{Example:}$
$$\text{For } \frac{2 + \cos{k}}{k^2} \text{, use the fact that} \cos{k} \leqslant 1$$
$$\therefore \frac{2 + \cos{k}}{k^2} \leqslant \frac{3}{k^2}$$
## $\textbf{5. Integral Test:}$
- $\text{Best for Logarithms, or easy to integrate functions}$
#### $\text{Formula:}$ 
- $\text{Convert the sequence } a_k \text{ into a continuous function } f(x) \text{ and integrate from } 1 \text{ to } \infty$
$$I = \lim_{N \rightarrow \infty}{\int_1^N{f(x)}}dx$$
#### $\text{Condition:}$ 
- $\text{The function } f(x) \text{ must be positive and decreasing for } x \geqslant 1$
#### $\text{Rules:}$ 
- $\text{Integral is \textbf{Finite}} \rightarrow \text{Series \textbf{Converges}}$
- $\text{Integral is \textbf{Infinite}} \rightarrow \text{Series \textbf{Diverges}}$
## $\textbf{6. Alternating Sign Test:}$
- $\text{Best for series with} (-1)^k$
#### $\text{Method:}$ 
- $\text{Ignore the negative sign (look at } |a_k| \text{) and check two conditions}$
#### $\text{Conditions:}$ 
1.  $\textbf{Limit: } \lim_{k \rightarrow \infty}{|a_k|} = 0$
2. $\textbf{Decreasing: } |\lim_{k \rightarrow \infty}{|a_k|}| \lt |a_k| \text{, the terms eventually get smaller (in magnitude)}$
#### $\text{Rules:}$ 
$\text{If \textbf{both} conditions are met} \rightarrow \text{The series \textbf{Converges}}$

$\textbf{Note: } \text{Does not check for absolute convergence}$

$\underline{\textbf{Related Pages: }}$
- [[Double Summation]]
- [[Methods to Find Limits]]
- [[Taylor Series]]

