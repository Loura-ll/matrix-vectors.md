# Algebra 1 - Chapter 1: Matrices and Vectors

## 1.1 Definitions

### Definition
1. An m x n matrix is a rectangular array of numbers with m rows and n columns.
2. A row vector is a 1 x n matrix.
3. A column vector is an m x 1 matrix.

### Matrix Addition and Scalar Multiplication
Let a, b be numbers, and let A, B, C be m x n matrices. Then:

1. A + B = B + A
2. A + (B + C) = (A + B) + C
3. (a + b)A = aA + bA
4. a(A + B) = aA + aB
5. a(bA) = (ab)A

> **Note.** These are the algebraic rules for matrix addition and scalar multiplication.

---

## 1.2 Matrix Multiplication

Let:
- A = (a_ij) be an m x n matrix
- B = (b_jk) be an n x p matrix

Then the product AB is defined and is an m x p matrix.

### Matrix times a Column Vector

Let x be an n x 1 column vector:

```text
x =
[ x_11 ]
[  ... ]
[ x_n1 ]
```

Let c_1, ..., c_n be the columns of A. Then:

```text
Ax = sum from k = 1 to n of x_k1 c_k
```

In coordinates:

```text
Ax =
[ sum from k = 1 to n of a_1k x_k1 ]
[ sum from k = 1 to n of a_2k x_k1 ]
[                ...                ]
[ sum from k = 1 to n of a_mk x_k1 ]
```

Also:

```text
Ax =
sum from k = 1 to n of x_k1
[ a_1k ]
[ a_2k ]
[  ... ]
[ a_mk ]
```

> **Note.** The vector Ax is a **linear combination** of the columns of A.

### What is a linear combination?
A **linear combination** of vectors v_1, ..., v_n is an expression of the form:

```text
a_1 v_1 + a_2 v_2 + ... + a_n v_n
```

where a_1, ..., a_n are scalars.

So Ax means:

**take the columns of A and combine them using the entries of x as coefficients.**

---

## 1.5 Theorem

Let A be an m x n matrix and B an n x p matrix. Let r_i be the i-th row of A, and let c_j be the j-th column of B.

1. The j-th column of AB equals A c_j.
2. The i-th row of AB equals r_i B.

> **Interpretation.**
> - Product columns come from multiplying A by columns of B.
> - Product rows come from multiplying rows of A by B.

---

## 1.17 Theorem: Algebraic Rules of Matrix Multiplication

Let a be a number. Let A, A' be m x n matrices, B, B' be n x p matrices, and C be a p x q matrix. Then:

