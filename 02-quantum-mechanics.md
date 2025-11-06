# Quantum mechanics

There are many ways to realize a physical qbit. One of them is to swing an electron in its ground state ($|0\rangle$) with half the energy it needs to reach its excited state ($|1\rangle$). With this technique, the electron will be in the state:
$|\psi\rangle = \frac{1}{\sqrt{2}} |0\rangle + \frac{1}{\sqrt{2}} |1\rangle$

In general, a qbit is in a linear combination of $|0\rangle$ and $|1\rangle$.
$|\psi\rangle = \alpha |0\rangle + \beta |1\rangle$, $\alpha, \beta \in \mathbb{C}$, $|\alpha|^2 + |\beta|^2 = 1$

Since $\alpha, \beta \in \mathbb{C} \Rightarrow \alpha = a+ib$, $\beta = c+id \Rightarrow |\alpha|^2 + |\beta|^2 = 1 \Leftrightarrow a^2+b^2+c^2+d^2 = 1$, which is the equation of an hypersphere. But since $|\psi\rangle = e^{i\gamma} |\psi\rangle \forall \gamma \in \mathbb{R}$
$\Rightarrow$ we can drop a dimension and think of the state of a qbit as a point in the 3D sphere.
$|\psi\rangle = \cos(\frac{\theta}{2}) |0\rangle + e^{i\phi} \sin(\frac{\theta}{2}) |1\rangle$

When we take a measure of the qbit state, we get $|0\rangle$ with probability $|\alpha|^2$ or $|1\rangle$ with probability $|\beta|^2$.

If we take two qbits, then the state vector is:
$|\psi\rangle = \alpha_{00} |00\rangle + \alpha_{01} |01\rangle + \alpha_{10} |10\rangle + \alpha_{11} |11\rangle$ $\sum |\alpha_{ij}|^2 = 1$
For instance, the Bell state is:
$|\psi\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$

This means that when we measure the first qbit, we also know the value of the second qbit and vice-versa.

For $n=500$ qbit, the number of amplitudes is greater than the number of atoms in the universe.

Post. associated with any isolated physical system there is an Hilbert space known as the **state space** of the system. The system is completely described by its **state vector**, which is a unit vector in the state space.

In the case of a single qbit, the state space is 2D, and an arbitrary vector in the state space is:
$|\psi\rangle = \alpha |0\rangle + \beta |1\rangle$, $\langle\psi|\psi\rangle = 1$

$\alpha$ and $\beta$ are called **amplitudes** for the state $|\psi\rangle$. ($|\psi\rangle = \sum_i \alpha_i |\phi_i\rangle$)

Post. The evolution of a closed quantum system is described by a unitary transformation:
$|\psi'\rangle = U |\psi\rangle$
Where $|\psi\rangle$ is the state at time $t_1$, $|\psi'\rangle$ at time $t_2$, and $U$ depends only on $t_1$ and $t_2$.

Post (continuous time) The time evolution of the state of a closed quantum system is described by the Schrödinger equation:
$i \hbar \frac{d|\psi\rangle}{dt} = H |\psi\rangle$
Where $H$ is the Hamiltonian of the closed system and it is Hermitian.

Since $H$ is Hermitian, we can diagonalize it: $H = \sum_E E |E\rangle \langle E|$
Where the states $|E\rangle$ are called the energy eigenstates and $E$ is the energy of the state $E$. The lowest energy is the ground state energy and the corresponding eigenspace is the ground state.

One can say that a system composed by the atom and the laser that excite it is not closed because we interact with it with a laser or with a gate and this is true. By the way, we can write an atomic Hamiltonian which has some terms related with the system interacting with it (like the laser intensity) and that is still an Hamiltonian.

Post. Quantum measurements are described by a collection of measurement operators $\{M_m\}$, where $m$ is the measurement outcome.
If the state is $|\psi\rangle$ before the measurement, then the probability that $m$ occurs is $p(m) = \langle\psi| M_m^\dagger M_m |\psi\rangle$, and the state after the measurement is $\frac{M_m |\psi\rangle}{\sqrt{p(m)}}$. The measurement satisfied the completeness equation:
$\sum_m M_m^\dagger M_m = I$

