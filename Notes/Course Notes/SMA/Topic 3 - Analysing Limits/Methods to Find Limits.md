
# Methods to Find Limits

### Method 1: Substitution
- **The Rule:** If the function is continuous at the limit, simply substitute the limit value in
- **Example:** $$\lim_{x \to 2} x^2 = (2)^2 = 4$$
- **When it fails:** This method does not work if you get an undefined result (e.g., $\frac{0}{0}$ or $\frac{\infty}{\infty}$)
---
### Method 2: Simplify/Factorise Then Substitute
- **The Concept:** Cancel out the problematic terms that prevent direct substitution from working
- **Example:**  Evaluate this limit
$$\lim_{x \to 1} \frac{x^2+x-2}{x^2+2x-3}$$
- **Factorise:** Convert the fraction to $\frac{(x-1)(x+2)}{(x-1)(x+3)}$
- **Cancel and Substitute:** Cancel out the $(x-1)$ terms to get $\frac{x+2}{x+3}$, then apply Method 1 to get $\frac{1+2}{1+3} = \frac{3}{4}$
---
### Method 3: The Pinching Theorem (Squeeze Theorem)
- **The Concept:** Used when a function oscillates wildly but is "trapped" by two other functions going to the exact same limit
- **The Logic:** When trying to find the limit of $f(x)$, if $g(x) \le f(x) \le h(x)$ AND both the limits of $g$ and $h$ equal $L$, then the limit of $f$ is also $L$.
    
- **Example:** Evaluate this limit $$\lim_{x \to 0} x \sin(\frac{1}{x})$$
- **Pinching:** Since $-1 \le \sin(\frac{1}{x}) \le 1$, we can multiply everything by $x$ to create the inequality $-|x|\le x \sin(\frac{1}{x}) \le |x|$
- **The Conclusion:** As both $-|x|$ and $|x|$ go to 0 as $x \to 0$, the middle term $x \sin(\frac{1}{x})$ is trapped and must also go to 0. Therefore, $\lim_{x \to 0} x \sin(\frac{1}{x}) = 0$
---
### Method 4: Standard Limits (Memorise)
- **Trigonometric:** $\lim_{x \to 0} \frac{\sin(x)}{x} = 1$

- **Exponential:** $\lim_{x \to 0} \frac{e^x-1}{x} = 1$

- **Logarithmic:** $\lim_{x \to \infty} \frac{1}{\ln(x)} = 0$

- **Tangent:** $\lim_{x \to 0} \frac{\tan(x)}{x} = 1$
---
### Method 5: Dividing by the Highest Power
- **The Concept:** Used exclusively for limits at infinity
- **The Rule:** Divide every term by the highest power of $x$ found in the denominator.

- **Constraints:** Note that this method does not work for standard polynomials (only fractions)
- **Example:** Evaluate this limit $$\lim_{x \to \infty} \frac{2x^2-7x}{3x^2+4}$$
- **Execution:** Divide by $x^2$ to get $\frac{2 - \frac{7}{x}}{3 + \frac{4}{x^2}}$. As $x \to \infty$, the fraction approaches $\frac{2}{3}$
---
### Method 6: Substituting Variables
- **The Concept:** Substituting variables to make a standard limit recognisable
- **Example:** Evaluate $$\lim_{x \to 0} \frac{\sin(3x)}{x}$$
- **Substitution:** Let $y=3x$, which implies $x = \frac{1}{3}y$.
    
- **Execution:** $$\frac{\sin(3x)}{x} = \frac{\sin(y)}{\frac{1}{3}y} = 3\frac{\sin(y)}{y} = 3(1) = 3$$
---
### Method 7: L'Hôpital's Rule
- **The Conditions:** The limit must produce an undefined result like $\frac{\infty}{\infty}$ or $\frac{0}{0}$. Additionally, the derivatives of the top and bottom must exist and be continuous
#### L'Hôpital Algorithm:
1. **Check:** Confirm if the limit gives $\frac{0}{0}$ or $\frac{\infty}{\infty}$
2. **Differentiate:** Differentiate the top and bottom separately (do not use the Quotient Rule)
3. **Evaluate:** Find $\lim_{x \to a} \frac{g'(x)}{h'(x)}$
4. **Repeat:** If the result is still $\frac{0}{0}$, you can apply the rule again

- **Example:** Find $$\lim_{x \to 0} \frac{\cos(x)-1}{x^2}$$
- **Check:** $\cos(0)-1 = 0$ and $0^2 = 0$, meaning we have $\frac{0}{0}$
- **Apply L'Hôpital:** Differentiate the top to get $-\sin(x)$ and the bottom to get $2x$. The new limit is $\lim_{x \to 0} \frac{-\sin(x)}{2x}$
- **Check again:** $-\sin(0) = 0$ and $2(0) = 0$, which is still $\frac{0}{0}$
- **Apply L'Hôpital:** Differentiate the top to get $-\cos(x)$ and the bottom to get $2$
- **Final Limit:** $\lim_{x \to 0} \frac{-\cos(x)}{2} = -\frac{1}{2}$
---
### Using Limits to Check for Continuity:
- **The Rule:** A function $f(x)$ is continuous at $x=a$ if $\lim_{x \to a} f(x) = f(a)$ (and $f(a)$ exists)