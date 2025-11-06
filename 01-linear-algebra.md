# Linear Algebra

**Definition:** A **vector space** is a collection of elements closed under multiplication with scalar and addition.

**Definition:** Each element of the vector space is called a **vector** and it is often represented with the column matrix notation

$$
|v\rangle = \begin{pmatrix}
z_1 \\
z_2 \\
\vdots \\
z_n
\end{pmatrix}
$$

or with the **Dirac notation** $|\psi\rangle$ (standard for QM).

In QM we are often interested in the vector space $\mathbb{C}^n$. A vector space is such if a set of axioms is satisfied. One of them states that a vector $0$ should exist in the vector space, $0$ has the property that $|v\rangle + 0 = |v\rangle$ $\forall |v\rangle$ in the vector space, and $z \cdot 0 = 0$ $\forall z \in \mathbb{C}$.

**Definition:** A **spanning set** for a vector space $V$ is a set of vectors $\{|v_1\rangle, \dots, |v_m\rangle\}$ such that any vector $|v\rangle \in V$ can be expressed as a linear combination of vectors in that set. $|v\rangle = \sum_i z_i |v_i\rangle$.

For instance, the vectors $|v_1\rangle = \begin{pmatrix} 3 \\ 1 \end{pmatrix}$ and $|v_2\rangle = \begin{pmatrix} i \\ 0 \end{pmatrix}$ are a spanning set for $\mathbb{C}^2$.

**Definition:** A set of vectors $\{|v_1\rangle, \dots, |v_m\rangle\}$ is said to be **linearly independent** if the equation $z_1|v_1\rangle + \dots + z_m|v_m\rangle = 0$ has only one solution: $z_1 = z_2 = \dots = z_m = 0$.

**Theorem:** Any two sets of linearly independent vectors that span $V$ contain the same number of elements.

**Definition:** A **basis** of a vector space $V$ is a spanning set of linearly independent vectors.

**Definition:** The **dimension** of a vector space $V$ is the number of elements in its basis.

**Definition:** A **linear operator** between two vector spaces $V$ and $W$ is a function $A: V \to W$ which is linear in its inputs:
$A(z_1|v_1\rangle + z_2|v_2\rangle) = z_1 A|v_1\rangle + z_2 A|v_2\rangle$
(or summation $\sum_i$)
$A(\sum_i z_i |v_i\rangle) = \sum_i z_i A|v_i\rangle$

If $V=W$, we say that $A$ is a linear operator on the vector space $V$.

For instance, the identity $I$ and the zero operator $0$, are linear operators.

Each linear operator has a matrix representation, and each matrix can be seen as a linear operator.

**Definition:** Some very important matrices are the **Pauli matrices**:
$\sigma_0 = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} \quad \sigma_x = X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \quad \sigma_y = Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} \quad \sigma_z = Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$

**Definition:** An **inner product** $\langle \cdot, \cdot \rangle$ on the field $\mathbb{C}$ is a function that takes two vectors as an input and outputs a scalar in $\mathbb{C}$, which has the following properties:

1.  Linearity in the second argument: $\langle v, \sum_i z_i w_i \rangle = \sum_i z_i \langle v, w_i \rangle$
2.  $\langle v, w \rangle = \langle w, v \rangle^*$
3.  $\langle v, v \rangle \ge 0 \quad \langle v, v \rangle = 0 \iff |v\rangle = 0$

In QM, we use the notation $\langle v | w \rangle$ for the inner product. For instance we can use the inner product defined by:
$\langle v | w \rangle = \sum_i z_i^* w_i = \begin{pmatrix} z_1^* & \dots & z_n^* \end{pmatrix} \begin{pmatrix} w_1 \\ \vdots \\ w_n \end{pmatrix}$

**Definition:** A **vector space** with a defined inner product is called an **inner product space**. In the case of finite dimensional complex vector spaces, a **Hilbert space** is exactly the same thing as an inner product space.

**Definition:** We say that two vectors $|v\rangle$ and $|w\rangle$ are **orthogonal** if their inner product is $0$. $\langle v | w \rangle = 0$.