1. A(B + B') = AB + AB'
2. (A + A')B = AB + A'B
3. (aA)B = a(AB) = A(aB)
4. A(BC) = (AB)C

> **Important.** Matrix multiplication is **associative**, but in general it is **not commutative**:
>
> ```text
> AB != BA
> ```

---

## 1.4 Transpose

### Definition
Let A be an m x n matrix. The **transpose** of A is denoted by A^T.

It is the n x m matrix obtained by turning rows into columns.

### 1.20 Theorem
Let A, A' be m x n matrices, let B be n x p, and let a be a number. Then:

1. (A + A')^T = A^T + (A')^T
2. (aA)^T = a(A^T)
3. (AB)^T = B^T A^T

> **Key identity.**
>
> ```text
> (AB)^T = B^T A^T
> ```
>
> The order reverses.

---

## 1.5 Identity and Zero

### 1.22 Definition

1. O_(m x n) is the m x n matrix with all entries equal to 0.
2. The zero vector O_n is the height-n column vector with all entries equal to 0. We often write simply O when the size is clear from context.
3. The identity matrix I_n is the n x n matrix with 1's on the diagonal and 0's elsewhere.

### Theorem
If A is an m x n matrix, then:

```text
A I_n = A
I_m A = A
```

> **Note.**
> - Right multiplication by the identity does nothing.
> - Left multiplication by the identity does nothing.
> - Sizes must match correctly.

---

# Linear Systems

A linear system in variables x_1, ..., x_n has the form:

```text
a_11 x_1 + a_12 x_2 + ... + a_1n x_n = b_1
...
a_m1 x_1 + a_m2 x_2 + ... + a_mn x_n = b_m
```

---

## Row Operations

The elementary row operations are:

1. Swap row i and row j
2. Multiply row i by a non-zero scalar
3. Add k times row i to row j

These operations are used to simplify a matrix while preserving the solution set of the corresponding linear system.

---

## 1.3 Reduced Row Echelon Form (RREF)

A matrix is in **RREF** if:

1. All leading entries are 1
2. Every all-zero row is at the bottom
3. All entries in the same column as a leading entry are 0
4. If rows i and i + 1 both have leading entries, then the leading entry in row i + 1 is to the right of the leading entry in row i

---

## 1.8 Solving Systems Using RREF

When solving a system by row reduction:

### No solution
If the final column of the augmented matrix has a leading entry, then the system has **no solution**.

### Free variables
Variables whose columns do **not** contain leading entries are called **free variables**.

They can be chosen freely.

### Pivot variables
The remaining variables are determined by the free variables. These are usually called **pivot variables** or **leading variables**.

### Three possible cases for the number of solutions

1. **The last column has a pivot** -> **no solution**
2. **At least one free variable** -> **infinitely many solutions**
3. **No free variables** -> **a unique solution**

> **Summary format for solutions**
>
> - express the pivot variables in terms of the free variables
> - if there is no solution, explicitly state **no solution**

---

## 1.39 Theorem

If A is an m x n matrix and n > m, then:

```text
Ax = 0
```

has a non-zero solution.

> **Chinese note.** 若列数大于行数，则 Ax = 0 必有非零解。

### Proof
Perform row operations on the augmented matrix (A | 0) to obtain its RREF.

An RREF matrix has at most one leading entry in each of its m rows. Since n > m, there are more columns than rows, so at least one of the first n columns has no leading entry. Therefore the corresponding variable is a free variable. Hence there are solutions in which that variable is non-zero, so the homogeneous system has a non-zero solution.

---

# 1.9 Invertibility

## 1.41 Definition

An n x n matrix A is **invertible** if there exists an n x n matrix B such that:

```text
AB = BA = I_n
```

We denote B = A^(-1), so:

```text
A A^(-1) = A^(-1) A = I_n
```

If:

```text
Ax = b
```

and A is invertible, then:

```text
x = A^(-1) b
```

---

## 1.42 Elementary Matrices

An **elementary matrix** is a matrix obtained by performing **one row operation** on the identity matrix.

> **Chinese note.** 对单位阵做一次行变换得到的矩阵，叫初等矩阵。

---

## 1.43 Theorem

Let r be a row operation and let A be an n x n matrix. Then:

```text
r(A) = r(I_n) A
```

> **Interpretation.**
> Performing a row operation on A is the same as left-multiplying A by the corresponding elementary matrix.

---

## 1.45 Theorem

Any invertible matrix can be written as a product of elementary matrices.

Suppose:

```text
E_k ... E_2 E_1 A = I_n
```

Then:

```text
A = E_1^(-1) E_2^(-1) ... E_k^(-1)
```

Since the inverse of an elementary matrix is again elementary, this shows that A is a product of elementary matrices.

---

## 1.46 Theorem

Row operations preserve the solution set of:

```text
Ax = b
```

### Proof
By Theorem 1.43:

```text
(A | b) -> E(A | b) = (EA | Eb)
```

If:

```text
Ay = b
```

then multiplying both sides by E gives:

```text
EAy = Eb
```

So the transformed system has the same solutions.

---

# Invertible Matrix Equivalences

For an n x n matrix A, the following are equivalent:

1. A is invertible
2. The only solution to Ax = 0 is x = 0
3. There is a sequence of row operations taking A to I_n

### Proof

#### (1) -> (2)
If A is invertible and:

```text
Ax = 0
```

then multiplying by A^(-1) gives:

```text
x = A^(-1) 0 = 0
```

#### (2) -> (3)
If the homogeneous system has only the trivial solution, then there are no free variables. Hence every column of the RREF of A has a leading entry, so the RREF must be I_n.

#### (3) -> (1)
If there exists a sequence of row operations taking A to I_n, then there exists an invertible matrix E such that:

```text
EA = I_n
```

Hence:

```text
A = E^(-1)
```

so A is invertible.

---

# How to Find A^(-1)

To determine whether A is invertible and, if so, to find A^(-1):

1. Form the augmented matrix

   ```text
   (A | I_n)
   ```

2. Perform row operations to obtain

   ```text
   (R | S)
   ```

   where R is in RREF

3. If R = I_n, then A is invertible and

   ```text
   A^(-1) = S
   ```

4. If R != I_n, then A is not invertible

> **Key check.**
> 看 RREF 左边是不是单位矩阵。

### Why does this work?
If:

```text
E(A | I_n) = (I_n | S)
```

then:

```text
EA = I_n
```

So E = A^(-1), and therefore:

```text
S = A^(-1)
```

If R != I_n, then R has fewer than n leading entries, so there is a free variable. Thus the homogeneous system:

```text
Ax = 0
```

has a non-zero solution, and therefore A is not invertible.

---

# Quick Summary

## Core ideas
- A matrix is a rectangular array of numbers.
- A vector is a special kind of matrix.
- Matrix-vector multiplication gives a linear combination of the columns.
- RREF helps solve linear systems.
- Free variables determine whether solutions are unique or infinite.
- For square matrices, invertibility is tied to:
  - no free variables in Ax = 0
  - row reduction to I_n
  - existence of A^(-1)

---

# Mind Map

## Outline Version

- Matrices and Vectors
  - Definitions
    - Matrix
    - Row vector
    - Column vector
    - Addition
    - Scalar multiplication
  - Matrix Multiplication
    - Inner dimensions match
    - Ax as linear combination
    - Columns of product
    - Rows of product
    - Associative not commutative
  - Transpose
    - Rows become columns
    - Addition rule
    - Scalar rule
    - (AB)^T = B^T A^T
  - Identity and Zero
    - Zero matrix
    - Zero vector
    - Identity matrix
    - AI_n = A
    - I_mA = A
  - Linear Systems
    - Augmented matrix
    - Row operations
    - RREF
    - Pivot variables
    - Free variables
    - No solution
    - Unique solution
    - Infinitely many solutions
  - Homogeneous Systems
    - Ax = 0
    - n > m implies non-zero solution
  - Invertibility
    - Inverse matrix
    - Elementary matrices
    - Row operations as left multiplication
    - Product of elementary matrices
    - Invertible matrix equivalences
    - Find inverse by augmenting with I
