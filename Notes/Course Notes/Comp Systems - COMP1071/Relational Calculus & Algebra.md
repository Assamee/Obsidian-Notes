# Relational Calculus
- Relational Calculus is "declarative". It describes **what** data you want, not the procedure for how to find it. 
###### Relational Tuple Calculus:
- A non-procedural query language based on first-order logic. Where queries are expressed as a set of tuples $\{t \; | \; P(t)\}$, that satisfy a specified predicate $P$
###### Notation:
$$\{t \; | \; P(t)\}$$
- - **$t$**: The tuple variable (represents the row you want to retrieve).
- **$|$**: "Such that".
- **$P(t)$**: The formula (predicate) that must be true for $t$ to be included in the result

Predicate = A function that returns **true/false** when arguments are given
Proposition = The **expression** obtained when **replacing values** for the
arguments of a predicate (a proposition is either true or false)

---
#### Basic Operators:
- Let $P(x)$ and $Q(x)$ be two predicates with an argument x
**AND:**
$$\{x \; | \; P(x) \land Q(x) \}$$
**OR:**
$$\{x \; | \; P(x) \lor Q(x) \}$$
**NOT: $(\neg \; or \sim)$**
$$\{x \; | \; P(x) \sim Q(x) \}$$
---
#### Example:
Find all staff members who earn more than £10,000
- We want a tuple (row), $s$ (for staff)
- $s$ must belong to the $Staff$ table
- The salary attribute of $s$ must be $\gt 10000$
$$\text{Result: } \{s \; | \; Staff(s) \land s.salary \gt 10000 \}$$
---
### Quantifiers $(\exists, \forall)$:
- Used when you need to check if data exists in a table
#### $\exists$ (Existential Quantifier): "There exists..."
- Checks if *at least one* related row exists in another table
###### Example $(\exists)$:
**Question:** Find the names of all customers who have a **Loan** (e.g. there is a tuple in the borrower table for them)

Database:
- customer(<u>customerName</u>, customerStreet, customerCity)
- borrower(<u>customerName</u>, <u>loanNumber</u>)

$$
\{c.customerName \; | \; customer(c) \land \exists b \;(borrower(b) \land b.customerName = c.customerName)\}
$$
Explanation:
- **Target:** We want to return $c.customerName$, so $c$ is our primary variable
- **Link:** We need to verify that this customer exists in the `borrower` table
- **Quantifier:** $\exists b$ reads "There exists a tuple $b$ in the borrower relation$\dots$"
- **Condition:** "$\dots$such that $b$'s name is the same as $c$'s name". If even **one** such row $b$ exists, the customer $c$ is included in the result.
---
#### $\forall$ (Universal Quantifier): "For all..."
- Use this when checking if _every_ row in a set meets a condition
###### Example $(\forall)$:
**Question:** Find the branches where **every** account held at that branch has a balance greater than $£500$

Database:
- branch(<u>branchName</u>, branchCity, assets) 
- account(<u>accountNumber</u>, branchName, balance)
$\{b.branchName \; | \; branch(b) \land \forall a \; ((account(a) \land a.branchName = b.branchName) \rightarrow a.balance \gt 500)\}$
Explanation:
- **Target:** We iterate through branches using variable $b$
- **Quantifier:** $\forall a$ reads "For all tuples $a$ in the universe"
- **Implication ($\rightarrow$):** This is the standard structure for "For All" queries. It reads: "IF $a$ is an account at this branch ($a.branchName = b.branchName$), THEN it must satisfy the condition ($a.balance > 500$)"
- If an account exists at the branch with a balance of £200, the implication fails, making the whole condition false for that branch, so it is excluded.
---
# Relational Algebra
- Relational Algebra is "procedural". It uses operators to construct a new set of data from existing ones, specifying **how** to retrieve data rather than just what to retrieve
###### Relational Algebra:
- A procedural query language where queries are expressed as a sequence of operations, taking one or more relations as an input, to produce a new relation as an output
---
### Unary Operations (One Table)
- These operations work on a single relation at a time
#### Selection $(\sigma)$:
- **Syntax:** $\sigma_{\text{condition}}(R)$
- **Purpose:** Selects a subset of **rows** (tuples) that satisfy a specific condition
- **SQL Equivalent:** `WHERE` clause
###### Example:
**Question:** Find all loans with an amount greater than $£1200$

