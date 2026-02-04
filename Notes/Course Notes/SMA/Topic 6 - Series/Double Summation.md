Work like nested loops in programming

```python
for i in range(m):
	for j in range(n):
		# Sum from 1 to n
	# Repeat for every value of i
```
$$\sum_{i=1}^m\sum_{j=1}^n(a_{i,j})$$
- Outer Loop (`i`): Runs from `1` to `m`
	- For the Outer Loop, treat `j` as a constant
- Inner Loop (`j`): Runs from `1` to `n` for every value of `i`
	- For the Inner Loop, treat `i` as a constant

General Example:
===
$$\text{Let }A_i\text{ and }B_j\text{ be functions in terms of }i\text{ and }j$$
$$\text{Question: Calculate } \sum_{i=1}^m\sum_{j=1}^n(A_i+B_j)$$
$\textbf{Step 1:}\text{ Splitting terms (Linearity)}$
$$\sum_{i=1}^n\sum_{j=1}^m(A_i+B_j) = \sum_{i=1}^n\left(\sum_{j=1}^m{A_i} + \sum_{j=1}^n{B_j}\right)$$
$\textbf{Step 2:}\text{ Factor Out Constants}$
$$\sum_{j=1}^m{A_i} = A_i\sum_{j=1}^m{1} = (A_i \times m)$$
Worked Example:
===
$$\text{Question: Calculate }S = \sum_{i=1}^2{\sum_{j=1}^3({i + j^2})}$$
$\textbf{Step 1:} \text{ Expand the Inner Summation (in terms of }i\text)$
$$\sum_{j=1}^3{(i + j^2)} = \sum_{j=1}^3{i} + \sum_{j=1}^3{j^2}$$
$\text{Now using the summation formula: }$
$$\sum_{j=1}^n{j^2} = \frac{1}{6}n(n+1)(2n+1)$$
$\textbf{Step 2:}\text{We can Calculate the Value of the Inner Sum (in terms of }i\text)$
$$\sum_{j=1}^3{(i + j^2)} = 3i + \frac{1}{6}(3)(4)(7)$$
$$\sum_{j=1}^3{(i + j^2)} = 3i + 14$$
$\textbf{Step 3:} \text{ Now we Expand the Outer Sum}$
				$\text{(We do this using our found value of the Inner Sum)}$
$$\sum_{i=1}^2{(3i + 14)} = 3\sum_{i=1}^2{i} + \sum_{i=1}^2{(14)}$$
$$\sum_{i=1}^2{(3i + 14)} = 3(\frac{1}{2})(2)(3) + 28$$
$\text{Final Answer:}$
$$\sum_{i=1}^2{(3i + 14)} = 37$$

