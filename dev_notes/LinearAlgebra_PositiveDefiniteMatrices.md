...menustart

 - [6 Positive Definite Matrices](#c4ac5577c068be490d5dc0e124314e32)
	 - [6.1 MINIMA , MAXIMA , AND SADDLE POINTS](#b7b91c67e89390f8298af104c60585f7)
		 - [Definite versus Indefinite: Bowl versus Saddle  (TODO)](#e0e36c552eecb66daf84e448cf5ed7e8)
		 - [Higher Dimensions: Linear Algebra](#e59a80ec6d81dedf197cebeea3a20a00)
	 - [6.2 TESTS FOR POSITIVE DEFINITENESS](#76c7d53a0682ab1c09ff64d5d3549d0f)
		 - [Positive Definite Matrices and Least Squares](#01201db7b9090769e9708a314cf02459)

...menuend




<h2 id="c4ac5577c068be490d5dc0e124314e32"></h2>
# 6 Positive Definite Matrices

<h2 id="b7b91c67e89390f8298af104c60585f7"></h2>
## 6.1 MINIMA , MAXIMA , AND SADDLE POINTS

Up to now, we have hardly thought about the **signs of the eigenvalues**. 

We couldn't ask whether λ was positive before it was known to be real. Chapter 5 established that every symmetric matrix has real eigenvalues. 

Now we will find a test that can be applied directly to A, without computing its eigenvalues, which will guarantee that all those eigenvalues are positive. 

The test brings together three of the most basic ideas in the book *pivots*, *determinants*, and *eigenvalues*.

---

The signs of the eigenvalues are often crucial. For stability in differential equations, we needed negative eigenvalues so that e<sup>λt</sup> would decay. 

The new and highly important problem is to recognize a ***minimum point***. This arises throughout science and engineering and every problem of optimization. The mathematical problem is to move the second derivative test F" > 0 into n dimensions. Here are two examples:

```
F(x,y) = 7 + 2(x+y)² - ysiny - x³
f(x,y) = 2x² + 4xy + y²
```

Does either F(x, y) or f(x, y) have a minimum at the point x = y = 0 ?

***Remark 1*** The ***zero-order*** terms F(0, 0) = 7 and f(0, 0) = 0 have no effect on the answer. They simply raise or lower the graphs of F and f .

***Remark 2*** The ***linear terms*** give a necessary condition: To have any chance of a minimum, the first derivatives must vanish at x = y = 0:


![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_minima_example.png)

Thus (x,y) = (0,0) is a stationary point for both functions.  The surface z = F(x,y) is tangent to the horizontal plane z = 7 , and the surface z = f(x,y) is tangent to the plane z = 0.  The question is whether the graphs *go above those planes or not*, as we move away from the tangency point x = y = 0.

***Remark 3*** The second derivatives at (0, 0) are decisive:

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_minima_remark3.png)

These second derivatives 4, 4, 2 contain the answer. Since they are the same for F and f, they must contain the same answer. The two functions behave in exactly the same way near the origin. ***F has a minimum if and only if f has a minimum***. I am going to show that those functions don't!

***Remark 4*** The *higher-degree terms* in F have no effect on the question of a local minimum, but they can prevent it from being a global minimum. In our example the term -x³ must sooner or later pull F toward -∞. For f(x, y), with no higher terms, all the action is at (0, 0).

*Every quadratic form f = ax² + 2bxy + cy² has a stationary point at the origin, where ∂f/∂x = ∂f/∂y = 0.*  A local minimum would also be a global minimum. The surface z = f (x, y) will then be shaped like a bowl, resting on the origin (Figure 6.1).

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_F6.1.png)

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_graph_x2_2xy_y2.png)

> function graph of f = x² + 2xy + y²

If the stationary point of F is at x = α, y = β, the only change would be to use the second derivatives at α, β:  

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_minima_quad_part_of_F.png)

This f(x, y) behaves near (0, 0) in the same way that F(x, y) behaves near (α, β).


The third derivatives are drawn into the problem when the second derivatives fail to give a definite decision. That happens when the quadratic part is singular. For a true minimum, f is allowed to vanish only at x = y = 0. When f(x, y) is strictly positive at all other points (the bowl goes up), it is called ***positive definite***.

<h2 id="e0e36c552eecb66daf84e448cf5ed7e8"></h2>
### Definite versus Indefinite: Bowl versus Saddle  (TODO)

TODO

<h2 id="e59a80ec6d81dedf197cebeea3a20a00"></h2>
### Higher Dimensions: Linear Algebra

Calculus would be enough to find our conditions F<sub>xx</sub> > 0 and F<sub>xx</sub>F<sub>yy</sub> > F<sub>xy</sub>² for a minimum. But linear algebra is ready to do more, because the second derivatives fit into a symmetric matrix A. The terms ax² and cy² appear *on the diagonal*. The cross derivative 2bxy is split between the same entry b above and below.  A quadratic f(x, y) comes directly from a symmetric 2 by 2 matrix! 

```
xᵀAx in R² :  

ax² + 2bxy + cy² = [x y]⎡a b⎤⎡x⎤.    (4)
                        ⎣b c⎦⎣y⎦
```

This identity (please multiply it out) is the key to the whole chapter.  It generalizes immediately to n dimensions, and it is a perfect shorthand for studying maxima and minima. When the variables are x₁, ... , xn, they go into a column vector x. ***For any symmetric matrix A, the product xᵀAx is a pure quadratic form f(x₁, ... , xn) = a₁₁x₁² + 2a₁₂x₁x₂ + ... + a<sub>nn</sub>x<sub>n</sub>²*** . 


There are no higher-order terms or lower-order terms-only second-order. The function is zero at x = (0, ... , 0), and its first derivatives are zero. The tangent is flat; this is a stationary point. We have to decide if x = 0 is a minimum or a maximum or a saddle point of the function f = xᵀAx.

---

**Example 3** 

```
f = 2x² + 4xy + y² and 

A = ⎡2 2⎤  -> saddle point.
    ⎣2 1⎦
```

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_2x2_4xy_y2.png)

> f = 2x² + 4xy + y²

**Example 5**

```
f = 2x₁² - 2x₁x₂ + 2x₂² - 2x₂x₃ + 2x₃² 

    ⎡ 2 -1  0⎤
A = ⎢-1  2 -1⎥
    ⎣ 0 -1  2⎦
```

minimum at (0, 0, 0).

---

Any function F(x₁, ... , xn) is approached in the same way. At a stationary point all first derivatives are zero.  A is the **"second-derivative matrix"** with entries **aᵢⱼ = ∂²F / ∂xᵢ∂xⱼ**. This automatically equals **aⱼᵢ = ∂²F / ∂xⱼ∂xᵢ** , so A is symmetric.  ***Then F has a minimum when the pure quadratic xᵀAx is positive definite.*** These second-order terms control F near the stationary point:


```
Taylor series:   F(x) = F(0) + xᵀ(grad F) + 1/2·xᵀAx + higher order terms.   (6)
```

At a stationary point, grad F = (∂F/∂x₁, ... , ∂F/∂xn) is a vector of zeros. The second derivatives in xᵀAx take the graph up or down (or saddle). If the stationary point is at x₀  instead of 0, F(x) and all derivatives are computed at x₀. Then x changes to x - x₀ on the right-hand side.


The next section contains the tests to decide whether xᵀAx is positive (the bowl goes up from x = 0). Equivalently, the tests decide whether the matrix A is positive definite -- which is the main goal of the chapter.

---

<h2 id="76c7d53a0682ab1c09ff64d5d3549d0f"></h2>
## 6.2 TESTS FOR POSITIVE DEFINITENESS

Which symmetric matrices have the property that xᵀAx > 0 for all nonzero vectors x?

There are 4 or 5 different ways to answer this question, and we hope to find all of them. The previous section began with some hints about the signs of eigenvalues, but that gave place to the tests on a, b, c:

```
A = ⎡a b⎤  is positive definite when a > 0 and ac - b² > 0.
    ⎣b c⎦
```

From those conditions, ***both eigenvalues are positive***.  

 - Their product λ₁λ₂ is the determinant ac - b² > 0, so the eigenvalues are either both positive or both negative. 
 	- c must be positive
 - They must be positive because their sum is the trace a + c > 0.

Looking at a and ac - b², it is even possible to spot the appearance of the ***pivots***. They turned up when we decomposed xᵀAx into a sum of squares:

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_sum_of_square.png)

