---
name: matrix-calculus
description: Matrix calculus tutorial and reference based on Jan R. Magnus' "A gentle introduction to matrix calculus". Provides tools, theorems, and worked examples for matrix differential calculus including trace, Kronecker product, vec operator, commutation matrix, duplication matrix, first and second derivatives, optimization, and applications in statistics and econometrics. Use when users ask about matrix derivatives, matrix differential calculus, optimization with matrices, Kronecker products, vec operators, or need help solving matrix calculus problems.
---

# Matrix Calculus

Matrix calculus tutorial based on Jan R. Magnus' "A gentle introduction to matrix calculus" - a comprehensive guide to matrix differential calculus with applications in statistics, econometrics, and optimization.

## Core Concepts

Matrix calculus rests on **two pillars** and requires **six tools**:

### Two Pillars
1. **Correct definition of matrix derivative** (Section 3)
2. **The concept of differential** (Section 4)

### Six Tools (Section 2)

| Tool | Description | Key Property |
|------|-------------|--------------|
| Trace | Sum of diagonal elements: $\operatorname{tr} A = \sum_i a_{ii}$ | $\operatorname{tr} A'B = \operatorname{tr} BA'$ (cyclic permutations) |
| Linear/Quadratic Forms | $Ax$ and $x'Ax$ | $x'Ax = 0 \; \forall x \iff A$ is skew-symmetric |
| Kronecker Product | $A \otimes B$ | $(A \otimes B)(C \otimes D) = AC \otimes BD$ |
| Vec Operator | Stacks columns: $\operatorname{vec} A$ | $\operatorname{vec} ABC = (C' \otimes A)\operatorname{vec} B$ |
| Commutation Matrix | $K_{mn}$ transforms $\operatorname{vec} A \to \operatorname{vec} A'$ | $K_{mn}' = K_{mn}^{-1} = K_{nm}$ |
| Duplication Matrix | $D_n$ transforms $\operatorname{vech} A \to \operatorname{vec} A$ for symmetric $A$ | Essential for symmetric matrix derivatives |

## The Correct Definition of Matrix Derivative

The **only correct definition** for the derivative of a matrix function $F(X)$ is:

$$DF(X) = \frac{\partial \operatorname{vec} F(X)}{\partial (\operatorname{vec} X)'}$$

Each row contains partial derivatives of one element of $F$ with respect to all elements of $X$. Each column contains partial derivatives of all elements of $F$ with respect to one element of $X$.

**Key consequences:**
- Derivative of scalar function $a'x$ is $a'$ (row vector, not column)
- Derivative of $\operatorname{tr} X$ is $(\operatorname{vec} I)'$ (row vector)

## First Differential and Identification Theorem

### Differential Rules

For matrices $X, Y$ and scalar $\alpha$:
- $dA = 0$ (constant)
- $d(\alpha X) = \alpha \, dX$
- $d(X') = (dX)'$
- $d(X + Y) = dX + dY$
- $d(XY) = (dX)Y + X(dY)$
- $d\operatorname{tr} X = \operatorname{tr} dX$ (square $X$)
- $d|X| = |X| \operatorname{tr} X^{-1} dX$ (nonsingular $X$)
- $d\log|X| = \operatorname{tr} X^{-1} dX$
- $dX^{-1} = -X^{-1}(dX)X^{-1}$ (nonsingular $X$)

### First Identification Theorem

$$d f(x) = A(x) \, dx \iff Df(x) = A(x)$$

For matrices:
$$d \operatorname{vec} F(X) = A(X) \, d\operatorname{vec} X \iff DF(X) = A(X)$$

**Workflow:** Compute differential $\to$ Identify derivative from coefficient of $dX$

### Common Derivatives

| Function | Derivative |
|----------|------------|
| $a'x$ | $a'$ |
| $x'Ax$ | $x'(A + A')$ (or $2x'A$ if $A$ symmetric) |
| $\operatorname{tr} X'AX$ | $(\operatorname{vec} C)'$ where $C = (A + A')X$ |
| $\log|X'X|$ | $2(\operatorname{vec} C)'$ where $C = X(X'X)^{-1}$ |
| $\operatorname{tr} X^k$ | $k(\operatorname{vec} X'^{k-1})'$ |
| $AX^{-1}B$ | $-(X^{-1}B)' \otimes (AX^{-1})$ |

## Optimization

### Unconstrained Optimization
1. Compute differential $df(x) = a(x)' dx$
2. Set $a(x) = 0$ and solve

### Constrained Optimization (Lagrange)

For constraint $g(x) = 0$, define Lagrangian:
$$\mathcal{L}(x) = f(x) - \lambda g(x)$$

For matrix constraint $G(X) = 0$:
$$\mathcal{L}(X) = f(X) - \operatorname{tr} L' G(X)$$

First-order conditions: $\partial f/\partial x' = \lambda \partial g/\partial x'$ and $g(x) = 0$

## Second Differential and Hessian

### Second Identification Theorem

$$d^2 f(x) = (dx)' B(x) dx \iff Hf(x) = \frac{B(x) + B(x)'}{2}$$

**Important:** Must symmetrize $B(x)$ - the matrix in the quadratic form is not necessarily symmetric.

### Hessian Matrix

The Hessian contains second-order partial derivatives:
$$Hf(x) = \frac{\partial^2 f(x)}{\partial x \partial x'} = \frac{\partial}{\partial x'}\left(\frac{\partial f(x)}{\partial x'}\right)'$$

### Chain Rule for Second Differentials

If $z = f(y)$ and $y = g(x)$:
$$d^2 z = (dA)B(x)dx + A(y)(dB)dx$$

where $dz = A(y)dy$ and $dy = B(x)dx$.

**Note:** Cauchy invariance does NOT hold for second differentials.

## Matrix Forms for Hessian

Proposition 15 (Hessian identification):
- $d^2 f(X) = \operatorname{tr} A(dX)'B \, dX \iff Hf(X) = \frac{1}{2}(A' \otimes B + A \otimes B')$
- $d^2 f(X) = \operatorname{tr} A(dX)B \, dX \iff Hf(X) = \frac{1}{2}K_{qn}(A' \otimes B + B' \otimes A)$

## Practical Tips (Tacit Knowledge)

1. **Think of matrices as units**, not individual elements
2. **Prove theorems for $n=2$ and $n=3$ first** - if it works for $n=3$, it probably works in general
3. **Test with diagonal matrices** when a matrix is symmetric
4. **To prove $A = B$**, prove $C = A - B = 0$ (often easier)
5. **Use $\operatorname{tr} C'C = 0$** to prove $C = 0$
6. **Always use the correct definition** of matrix derivative
7. **For Hessian, start with first differential**, not first derivative
8. **Symmetrize $B(x)$** in $d^2 f(x) = (dx)'B(x)dx$

## Applications

The reference material includes worked examples:

1. **Least Squares** (Section 6): Constrained and unconstrained
2. **Maximum Likelihood** (Section 13): Multivariate normal
3. **ML with Parameters in Design Matrix** (Section 14)
4. **Eckart-Young Theorem** (Section 15): Matrix approximation

## Reference

For complete theory, proofs, and exercises, see [references/magnus_matrix_calculus.md](references/magnus_matrix_calculus.md) - the full text of "A gentle introduction to matrix calculus" by Jan R. Magnus.

## Resources

### references/
- **magnus_matrix_calculus.md** - Complete tutorial text with all theorems, proofs, and exercises