Suppose that we have a set of possible states $|i\rangle$ for our system and we want to determine in which $i$ is our system. We can do it only if $|i\rangle$ are orthogonal. Defining the measurement operator as $M_i = |i\rangle \langle i|$
$\Rightarrow p(j) = \langle\psi_i| M_j M_j |\psi_i\rangle = \langle\psi_i| |j\rangle \langle j| |j\rangle \langle j| |\psi_i\rangle = |\langle j|\psi_i\rangle|^2 = \delta_{ij}$
But if the states are not orthogonal, I have probability greater than $0$ for more than one state.

Two quantum states can be distinguished $\Leftrightarrow$ they are orthonormal.

Def. A projective measurement is a measurement tied to a specific physical observable like spin and energy.

Post. A projective measurement is described by an observable $M$ which is an Hermitian operator on the state space of the system being described. This observable has a spectral decomposition:
$M = \sum_m m P_m$ $\to$ this includes degeneracies of the eigenvalues. For instance, if $m$ has $d(m)$ eigenvalues $\to P_m = |m,1\rangle \langle m,1| + ... + |m, d(m)\rangle \langle m, d(m)|$
Where $P_m$ is the projector onto the eigenspace of $M$ with eigenvalue $m$. The eigenvalues $m$ are the possible outcomes of the measurement.
The probability of getting $m$ is:
$p(m) = \langle\psi| P_m |\psi\rangle$
And, after the measurement, the state will be:
$|\psi'\rangle = \frac{P_m |\psi\rangle}{\sqrt{p(m)}}$

Theo. The average value of the measurement is:
$\langle M \rangle = \langle\psi| M |\psi\rangle$
And the variance is:
$[\Delta(M)]^2 = \langle M^2 \rangle - \langle M \rangle^2$

The measurement of the spin along a $\vec{v}$ axis is given by: $\vec{v} \cdot \vec{\sigma} = V_x \sigma_x + V_y \sigma_y + V_z \sigma_z$

Theo. Heisenberg uncertainty principle. Given two observable $A$ and $B$, we always have:
$\Delta(A) \Delta(B) \ge \frac{1}{2} |\langle\psi| [A,B] |\psi\rangle|$

Suppose that $A$ is the measurement of the position, whilst $B$ is the measurement of the momentum. This does not mean that measuring the position we disturb the momentum and vice-versa. This means that a large number of particle in a state $|\psi\rangle$ is well defined in terms of position, we can't ensure that we are picking particles with similar momentum and vice-versa.

Theo. POVM. Let a quantum system be described by its state $|\psi\rangle$. A POVM measurement is described by a set of positive operators $\{E_m\}$ which is complete:
$\sum_m E_m = I$. The probability of obtaining $m$ is:
$p(m) = \langle\psi| E_m |\psi\rangle$.
To determine the state after the measurement, we need to specify $M_m$:
$E_m = M_m^\dagger M_m$

This means that, given 2 states which are not-orthogonal, we can't specify a set of measurement operator that allow us to determine with 100% probability if the state is the first, the second or we don't know.

Def. We say that two states $|\psi_1\rangle$ and $|\psi_2\rangle$ differs by a **global phase factor** if $|\psi_2\rangle = e^{i\theta} |\psi_1\rangle, \theta \in \mathbb{R}$. $|\psi_1\rangle$ and $|\psi_2\rangle$ have the same probability to occur and they are physically identical and undistinguishable.
We say that $|\psi_1\rangle$ and $|\psi_2\rangle$ differs by a **relative phase factor** if each of the amplitudes in the basis are the same or differs by a phase factor. In other words, being $|\psi_1\rangle = \sum_i a_i |i\rangle$ and $|\psi_2\rangle = \sum_i b_i |i\rangle \Rightarrow a_i = e^{i\theta_i} b_i$.

Many important measurements are not projective. To be projective it means applying it twice we get the same result. If we use a screen to measure the position of a photon we destroy it, so it's not projective.

Post. The state space of a composite physical system is the tensor product of the state spaces of the component physical systems. Moreover, if we have systems numbered 1 through $m$, the joint state of the system is $|\psi_1\rangle \otimes |\psi_2\rangle \otimes \dots \otimes |\psi_m\rangle$.
