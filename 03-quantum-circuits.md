# Quantum circuits

A generic qbit is in the form $|\psi\rangle = c_0 |0\rangle + c_1 |1\rangle$, $c_0, c_1 \in \mathbb{C}$
We can express this state in polar coordinates $|\psi\rangle = \nu_0 e^{i\theta_0} |0\rangle + \nu_1 e^{i\theta_1} |1\rangle$ where $\nu_0, \nu_1, \theta_0, \theta_1 \in \mathbb{R}$.
The equation $|c_0|^2 + |c_1|^2 = 1$ involves 4 real parameters, and the eq represents an hypersphere.
However, it turns out that we can drop 2 degrees of freedom. The first one can be dropped knowing that we can change the global phase and obtain the same physical state, so we multiply by $e^{-i\theta_0}$.
$|\psi\rangle = \nu_0 |0\rangle + \nu_1 e^{i(\theta_1 - \theta_0)} |1\rangle$

The second can be dropped noting that:
$|c_0|^2 + |c_1|^2 = 1 \Rightarrow \nu_0^2 + \nu_1^2 = 1 \Rightarrow \exists \theta : \nu_0 = \cos\theta, \nu_1 = \sin\theta$
$\Rightarrow |\psi\rangle = \cos(\frac{\theta}{2}) |0\rangle + e^{i\phi} \sin(\frac{\theta}{2}) |1\rangle$, $\theta \in [0, \pi]$, $\phi \in [0, 2\pi)$
And the 2 remaining degrees of freedom are latitude and longitude.

$\phi$ is the angle that $|\psi\rangle$ is making with $x$, while $\theta$ is the angle with $z$.
When we change $\phi$ leaving $\theta$ constant we are moving on the latitude, when we change $\theta$ leaving $\phi$ constant we are moving on the longitude.

The most common measurement is the Z measurement where the possible outcomes are the eigenvalues of $Z$: $|0\rangle$ and $|1\rangle$, that are represented on the sphere's poles. Moving on the latitude, we are changing relative phase, and the probabilities of the outcomes of a Z-measurement are constant (we are changing probabilities over the other axis).
Since $\cos(\theta - \pi) = \cos(\theta)$ and $\sin(\phi + \pi) = \sin(\phi)$, we have two points on the sphere representing the same state: one in the upper hemisphere and one in the lower one.
Applying the Pauli matrices, means to rotate the sphere over a particular axis by $\pi$, leaving $|\psi\rangle$ where it was.

Def. A quantum gate is a gate that can be expressed as a unitary matrix
$\Rightarrow$ is reversible

Def. Hadamard gate
The Hadamard gate is applied to a single qbit. And it corresponds to a rotation around $y$ by $\pi/2$ and a rotation around $x$ by $\pi$. Its matrix representation is:
$$H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}$$
$\alpha |0\rangle + \beta |1\rangle$ `---[H]---` $\alpha \frac{|0\rangle + |1\rangle}{\sqrt{2}} + \beta \frac{|0\rangle - |1\rangle}{\sqrt{2}}$

Def. Controlled Not gate

<pre>
|x⟩ ---•--- |x⟩
       |
|y⟩ ---⊕--- |x ⊕ y⟩
</pre>

Def. Toffoli gate

<pre>
|x⟩ ---•--- |x⟩
       |
|y⟩ ---•--- |y⟩
       |
|z⟩ ---⊕--- |z ⊕ (x ∧ y)⟩
</pre>

The Toffoli gate is interesting because it is universal for the classical world. In fact, we can obtain the AND setting $|z\rangle$ to $|0\rangle$ and the NOT setting $|x\rangle$ and $|y\rangle$ to $|1\rangle$. Since the set {AND, NOT} is universal for the classical world $\Rightarrow$ Toffoli gate is universal for the classical world.
Putting $|x\rangle$ to $|1\rangle$ and $|z\rangle$ to $|0\rangle$, we also have the FANOUT of $|y\rangle$.

Def. Fredkin gate

<pre>
|x⟩ ---•--- |x⟩
       |