**Definition:** The **norm** of a vector is the square root of the inner product with itself. $|| |v\rangle || = \sqrt{\langle v | v \rangle}$

**Definition:** A **unit vector** is a vector whose norm is $1$. We say that a vector is **normalized** if it is a unit vector. To **normalize** a vector, it means to divide it by its norm, so the result is a unit vector.

Of course, we can normalize all vectors but the $0$.

**Definition:** We say that a set of vectors $\{|v_i\rangle\}$ is **orthonormal** if it's composed only of unit vectors orthogonal one to another. $\langle v_i | v_j \rangle = \delta_{ij}$

Suppose we have a basis $B = \{|w_1\rangle \dots |w_n\rangle\}$ for some vector space $V$. There is a method, called the **Gram-Schmidt procedure**, which can be used to generate an orthonormal basis $\{|v_i\rangle\}$.
First we define:
$|v_1'\rangle = |w_1\rangle$
$|v_1\rangle = \frac{|v_1'\rangle}{|| |v_1'\rangle ||}$

...and then, inductively (for $k \ge 1$):
$|v_{k+1}'\rangle = |w_{k+1}\rangle - \sum_{i=1}^k \langle v_i | w_{k+1} \rangle |v_i\rangle$
$|v_{k+1}\rangle = \frac{|v_{k+1}'\rangle}{|| |v_{k+1}'\rangle ||}$

Given two vectors $|v\rangle$ and $|w\rangle$ in a Hilbert space we define **outer product** of the two vectors, the quantity $|v\rangle\langle w|$.

The outer product is a matrix which has the property to _[side note: take the projection along $|w\rangle$]_ input a vector $|v_i\rangle$ along $|w\rangle$ and create an output vector in the direction of $|v\rangle$, with a length proportional to that component.
$(|v\rangle\langle w|) |v_i\rangle = |v\rangle (\langle w | v_i \rangle) = \langle w | v_i \rangle |v\rangle$

**Theorem:** **Completeness relation**: Let $\{|v_i\rangle\}$ be an orthonormal basis for the vector space $V \implies \sum_i |v_i\rangle\langle v_i| = I$

We can represent any operator in the outer product notation. Let $A: V \to W$ a linear operator, $\{|v_i\rangle\}$ orthonormal basis for $V$ and $\{|w_j\rangle\}$ orthonormal basis for $W \implies A = I_W A I_V = (\sum_j |w_j\rangle\langle w_j|) A (\sum_i |v_i\rangle\langle v_i|) = \sum_{ij} \langle w_j | A | v_i \rangle |w_j\rangle\langle v_i|$

**Theorem:** **Cauchy-Schwarz**: Let $|v\rangle$ and $|w\rangle$ two vectors in a Hilbert space $V \implies |\langle v | w \rangle|^2 \le \langle v | v \rangle \langle w | w \rangle$

**Definition:** Given a linear operator $A$ on a vector space $V$, we call **eigenvector** of $A$ on $V$ a vector $|v\rangle$ such that $A|v\rangle = \lambda |v\rangle$ for some $\lambda \in \mathbb{C}$. $\lambda$ is called the **eigenvalue** of $A$ corresponding to $|v\rangle$.

We use to find the eigenvalues of an operator $A$ through the **characteristic function** $\det(A - \lambda I) = 0$. Then we use the definition of eigenvectors to find them.

**Definition:** The **eigenspace** corresponding to an eigenvalue $\lambda$ is the set of vectors which have $\lambda$ as an eigenvalue.

**Definition:** A **diagonal representation** of an operator $A$ on $V$ is $A = \sum_i \lambda_i |v_i\rangle\langle v_i|$ where $\{|v_i\rangle\}$ is an orthonormal set of eigenvectors of $A$.

**Definition:** An operator is said to be **diagonalizable** if it has a diagonal representation.

**Definition:** A basis composed of eigenvectors is called **eigenbasis**.

**Definition:** When an eigenspace is more than 1D, we say that it is **degenerate**.