Database:
- loan(<u>loanNumber</u>, branchName, amount)
$$\sigma_{amount > 1200}(loan)$$
**Explanation:**
- **Operation:** The $\sigma$ symbol acts like a filter
- **Condition:** It looks at the `amount` column for every row
- **Result:** It returns the **entire row** (all columns) for any loan where the amount is strictly greater than 1200
---
#### Projection $(\pi)$:
- **Syntax:** $\pi_{col1,col2 \dots}(R)$
- **Purpose:** Selects specific **columns** (attributes) and discards the rest
- **SQL Equivalent:** `SELECT DISTINCT col1, col2 ...` 
- _**Note:**_ _Unlike SQL, Relational Algebra explicitly eliminates duplicates in the result_
###### Example:
**Question:** Find the loan numbers of all loans
**Database:** 
- loan(<u>loanNumber</u>, branchName, amount)
$$\{\pi_{loanNumber}(loan)\}$$
**Explanation**
- **Operation:** The $\pi$ symbol selects specific columns.
- **Result:** It creates a new list containing _only_ the `loanNumber` column.
---
#### Rename $(\rho)$:
- **Syntax:** $\rho_{NewName}(R) \text{ or } \rho_{S(A,B,C)}(R)$ 
- **Purpose:** Gives a temporary name to a relation or its attributes
- **Usage:** Used when you need to join a table with itself (e.g. finding a supervisor from within the same Staff table)
###### Example:
**Question:** We want to join the `loan` table with itself (e.g., to find pairs of loans with the same amount). To do this, we must give one copy a different name.

**Database:**
- loan(<u>loanNumber</u>, branchName, amount)
$$\rho_{SecondLoan}(loan)$$

**Explanation:**
- **Operation:** The $\rho$ operator renames the relation `loan` to `SecondLoan`
- **Usage:** This allows us to write expressions like $loan \times SecondLoan$ without ambiguity (e.g., `loan.amount` vs `SecondLoan.amount`)
---
#### Combined Example $(\exists, \forall, \rho)$:
**Question:** Find the names of all customers who live in "Durham", and rename the resulting list to "DurhamCustomers"

**Database:** 
- customer(<u>customerName</u>, customerStreet, customerCity)
$$
\rho_{DurhamCustomers}(\pi_{customerName}(\sigma_{customerCity = 'Durham'}(customer)))
$$
**Explanation:**
- **Order of Operations:** Relational Algebra works from the **inside out** (like brackets in maths)
    
- **Step 1 (Inner - $\sigma$):** $\sigma_{customerCity = \text{'Durham'}}(customer)$
    - First, we filter the table to keep **only** the rows where the city is "Durham".
- **Step 2 (Middle - $\pi$):** $\pi_{customerName}(\dots)$
	- From that filtered result, we throw away the `customerStreet` and `customerCity` columns, keeping only the `customerName`
- **Step 3 (Outer - $\rho$):** $\rho_{DurhamCustomers}(\dots)$
	- Finally, we give this result table a temporary name, "DurhamCustomers", so we can refer to it later

**Why this order?**
- We usually **Select** ($\sigma$) first to reduce the number of rows.
- Then we **Project** ($\pi$) to reduce the number of columns.
- This makes the data smaller and faster to work with before passing it to other operations.
---
### Binary Operations (Two Table)
- These operations combine two relations
#### Union $(\cup)$:
- **Syntax:** $A \cup B$
- **Purpose:** Combines all tuples from relation $A$ and relation $B$ into one set (removing duplicates)
###### Constraint: $R$ and $S$ must be Union Compatible. Meaning: ^a04368
1. They have the same number of attributes
2. Matching attributes must have the same domain (data type)
###### Example $(\cup)$:
**Question:** Find the names of all customers who have a **Loan** OR an **Account** (or both).