|y⟩ ---×--- |y⟩ if x=0 else |z⟩
       |
|z⟩ ---×--- |z⟩ if x=0 else |y⟩
</pre>

Also the Fredkin gate is universal setting $|y\rangle = |0\rangle$ we have $|x \land z\rangle$ on the middle output parameter, and setting $|y\rangle = |1\rangle$ and $|z\rangle = |0\rangle$ we have $|\neg x\rangle$ in the middle part.

Def. Pauli matrices
$$X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}$$
$$Y = \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}$$
$$Z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$$
$X$ is the NOT gate. These are ways of rotating the Bloch sphere about $x, y$ and $z$ axis respectively by $\pi$.
$|\psi\rangle$ `---[X]---` $|\psi'\rangle$

Def. Phase shift gate
$$R(\theta) = \begin{bmatrix} 1 & 0 \\ 0 & e^{i\theta} \end{bmatrix}$$
$|\psi\rangle$ `---[R(θ)]---` $|\psi'\rangle$
This gate changes the longitude, leaving the latitude as is.

### Def. Deutsch gate

<pre>
|x⟩ ---•--- |x⟩
       |
|y⟩ ---•--- |y⟩
       |
|z⟩ ---[R(θ)]--- R(θ)|z⟩ if |x⟩=|1⟩ and |y⟩=|1⟩ else |z⟩
</pre>

### Theo. The Deutsch gate is a universal quantum gate.

The set {H, "NOT", $R(\cos^{-1}(3/5))$} is a set of universal quantum gates.
This means that every quantum gate can be expressed as a combination of gates in the set of universal quantum gates.

### Theo. No cloning theorem

Consider a classical CNOT gate, where we put $|y⟩ = |0⟩$, in the classical world. We will have $|x⟩$ on both outputs (fanout).
However, in the quantum world, it is impossible to make a copy of a quantum state.

In fact, let $C: \mathcal{H} \to \mathcal{H} \otimes \mathcal{H}$ a cloning operation, which should be linear and unitary. $C(|x⟩ \otimes |0⟩) = (|x⟩ \otimes |x⟩)$.
Since $C$ is a cloning operation, $C(|0⟩ \otimes |0⟩) = |0⟩ \otimes |0⟩$ and $C(|1⟩ \otimes |0⟩) = |1⟩ \otimes |1⟩$.
Let's take a superposition: $C( \frac{|0⟩ + |1⟩}{\sqrt{2}} \otimes |0⟩ ) = \frac{|0⟩ + |1⟩}{\sqrt{2}} \otimes \frac{|0⟩ + |1⟩}{\sqrt{2}} = \frac{1}{2} (|00⟩ + |01⟩ + |10⟩ + |11⟩)$

But, since $C$ is linear:
$C( \frac{|0⟩ + |1⟩}{\sqrt{2}} \otimes |0⟩ ) = \frac{1}{\sqrt{2}} ( C(|0⟩ \otimes |0⟩) + C(|1⟩ \otimes |0⟩) ) = \frac{1}{\sqrt{2}} ( |0⟩ \otimes |0⟩ + |1⟩ \otimes |1⟩ ) \neq \frac{1}{2} (|00⟩ + |01⟩ + |10⟩ + |11⟩)$

So $C$ is not linear, and hence is not a quantum gate.

<pre>
|ψ⟩ ---•--- |ψ₁⟩
       |
|0⟩ ---⊕--- |ψ₂⟩
</pre>

In the CNOT example, $|\psi_f⟩ = [\alpha|00⟩ + \beta|11⟩]$
After the CNOT acts on the second qbit we have $|\psi_f⟩ = \alpha|00⟩ + \beta|11⟩ \neq |\psi⟩ \otimes |\psi⟩$
So $|\psi_f⟩ \neq |\psi⟩ \otimes |\psi⟩$, in fact $|\psi⟩ \otimes |\psi⟩ = (\alpha|0⟩ + \beta|1⟩) \otimes (\alpha|0⟩ + \beta|1⟩) = \alpha^2|00⟩ + \alpha\beta|01⟩ + \alpha\beta|10⟩ + \beta^2|11⟩$
Which has no solution of $\alpha$ and $\beta$ to be = $|\psi_f⟩$.