When solving the equation to find the eigenvectors, we find more than one free parameter, we have a degenerate eigenspace.

**Theorem:** Given a linear operator $A$ on a Hilbert space $V$, there exists a unique linear operator $A^\dagger$ on $V$ such that:
$\langle\psi|A|\phi\rangle = \langle A^\dagger \psi | \phi \rangle, \forall |\psi\rangle, |\phi\rangle \in V$

**Definition:** We call **adjoint** or **Hermitian conjugate** of $A$ on $V$, the operator $A^\dagger$ such that the previous statement holds. $A^\dagger = (A^*)^T$

**Theorem:** $(AB)^\dagger = B^\dagger A^\dagger$
This is true because
$\langle\psi|(AB)^\dagger|\phi\rangle = \langle AB \psi | \phi \rangle = \langle B \psi | A^\dagger \phi \rangle = \langle \psi | B^\dagger A^\dagger \phi \rangle$
$(AB)^T = B^T A^T$
For the previous.

**Definition:** If $A = A^\dagger$, we say that $A$ is **self-adjoint** or **Hermitian**.

**Definition:** Given a $d$-dimensional vector space $V$, and a $k$-dimensional vector subspace $W$ of $V$ and given a basis of $W$ $\{|w_i\rangle\}$, we call **projector** of $V$ onto $W$, the operator:
$P \equiv \sum_{i=1}^k |w_i\rangle\langle w_i|$

**Theorem:** The projector is Hermitian $P^\dagger = P$.

**Definition:** The **orthogonal complement** of $P$ is the operator $Q \equiv I - P$, and it is the projector of $V$ onto the subspace spanned by $\{|k+1\rangle, \dots, |d\rangle\}$.

**Definition:** An operator $A$ is said to be **normal** if $A A^\dagger = A^\dagger A$.

**Theorem:** **Spectral decomposition:** An operator is normal $\iff$ is diagonalizable.

**Definition:** An operator $A$ is said to be **unitary** if $A^\dagger A = I$.

**Theorem:** An unitary operator is also normal.

**Theorem:** Given an unitary operator $U \implies \langle U\psi | U\phi \rangle = \langle \psi | \phi \rangle$. In other words, unitary operators preserve inner products.

**Theorem:** Given $\{|v_i\rangle\}$ & $\{|w_i\rangle\}$ two basis of $V$. The operator defined by $U = \sum_i |w_i\rangle\langle v_i|$ is unitary.

**Definition:** We say that an operator $A$ is **positive** if $\langle\psi|A|\psi\rangle \in \mathbb{R}$ and $\langle\psi|A|\psi\rangle \ge 0 \quad \forall |\psi\rangle \in V$. If also $\langle\psi|A|\psi\rangle > 0$, we say that the operator $A$ is **positive definite**.

**Theorem:** Any positive operator is Hermitian, hence, any positive operator has a diagonal representation $\sum_i \lambda_i |i\rangle\langle i|$ with $\lambda_i \ge 0$.

**Theorem:** Eigenvectors with different eigenvalues of an Hermitian matrix are orthogonal.

**Definition:** We call **Kronecker product** between two matrix $A:(m \times n)$ and $B:(p \times q)$ the matrix with size $mp \times nq$:

$$
A \otimes B = \begin{pmatrix} A_{11} B & \dots & A_{1n} B \\ \vdots & & \vdots \\ A_{m1} B & \dots & A_{mn} B \end{pmatrix}
$$

And we read it as $A$ tensor $B$.

**Definition:** We call **tensor product** of two vector spaces $V$ and $W$, a collection of elements $|v\rangle \otimes |w\rangle$ such that:

1.  $\forall z \in \mathbb{C}, |v\rangle \in V, |w\rangle \in W \implies z(|v\rangle \otimes |w\rangle) = (z|v\rangle) \otimes |w\rangle = |v\rangle \otimes (z|w\rangle)$
2.  $|v_1\rangle, |v_2\rangle \in V, |w\rangle \in W \implies (|v_1\rangle + |v_2\rangle) \otimes |w\rangle = |v_1\rangle \otimes |w\rangle + |v_2\rangle \otimes |w\rangle$
3.  $|v\rangle \in V, |w_1\rangle, |w_2\rangle \in W \implies |v\rangle \otimes (|w_1\rangle + |w_2\rangle) = |v\rangle \otimes |w_1\rangle + |v\rangle \otimes |w_2\rangle$

