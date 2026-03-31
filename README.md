# Linear Algebra Review Notes (Clean Printable Version)

**Date:** 2026-03-31

---

## 1. Basic Definitions

### 1.1 Matrices and Vectors

(a) An $m \times n$ matrix is a rectangular array of numbers with $m$ rows and $n$ columns.  
(b) A row vector is a $1 \times n$ matrix.  
(c) A column vector is an $m \times 1$ matrix.

Let $a,b \in \mathbb{R}$, and let $A,B$ be $m \times n$ matrices. Then:

(a) $A+B = B+A$  
(b) $A+(B+C) = (A+B)+C$  
(c) $(a+b)A = aA+bA$  
(d) $a(A+B) = aA+aB$  
(e) $a(bA) = (ab)A$

---

## 2. Matrix Multiplication

Let $A=(a_{ij}) \in \mathbb{R}^{m\times n}$ and $B=(b_{jk}) \in \mathbb{R}^{n\times p}$.

Let

$$
X=
\begin{pmatrix}
x_{11}\\
\vdots\\
x_{n1}
\end{pmatrix},
$$

and let $C_k$ denote the $k$-th column of $A$. Then

$$
AX=\sum_{k=1}^n x_{k1}C_k
=
\begin{pmatrix}
\sum_{k=1}^n a_{1k}x_{k1}\\
\sum_{k=1}^n a_{2k}x_{k1}\\
\vdots\\
\sum_{k=1}^n a_{mk}x_{k1}
\end{pmatrix}.
$$

### Theorem 1.5

Let $r_i$ be the $i$-th row of $A$, and let $c_j$ be the $j$-th column of $B$.

(a) The $j$-th column of $AB$ equals $Ac_j$.  
(b) The $i$-th row of $AB$ equals $r_iB$.

### Theorem 1.17

(a) $A(B+B') = AB+AB'$  
(b) $(A+A')B = AB+A'B$  
(c) $(aA)B = a(AB) = A(aB)$  
(d) $A(BC) = (AB)C$

---

## 3. Transpose

### Definition

Let $A \in \mathbb{R}^{m\times n}$. The transpose of $A$ is denoted by $A^\top$.

### Theorem 1.20

(a) $(A+A')^\top = A^\top + (A')^\top$  
(b) $(aA)^\top = a(A^\top)$  
(c) $(AB)^\top = B^\top A^\top$

---

## 4. Zero and Identity Matrices

### Definition 1.22

(a) $0_{m\times n}$: the $m \times n$ matrix whose entries are all zero.  
(b) Zero vector $0_n$: the $n$-dimensional zero column vector.  
(c) Identity matrix $I_n$: the square matrix with diagonal entries $1$ and off-diagonal entries $0$.

### Properties

$$
AI_n = A, \qquad I_mA = A.
$$

---

## 5. Linear Systems and Row Operations

### Elementary Row Operations

1. Swap row $i$ and row $j$  
2. Multiply row $i$ by a nonzero scalar  
3. Add $k$ times row $i$ to row $j$

### Reduced Row Echelon Form (RREF)

A matrix is in reduced row echelon form if:

(a) Every leading entry is $1$  
(b) All zero rows are at the bottom  
(c) Every entry above and below a leading entry is $0$  
(d) The leading entries move to the right as you go down the rows

### Solution Cases

- **No solution:** there is a leading entry in the final column
- **Unique solution:** there are no free variables
- **Infinitely many solutions:** there is at least one free variable

### Theorem 1.39

If $A \in \mathbb{R}^{m\times n}$ and $n>m$, then the homogeneous system

$$
Ax=0
$$

has a **nonzero solution**.

---

## 6. Invertible Matrices

### Definition 1.41

A matrix $A \in \mathbb{R}^{n\times n}$ is invertible if there exists a matrix $B$ such that

$$
AB=BA=I_n,
\qquad B=A^{-1}.
$$

In that case, the solution of

$$
Ax=b
$$

is

$$
x=A^{-1}b.
$$

### Elementary Matrices (1.42)

An elementary matrix is a matrix obtained from $I_n$ by performing **one row operation**.

### Theorem 1.43

If $r$ is a row operation, then

$$
r(A)=r(I_n)\,A.
$$

### Theorem 1.46

Row operations **preserve the solution set** of the linear system $Ax=b$.

---

## 7. Equivalent Conditions for Invertibility

For $A \in \mathbb{R}^{n\times n}$, the following are equivalent:

(a) $A$ is invertible  
(b) $Ax=0$ has only the trivial solution $x=0$  
(c) $A$ can be row-reduced to $I_n$

### How to Find $A^{-1}$

1. Form the augmented matrix $(A \mid I_n)$  
2. Compute its RREF: $(R \mid S)$  
3. If $R=I_n$, then $A^{-1}=S$  
4. If $R \ne I_n$, then $A$ is not invertible

---

## 8. Mind Map

```mermaid
mindmap
  root((Linear Algebra Review))
    Basic Definitions
      Matrix
      Row Vector
      Column Vector
      Matrix Addition
      Scalar Multiplication
    Matrix Multiplication
      Column Interpretation
      Theorem 1.5
      Theorem 1.17
      Associativity
      Distributivity
    Transpose
      Definition
      Transpose of Sum
      Transpose of Scalar Multiple
      Transpose of Product
    Zero and Identity
      Zero Matrix
      Zero Vector
      Identity Matrix
      AI_n = A
      I_mA = A
    Linear Systems
      Row Operations
      RREF
      No Solution
      Unique Solution
      Infinitely Many Solutions
      Homogeneous System
    Invertible Matrices
      Definition
      A^{-1}
      Elementary Matrices
      Row Operation Matrix Form
      Solution x = A^{-1}b
    Invertibility Tests
      Ax = 0
      Row Reduce to I_n
      Augmented Matrix
      Find Inverse
