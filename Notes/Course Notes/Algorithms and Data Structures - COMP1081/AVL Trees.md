## AVL Tree
- An AVL tree is a self-balancing Binary Search Tree (BST) where, for every node, the height difference between its left and right subtrees is at most 1
- It guarantees $O(\log n)$ height
---
## Trinode Restructuring
- When an imbalance is detected, we identify three nodes $(z, y, x)$ to determine which rotation to perform
###### Identifying the Variables:
1. **$z$ (The Unbalanced Node):** The first unbalanced node (traveling up from your operation)
2. $y$ **(The Taller Child):**
	- **Insertion:** The child of $z$ that lies on the path of insertion
	- **Deletion:** The child of $z$ with the larger height
3. **$x$ (The Taller Grandchild):**
	- **Insertion:** The child of $y$ that lies on the path of insertion
	- **Deletion:** The child of $y$ with the larger height. (If equal, pick the one on the same side as $y$)
##### The Four Rotation Cases
- Once $z$, $y$, and $x$ are identified, the "shape" they form dictates the fix

| **Orientation ($z \to y \to x$)** | **Case Name**   | **Operation (The Fix)**                             |
| :-------------------------------- | :-------------- | :-------------------------------------------------- |
| **Right-Right** ($\setminus$)     | Left Case       | **Single Left Rotation** on $z$                     |
| **Left-Left** ($/$)               | Right Case      | **Single Right Rotation** on $z$                    |
| **Right-Left** ($>$)              | Right-Left Case | **Double Rotation:** Right on $y$, then Left on $z$ |
| **Left-Right** ($<$)              | Left-Right Case | **Double Rotation:** Left on $y$, then Right on $z$ |

---
#### Worked Example: Deletion (Double Rotation)
_Scenario: Right-Left Imbalance (Requires Right-Left Double Rotation)_

 ###### The Setup
- We start with this valid tree. The task is to **Delete Node 10**.

``` Plaintext
       30
      /  \
    15    50
   /     /  \
 10    35    60
         \
          40
```
###### Trinode Identification
- **$z = 30$** (First unbalanced node).
- **$y = 50$** (The Taller child of 30).
- **$x = 35$** (The Taller child of 50). _Note: 35 is the Left child of 50._
- **Shape:** Right ($30 \to 50$) then Left ($50 \to 35$). This is a **Right-Left ($>$) Zig-Zag**.
###### The Fix (Double Rotation)
**Step A: Right Rotation on $y$ (50)**
- Goal: Straighten the line.
- Node 35 moves **UP** to replace 50.
- **CRITICAL:** 35's existing right child (40) is handed over to become 50's _left_ child.


``` Plaintext
       30  (z)
      /  \
    15    35  (New y)
            \
             50
            /  \
          40    60
```
###### Step B: Left Rotation on $z$ (30)
- Goal: Balance the tree.
- Node 35 moves **UP** again to replace 30.
- Node 30 becomes the _left_ child of 35.
###### Final Result:

``` Plaintext
          35  (New Root)
         /  \
       30    50
      /     /  \
    15    40    60
```