If $\{|v_i\rangle\}$ is a basis for $V$ and $\{|w_j\rangle\}$ is a basis for $W$, then $\{|v_i\rangle \otimes |w_j\rangle\}$ is a basis for $V \otimes W$. $|v_i\rangle \otimes |w_j\rangle$ is sometime written as $|v_i\rangle|w_j\rangle, |v_i, w_j\rangle$ or $|ij\rangle$.

**Theorem:** If $A$ is a linear operator in $V$ and $B$ is a linear operator in $W$, the operator $A \otimes B$ defined as:
$(A \otimes B) (|v\rangle \otimes |w\rangle) = A|v\rangle \otimes B|w\rangle = \sum_{ij} z_i A|v_i\rangle \otimes B|w_j\rangle$
is linear in $V \otimes W$.

**Definition:** We can define an inner product on the tensor space $V \otimes W$:
$(\sum_i z_i |v_i\rangle \otimes |w_i\rangle, \sum_j z_j' |v_j\rangle \otimes |w_j\rangle) \equiv \sum_{ij} z_i^* z_j' \langle v_i | v_j \rangle \langle w_i | w_j \rangle$

Given this inner product, $V \otimes W$ is an Hilbert space and inherits all the notions of adjoint, unitarity, normality and hermiticity.

**Definition:** Given a normal matrix $A$, and a function $f: \mathbb{C} \to \mathbb{C}$, we can define the **matrix function** $f(A) = \sum_i f(\lambda_i) |i\rangle\langle i|$ where $A = \sum_i \lambda_i |i\rangle\langle i|$ is the spectral decomposition of $A$ (which exists because $A$ is normal).

**Definition:** We call **trace** of a matrix $A$ the quantity:
$Tr(A) = \sum_{ii} A_{ii}$

**Theorem:** The trace has the following properties:

- $Tr(AB) = Tr(BA)$
- $Tr(A+B) = Tr(A) + Tr(B)$
- $Tr(zA) = z Tr(A)$

Since the trace is linear and cyclic $\implies$ is invariant under unitary similarity transformations $A \to U A U^\dagger$. $Tr(U A U^\dagger) = Tr(U^\dagger U A) = Tr(A)$.

**Theorem:** $Tr(|v\rangle\langle w|) = \langle w | v \rangle$

**Definition:** The **commutator** between two linear operators $A$ and $B$ is the quantity: $[A, B] = AB - BA$.

**Definition:** The **anti-commutator** between two linear operators $A$ and $B$ is the quantity: $\{A, B\} = AB + BA$.

**Definition:** Given two linear operators $A$ and $B$, we say that they **commute** if $[A, B] = 0$, and they **anti-commute** if $\{A, B\} = 0$.

**Theorem:** **Simultaneous diagonalization theorem:** Given two Hermitian operators $A$ and $B$, $[A, B] = 0 \iff$ exists an orthonormal basis $\{|i\rangle\}$ such that $A$ and $B$ are diagonal with respect to $\{|i\rangle\}$.
In this case, we say that $A$ and $B$ are **simultaneously diagonalizable**.

**Theorem:** **Polar decomposition:** Let $A$ be a linear operator on $V$. There exists a unitary matrix $U$ and two positive operators $J$ and $K$ such that:
$A = UJ = KU$
and $J = \sqrt{A^\dagger A}$, $K = \sqrt{A A^\dagger}$.
If $A$ is invertible $\implies U$ is unique.

**Theorem:** **Singular value decomposition:** Let $A$ be a $m \times n$ matrix. There exist two unitary matrix $U$ and $V$ and a diagonal matrix $D$ with non negative entries such that: $A = U D V$.
The diagonal elements of $D$ are called the **singular values** of $A$.
