<div align="center">

# 🔬 Basics of SciPy

**A beginner-friendly introduction to scientific computing in Python, and the maths behind machine learning.**

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-1.15%2B-8CAAE6?logo=scipy&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-2.x-013243?logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-success)

</div>

---

## 📖 Overview

This repository contains a hands-on Jupyter notebook that introduces **SciPy**, Python's open-source library for scientific and technical computing. It covers three core areas of mathematics that machine learning is built on:

| # | Topic | What you learn | Why it matters for ML |
|:-:|---|---|---|
| 1 | **Calculus** | Numerical derivatives (1st and 2nd order) | Gradient descent, the way models learn |
| 2 | **Combinatorics** | Permutations and combinations | Probability and model selection |
| 3 | **Linear Algebra** | Matrices, determinants, inverses | Datasets as matrices, linear regression |

---

## 🧱 NumPy vs SciPy

> **NumPy *holds* the numbers. SciPy *solves* problems with them.**

| | **NumPy** | **SciPy** |
|---|---|---|
| Purpose | Store and manipulate arrays | Advanced scientific algorithms |
| Depends on | Nothing | NumPy |
| Examples | `mean`, `sum`, `reshape` | `derivative`, `linalg.inv`, `optimize`, `stats` |

---

## 📂 Repository Structure

```
Basics_Of_Scipy/
├── 2. SciPy.ipynb    # Main notebook: code + step-by-step explanations
└── README.md         # You are here
```

---

## 📘 What's Inside the Notebook

The notebook is written so that **you don't need any outside help**. Every code cell has a plain-English explanation, a worked example by hand, and a note on why it matters for machine learning.

| Section | Explanations included |
|---|---|
| **0. NumPy vs SciPy** | "Holds vs solves", comparison table, analogies, where they overlap, how both fit into ML |
| **1. Getting started** | Installing SciPy, checking your version and why it matters |
| **2. Derivatives** | Slope intuition, the power rule worked by hand, the `scipy.misc` → `scipy.differentiate` story, `lambda` and `.df`, floating-point error, a runnable **gradient descent** demo |
| **3. Permutations & combinations** | "Does order matter?", full lists for 4 people, factorial, both formulas worked step by step, why `C = P ÷ r!`, probability, a runnable **Naive Bayes** spam-filter demo |
| **4. Linear algebra** | Matrices and datasets, row × column multiplication (`@` vs `*`), the identity matrix, determinants (2×2 and 3×3 by hand), the inverse recipe, **why the inverse formula works**, solving equations, a runnable **linear regression** demo |
| **📝 Practice** | Exercises for every section, with collapsible answers |
| **📋 Cheat sheet** | Every function on one page, plus memory tricks |

---

## 🚀 Getting Started

### 1. Prerequisites
- Python **3.10** or newer
- Basic Python knowledge (variables, functions, lists)

### 2. Install the dependencies
```bash
pip install numpy scipy jupyter
```

### 3. Launch the notebook
```bash
jupyter notebook "2. SciPy.ipynb"
```
Or open it directly in **VS Code** with the Jupyter extension.

### 4. Verify your setup
```python
import scipy, numpy
print(scipy.__version__, numpy.__version__)
```

---

## 🧮 Quick Reference

### 1. Derivatives
```python
from scipy.differentiate import derivative

f = lambda x: x**2 + x + 1

derivative(f, 2).df                          # f'(2)  = 5.0
derivative(lambda x: derivative(f, x).df, 2).df   # f''(2) = 2.0
```

### 2. Permutations & Combinations
```python
from scipy.special import comb, perm

comb(4, 2)   # 6.0   → order does NOT matter (teams)
perm(4, 2)   # 12.0  → order DOES matter (medals)
```

| | Order matters? | Formula |
|---|:-:|---|
| **Permutation** | ✅ | `n! / (n − r)!` |
| **Combination** | ❌ | `n! / (r! · (n − r)!)` |

### 3. Linear Algebra
```python
import numpy as np
from scipy import linalg

A = np.array([[1, 5, 2],
              [3, 2, 1],
              [1, 2, 1]])

linalg.det(A)          # -2.0  → non-zero, so A is invertible
linalg.inv(A)          # inverse of A
A @ linalg.inv(A)      # ≈ identity matrix
```

**2×2 inverse by hand:** *find the determinant, swap the corners, negate the other two, divide by the determinant.*

```
[ a  b ]⁻¹       1      [  d  −b ]
[ c  d ]    = ─────── × [ −c   a ]        where det = ad − bc
               ad − bc
```

---

## ⚠️ Compatibility Note

Many older tutorials use `scipy.misc.derivative`, which was **deprecated in SciPy 1.10** and **removed in SciPy 1.12**. This notebook uses its replacement, so it needs **SciPy 1.15 or newer**:

| Old (SciPy ≤ 1.11) | New (SciPy ≥ 1.15) |
|---|---|
| `from scipy.misc import derivative` | `from scipy.differentiate import derivative` |
| `derivative(func=f, x0=2)` | `derivative(f, 2).df` |
| `derivative(func=f, x0=2, n=2)` | `derivative(lambda x: derivative(f, x).df, 2).df` |

---

## 🧠 Memory Tricks

| Topic | Trick |
|---|---|
| NumPy vs SciPy | **NumPy *holds* the numbers, SciPy *solves* problems with them.** |
| Derivative | *Slope = "if I move a little, how much does it change?"* |
| Perm vs Comb | **P**ermutation = **P**osition matters. **C**ombination = just the **C**rowd. |
| Matrix shape | **RC Cola:** **R**ows first, then **C**olumns. |
| Determinant | *"Can this matrix be undone?"* Zero means no. |
| 2×2 inverse | *"Find det, swap the corners, flip the rest, divide by det."* |

---

## 🎯 Learning Outcomes

After working through this notebook, you will be able to:

- [x] Explain the difference between NumPy and SciPy
- [x] Compute first and second derivatives numerically
- [x] Tell permutations from combinations and calculate both
- [x] Compute a matrix's determinant and inverse, by hand and in code
- [x] Explain how each topic connects to machine learning

---

## 🗺️ What's Next

```
NumPy  ──►  SciPy  ──►  Pandas  ──►  Matplotlib  ──►  scikit-learn
           (you are here)
```

---

## 📚 Resources

- [SciPy Official Documentation](https://docs.scipy.org/doc/scipy/)
- [SciPy User Guide](https://docs.scipy.org/doc/scipy/tutorial/index.html)
- [NumPy Documentation](https://numpy.org/doc/)
- [3Blue1Brown, *Essence of Linear Algebra*](https://www.3blue1brown.com/topics/linear-algebra), a visual introduction to matrices

---

<div align="center">

⭐ **If you found this helpful, consider giving the repository a star!** ⭐

</div>