**Database:**
- borrower(<u>customerName</u>, loanNumber)
- depositor(<u>customerName</u>, accountNumber)
$$\pi_{customerName}(borrower) \cup \pi_{customerName}(depositor)$$
**Explanation:**
- **The Goal:** We want a single list of names that appear in _either_ table
- **The Rule (Union Compatibility):** You cannot just Union `borrower` and `depositor` directly because they have different columns (`loanNumber` vs `accountNumber`) 
- **The Fix:** We use Projection ($\pi$) first to trim both tables down to just `customerName` so they are compatible
---
#### Set Difference $(-)$:
- **Symbol:** $R - S$
- **Purpose:** Returns tuples that are in $R$ but **NOT** in $S$
- **Constraint:** Relations must also be **Union Compatible** (!{[[Relational Calculus & Algebra#^a04368]]) ^d000f6
- **Example:** "Find cities with a Property but no Branch" $\rightarrow \pi_{city}(Property) - \pi_{city}(Branch)$
###### Example $(-)$:
**Question:** Find the names of customers who have an **Account** but **NOT** a **Loan**

**Database:**
- borrower(<u>customerName</u>, loanNumber)
- depositor(<u>customerName</u>, accountNumber)
$$\pi_{customerName}(depositor) - \pi_{customerName}(borrower)$$
---
#### Cartesian Product $(\times)$
- **Symbol:** $R \times S$
- **Purpose:** Combines **every** tuple in $R$ with **every** tuple in $S$ (concatenation)
- **Size:** If $R$ has 5 rows and $S$ has 3 rows, the result has $5 \times 3 = 15$ rows
- **Note:** This is rarely used alone; it is usually followed by a Selection ($\sigma$) to filter meaningful pairs
###### Example:
**Question:** Create a theoretical list of every possible combination of **Customers** and **Branches**

**Database:**
- customer(<u>customerName</u>, $\dots$)
- branch(<u>branchName</u>, $\dots$)
$$customer \times branch$$
---
### Derived Operations (Relational Algebra)
- These operations are "derived" because they can be built by combining the basic operations (Selection, Projection, Cartesian Product, Union, Difference). However, they are so common that they have their own symbols
#### Intersection $(\cap)$:
- **Syntax:** $R \cap S$
- **Purpose:** Returns a relation containing all tuples that appear in both input relations $R$ and $S$
- **Constraint:** Relations must be **Union Compatible** (!{[[Relational Calculus & Algebra#^a04368]]) ^d000f6
- **Derivation:** $R \cap S = R - (R - S)$ 
###### Example:
**Question:** Find the names of customers who have **BOTH** a **Loan** and an **Account**.

**Database:**
- borrower(<u>customerName</u>, loanNumber)
- depositor(<u>customerName</u>, accountNumber)
$$\pi_{customerName}(borrower) \cap \pi_{customerName}(depositor)$$
**Explanation:**
- **The Goal:** We want names that appear in _both_ lists.
- **Union Compatibility:** Just like Union and Difference, the inputs must have the same structure. We project `customerName` first
---
#### Joins $(\bowtie)$:
- Joins connect data from two tables based on related columns
#### Theta Join $(\bowtie_{\theta})$:
- **Syntax:** $R \bowtie_\theta S = \sigma_\theta(R \times S)$
- **Purpose:** A cartesian Product followed by a Selection condition $\theta$
- **Usage:** General joining with any condition (e.g. $R.a \lt S.b)$
###### Example:
**Question:** Find all combinations of loans and branches where the loan amount is greater than the branch's assets. (A "risky" situation)

**Database:**
- loan(<u>loanNumber</u>, branchName, amount)
- branch(<u>branchName</u>, branchCity, assets)
$$loan \bowtie_{loan.amount > branch.assets} branch$$
**Explanation:**
- **Operation:** This combines every loan with every branch (Cartesian Product), but _only_ keeps the pairs where the condition $\theta$ (`amount > assets`) is true
- **Note:** This is a general join; the columns don't need to have the same name.
---
#### Equijoin $(=)$:
- **Purpose:** A specific type of Theta join where the condition uses only the equality operator $(=)$
###### Example:
**Question:** Join the `borrower` and `loan` tables by explicitly linking their loan numbers.

**Database:**
- borrower(<u>customerName</u>, <u>loanNumber</u>)
- loan(<u>loanNumber</u>, branchName, amount)
$$borrower \bowtie_{borrower.loanNumber = loan.loanNumber} loan$$
**Explanation:**
- **Operation:** This is a specific type of Theta join where the condition uses strictly equals ($=$)
- **Result:** It returns rows where the loan numbers match.
- **Important:** Unlike Natural Join, the result will contain **two** columns for `loanNumber` (one from `borrower`, one from `loan`) unless you project one out
---
### Natural Join $(\bowtie)$:
- **Purpose:** An **Equijoin** performed over all attributes with the same name in both relations, followed by the removal of duplicate attribute columns 
	- "Join these two tables by matching up every column that has the same name"
###### Example:
**Question:** Join `borrower` and `loan` naturally (the most common way).

**Database:**
- borrower(<u>customerName</u>, <u>loanNumber</u>)
- loan(<u>loanNumber</u>, branchName, amount)
$$borrower \bowtie loan$$
**Explanation:**
- **Operation:** The database automatically detects that both tables have a column named `loanNumber` and joins on it.
- **Result:** Same as the Equijoin above, **EXCEPT** the duplicate `loanNumber` column is automatically removed. You get exactly one `loanNumber` column in the output.
- **Constraint:** This only works if the joining columns have identical names in both tables.
---
##### Outer Joins:
- **Left Outer Join** (⟕)**:** Keeps all rows from the Left table, even if there's no match in the Right (fills with NULL)
- **Right Outer Join** (⟖)**:** Keeps all rows from the Right table
- **Full Outer Join** (⟗)**:** Keeps all rows from both tables
---
#### Division $(\div)$:
- **Syntax:** $A \div B$
- **Definition:** Where $B$ has a subset of attributes of $A$, and the result consists of the values of attributes in $A$ but not in $B$ that are associated with **every** tuple in $B$
- **Requirement:** $B$ must have a subset of attributes from $A$: $A(X_1, X_2, \dots, Y_1, Y_2, \dots)$ and $B(Y_1, Y_2, \dots)$
###### Example:
**Question:** Find the names of customers who have an account at **EVERY** branch located in "London".

**Database:**
- depositor(<u>customerName</u>, accountNumber)
- account(<u>accountNumber</u>, branchName, balance)
- branch(<u>branchName</u>, branchCity, assets)

**Step 1: The Dividend (The "Candidates")**
We first need a list of _who_ has an account _where_. We join `depositor` and `account` to link customers to branches.
$$R1 \leftarrow \pi_{customerName, branchName}(depositor \bowtie account)$$

**Step 2: The Divisor (The "Target Set")**
Next, we need a list of _only_ the branches in London.
$$R2 \leftarrow \pi_{branchName}(\sigma_{branchCity=\text{'London'}}(branch))$$
**Final Operation:**
$$R1 \div R2$$
**Explanation:**
- **The Logic:** The division operator $A \div B$ returns the values from column A (customers) that are paired with **every single value** in column B (London branches).
- **Concrete Example:**
    - Suppose the **London branches** ($R2$) are: `{B1, B2}`
    - **Customer A** has accounts at `{B1, B2}`. $\rightarrow$ **Selected** (Matches all)
    - **Customer B** has accounts at `{B1, B2, B3}`. $\rightarrow$ **Selected** (Matches all + extra)
    - **Customer C** has an account at `{B1}` only. $\rightarrow$ **Rejected** (Missing B2)
- **Key Indicator:** If an exam question asks "Find X that are related to **ALL** Y", you must use Division
---
**Summary of Keywords for Question Identification**
- "Find $\dots$ over X value" $\rightarrow$ **Selection ($\sigma$)**
- "Find the names of$\dots$" $\rightarrow$ **Projection ($\pi$)**
- "Find $\dots$ who have a loan **OR** an account" $\rightarrow$ **Union ($\cup$)**
- "Find $\dots$ who have a loan **AND** an account" $\rightarrow$ **Intersection ($\cap$)**
- "Find $\dots$ who have a loan **BUT NOT** an account" $\rightarrow$ **Difference ($-$)**
- "Find $\dots$ who have a loan **AT** branch X" $\rightarrow$ **Join ($\bowtie$)** + **Selection ($\sigma$)**
- "Find $\dots$ who have **ALL**..." $\rightarrow$ **Division ($\div$)**
---