### Def. Bell states: $|\beta_{xy}⟩ = \frac{|0,y⟩ + (-1)^x |1, \bar{y}⟩}{\sqrt{2}}$

<pre>
|x⟩ ---[H]---•--- |ψ₁⟩
             |
|y⟩ ---------⊕--- |ψ₂⟩
</pre>

$\Rightarrow |\psi_0⟩ = |00⟩, |\psi_1⟩ = \frac{|0⟩ + |1⟩}{\sqrt{2}}, |\psi_2⟩ = \frac{|00⟩ + |11⟩}{\sqrt{2}}$
$\Rightarrow |\psi_0⟩ = |10⟩, |\psi_1⟩ = \frac{|0⟩ - |1⟩}{\sqrt{2}}, |\psi_2⟩ = \frac{|00⟩ - |11⟩}{\sqrt{2}}$
$|\psi_2⟩ = \frac{|00⟩ + |11⟩}{\sqrt{2}}$
$|\psi_2⟩ = \frac{|00⟩ + |11⟩}{\sqrt{2}}$
$|\psi_2⟩ = \frac{|00⟩ + |11⟩}{\sqrt{2}}$

### Def. Quantum teleportation is a technique for moving quantum states from one point in space to another, without the need to have a quantum communication channel.

To realize quantum teleportation, Alice and Bob creates the Bell state $\frac{|00⟩ + |11⟩}{\sqrt{2}}$ when they are together. When Bob comes back to his home in Alpha Centauri, Alice wants to send him the state $|\psi⟩$, and to do that she can use a radio signal or any classical information channel.
Since $|\psi⟩$ is unknown for Alice, she doesn't know how to encode its state unless she measure it making it collapsing in $|0⟩$ or $|1⟩$. Even if she knew the state, she'd need an infinite amount of information to describe two real numbers with infinite precision.
But it turns out that she can build the following quantum circuit and send Bob the output so Bob can reconstruct $|\psi⟩$.

<pre>
Alice:
|ψ⟩              ---[H]---•---[M₁]---(classical bit M₁)-->-----------•
                          |                                          |
|β₀₀⟩ (Alice's)  ---------⊕---[M₂]---(classical bit M₂)-->-----•     |
                                                               |     |
                                                               |     |
Bob:                                                           |     |
|β₀₀⟩ (Bob's)    ---------------------------------------------[X]---[Z]---|ψ⟩
                  ↑    ↑    ↑                                   
                |ψ₀⟩  |ψ₁⟩ |ψ₂⟩                    
</pre>

$|\psi_0⟩ = |\psi⟩ |\beta_{00}⟩ = \frac{1}{\sqrt{2}} [ \alpha|0⟩(|00⟩ + |11⟩) + \beta|1⟩(|00⟩ + |11⟩) ]$

$|\psi_1⟩ = \frac{1}{2} [ \alpha(|0⟩ + |1⟩)(|00⟩ + |11⟩) + \beta(|0⟩ - |1⟩)(|00⟩ + |11⟩) ]$

$|\psi_2⟩ = \frac{1}{2} [ |00⟩(\alpha|0⟩ + \beta|1⟩) + |01⟩(\alpha|1⟩ + \beta|0⟩) + |10⟩(\alpha|0⟩ - \beta|1⟩) + |11⟩(\alpha|1⟩ - \beta|0⟩) ]$

Then Alice measure $M_1$ and $M_2$ and get 2 bits. If she measure $|00⟩$, then Bob already has $|\psi⟩$. If she measure $|01⟩$, then Bob can apply $X$ to his qbit and has $|\psi⟩$ again. If $|10⟩$, Bob applies $Z$ and if $|11⟩$, Bob applies $X$ and $Z$.
Speed of light is not violated because we need to send classical information. State is not cloned because Alice destroyed her $|\psi⟩$ measuring it.
