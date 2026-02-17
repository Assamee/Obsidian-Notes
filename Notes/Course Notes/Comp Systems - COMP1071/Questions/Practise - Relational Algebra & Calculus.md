# Question 1
Database: ![[Example Database.png]]

![[Pasted image 20260217190738.png]]
1.  ![[Pasted image 20260217190833.png]]
``` SQL
SELECT *
FROM loan
WHERE loan.amount > 1200
```
$$\begin{aligned}
\text{Let $a$ be the amounts, (tuple/row)} \\
\text{AND $a$ must belong to the $loan$ table:} \\
\{ a \; | \; loan(a) \land a.amount \gt 12000 \}
\end{aligned}$$
$$\begin{aligned}
& \text{Relational Algebra: } \\
& \sigma_{amount \gt 1200}(loan) 
\end{aligned}$$

2.  ![[Pasted image 20260217191753.png]]
``` SQL
SELECT loan.loanNumber
FROM loan
WHERE loan.amount > 1200
```
$$\begin{aligned}
\text{Let $t$ be the loan number, } \hspace{8cm}\\
\{ t \; | \; \exists l \in loan(t.loanNumber = l.loanNumber \land l.amount \gt 1200 )\}
\end{aligned}$$
English: "Find the loan number $t$ such that there exists a row $l$ in the loan table where the amounts match and $l$ is over $1200$"
$$\begin{aligned}
&\text{Relational Algebra: } \\
& \pi_{loanNumber}(\sigma_{amount \gt 1200}(loan))
\end{aligned}$$

Extra Question 1) Find the **branch names** and **cities** of all branches that have **assets** greater than **£2,000,000**.
``` SQL
SELECT branch.branchName, branch.branchCity
FROM branch
WHERE branch.assets > 2000000
```
$$\begin{aligned}
\{t \; | \; \exists b \in branch(t.branchName = b.branchName \land t.branchCity = b.branchCity \\ \land \; b.assets \gt 2000000) \}
\end{aligned}$$
English: "Find a tuple(row) $t$, such that, there exists a row $b$ in the $branch$ table ($t$ gets its $branchName$ and $branchCity$), where the $assets$ attribute is greater than $2000000$" 
$$\begin{aligned}
& \text{Relational Algebra: } \\
& \pi_{branchName, branchCity}(\sigma_{assets \gt 2000000}(branch))
\end{aligned}$$
3. ![[Pasted image 20260217202606.png]]
``` SQL
SELECT borrower.customerName FROM borrower
-- If there is a row in borrower, then there must be a loan
UNION
SELECT depositor.customerName FROM depositor
-- If there is a row in depositor, then there must be an account
```
###### Relational Algebra:
$$
\pi_{customerName}(borrower) \cup \pi_{customerName}(depositor)
$$
###### Relational Tuple Calculus:
$$
\{t.customerName \; | \; borrower(t) \cup depositor(t) \}
$$
![[Example Database.png]]
4. ![[Pasted image 20260217210731.png]]
``` SQL
SELECT borrower.customerName
FROM borrower
JOIN loan ON loan.loanNumber = borrower.loanNumber
WHERE loan.branchName = "Durham Central"
```
###### Relational Algebra:
$$
\pi_{}(\sigma_{customerName}(borrower))
$$
![[Example Database.png]]
Extra Question) Find the names of all customers who have a **Loan**
Database: 
- customer(<u>customerName</u>, customerStreet, customerCity) 
- borrower(<u>customerName</u>, <u>loanNumber</u>)
$$
\{c.customerName \; | \; customer(c) \land \exists b \; (borrower(b) \land b.customerName = c.customerName)\}
$$