Those coefficients a and (ac - b²)/a are the pivots for a 2 by 2 matrix. For larger matrices the pivots still give a simple test for positive definiteness: xᵀAx stays positive when n independent squares are multiplied by ***positive pivots***.

One more preliminary remark. The two parts of this book were linked by the chapter on determinants. Therefore we ask what part determinants play.

***It is not enough to require that the determinant of A is positive***.

If a = c = -1 and b = 0, then det(A) = 1 but A = -I = negative definite.  The determinant test should apply not only to A itself, giving ac - b² > 0, but also to the 1 by 1 submatrix a in the upper left-hand corner.

The natural generalization will involve all n of the upper left submatrices of A:

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_n_submatrices_of_A.png)

Here is the main theorem on positive definiteness, and a reasonably detailed proof:

**6B** ***Each of*** the following tests is a necessary and sufficient condition for the ***real symmetric*** matrix A to be ***positive definite***:

 1. xᵀAx > 0 for all non zero real vectors x.
 2. All the eigenvalues of A satisfy λᵢ > 0.
 3. All the upper left submatrices A<sub>k</sub> have positive determinants.
 4. All the pivots (without row exchanges) satisfy d<sub>k</sub> > 0.

**Proof**:  Condition 1. defines a positive definite matrix. Our first step shows that each eigenvalue will be positive:

```
  If Ax = λx, then xᵀAx = xᵀλx = λ·‖x‖² .
```

***A positive definite matrix has positive eigenvalues, since xᵀAx > 0***.

Now we go in the other direction. If all λᵢ > 0, we have to prove xᵀAx > 0 for every vector x (not just the eigenvectors).

Since symmetric matrices have a full set of orthonormal eigenvectors, any x is a combination c₁x₁ + ... + cnxn. Then

```
Ax = c₁Ax₁ + ... + cnAxn = c₁λx₁ + ... + cnλxn.
```

Because of the orthogonality xᵢᵀxⱼ = 0, and the normalization xᵢᵀxᵢ = 1 , 

```
xᵀAx = (c₁x₁ᵀ + ... + cnxnᵀ )(c₁λx₁ + ... + cnλxn)
	 = c₁²λx₁ + ... + cn²λ
```

If every λᵢ > 0, then equation (2) shows that xᵀAx > 0.  Thus condition 2 implies condition 1 .

*If condition 1 holds, so does condition 3*: The determinant of A is the product of the eigenvalues. And if condition 1 holds, we already know that these eigenvalues are positive. But we also have to deal with every upper left submatrix A<sub>k</sub>. The trick is to look at all nonzero vectors whose last n - k components are zero: 

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_atAx_n-k_components.png)

Thus A<sub>k</sub> is positive definite. Its eigenvalues (not the same λᵢ!) must be positive. Its determinant is their product, so all upper left determinants are positive.

*If condition 3 holds, so does condition 4* :  According to Section 4.4, the kth pivot d<sub>k</sub> is the ratio of det(A<sub>k</sub>) to det(A<sub>k-1</sub>). If the determinants are all positive, so are the pivots.

*If condition 4 holds, so does condition 1* : We are given positive pivots, and must deduce that xᵀAx > 0. This is what we did in the 2 by 2 case, by completing the square. The pivots were the numbers outside the squares. To see how that happens for symmetric matrices of any size, we go back to *elimination on a symmetric matrix* : A = LDLᵀ .

**Example 1** : Positive pivots 2, 3/2 , 4/3 :

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_positive_definite_LDLT.png)

I want to split xᵀAx into xᵀLDLᵀx:

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_positive_definite_LDLT_2.png)

So xᵀAx is a sum of squares with the pivots 2, 3/2, and 4/3 as coefficients:

![](https://raw.githubusercontent.com/mebusy/notes/master/imgs/LA_positive_definite_LDLT_3.png)

Those positive pivots in D multiply perfect squares to make xᵀAx positive. Thus condition 4 implies condition 1 , and the proof is complete.

It is beautiful that elimination and completing the square are actually the same. Elimination removes x₁ from all later equations.  Similarly, the first square accounts for all terms in xᵀAx involving x₁. The sum of squares has the pivots outside. *The multipliers lᵢⱼ are inside* ! You can see the numbers -1/2 and -2/3 inside the squares in the example.

*Every diagonal entry aᵢᵢ must be positive* . As we know from the examples, however, it is ***far from sufficient*** to look only at the diagonal entries.

The pivots dᵢ are not to be confused with the eigenvalues. For a typical positive definite matrix, they are two completely different sets of positive numbers. In our 3 by 3 example, probably the determinant test is the easiest:

```
Determinant test
  det(A₁) = 2, det(A₂) = 3, det(A₃) = det A = 4.
```

The pivots are the ratios d₁ = 2, d₂ = 3/2, d₃ = 4/3. 

Ordinarily the eigenvalue test is the longest computation. For this A we know the λ's are all positive:


```
Eigenvalue test
  λ₁ = 2 - √2, λ₂ = 2, λ₃ = 2 + √2.
```

Even though it is the hardest to apply to a single matrix, eigenvalues can be the most useful test for theoretical purposes. ***Each test is enough by itself***.

---

<h2 id="01201db7b9090769e9708a314cf02459"></h2>
### Positive Definite Matrices and Least Squares






