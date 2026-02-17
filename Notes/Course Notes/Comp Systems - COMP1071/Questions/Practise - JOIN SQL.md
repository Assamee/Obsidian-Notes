Example Database: ![[Example Database.png]]

Question 1) Find the names of all customers who have **both** an account and a loan at the 'Durham Central' branch
Tables needed: borrower, loan, depositor, account
```SQL
SELECT b.customerName
FROM borrower b
-- Match 1: Links each Person (borrower) to their specific Loan
-- Without this, we couldn't know which branch issued the person's loan
JOIN loan l
	ON l.loanNumber = b.loanNumber
-- Match 2: Links each Person (borrower) with a Loan to the depositor table
-- Links each [borrower with a Loan] to each [borrower with a deposit] (same borrower)
-- "Both" condition: Ensure the (borrower) customerName exists in both tables
JOIN deposior d
	ON d.customerName = b.customerName
--	Links the Person's Account ID (depositor) to the Actual account details
JOIN account a
	ON a.accountNumber = d.accountNumber

WHERE l.branchName = 'Durham Central'  
AND a.branchName = 'Durham Central';
```
![[Example Database.png]]
### Branch-Based Join:

Question 2) Find the names of all customers who have a **loan** in at the **'Durham Central'** branch, and for each of those customers, list the `accountNumber` of **every account** that is also registered at that same 'Durham Central' branch
``` SQL
SELECT b.customerName, a.accountNumber
FROM borrower b
-- Match every borrower to a loan
JOIN loan l ON l.loanNumber = b.loanNumber

-- Match every [borrower with a loan] to an account
JOIN account a ON a.branchName = l.branchName

WHERE l.branchName = 'Durham Central';
```

![[Example Database.png]]
Question 1) You need to connect loans to their physical location.
- Find the loan number, loan amount, and the city of the branch where the loan is held.
``` SQL
SELECT l.loannumber, l.amount, b.branchCity
FROM loan l
JOIN branch ON l.branchName = b.branchName
```

Question 2) The bank wants a report on customer engagement with loans.
-  List the names of **all** customers and the loan numbers associated with them. Ensure that customers who currently have **no loans** are still included in the list with a `NULL` loan number.
``` SQL
SELECT c.customerName, l.loanNumber -- l. to show NULL values
FROM customer c
-- Left Join the loan table onto the borrower table
LEFT JOIN borrower b ON c.customerName = b.customerName
```

![[Example Database.png]]
Question 3) You are auditing branches for inactivity.
- List all loan numbers and their branch names. Ensure that **every branch** is listed, even if it currently holds **no loans**.
``` SQL
SELECT l.loanNumbers, b.branchName
FROM branch b
LEFT JOIN loan l ON l.branchName = b.branchName
```

Question 4) Comparing branches against each other. (Self-Join)
- Find all pairs of different branch names that are located in the **same city** 
``` SQL
SELECT b1.branchName, b2.branchName
FROM branch b1
JOIN branch b2 ON b1.branchName = b2.branchName
WHERE b1.branchCity < b2.branchCity -- < Removes duplicates (e.g. showing "Branch A & Branch B" but filtering out the mirror "Branch B & Branch A")
```

Question 5) Theoretical marketing planning.
- Generate a list of every possible combination of a **customer** and a **branch**, regardless of whether they have ever done business together.
``` SQL
SELECT *
FROM customer
CROSS JOIN branch
```


$\underline{\textbf{Related Pages: }}$
- [[Relational Calculus & Algebra]]
- [[Practise - Relational Algebra & Calculus]]