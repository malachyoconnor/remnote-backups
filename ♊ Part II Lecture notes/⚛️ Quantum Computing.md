- Lecture 1 - Bits and Qubits
    - What computers can or cannot compute is defined by the laws of physics alone.
    - 3 day computation vs 1 minute for a certain problem - note the problem was simulating itself.
    - Double Slit experiment
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zsYW979FOUjLSg3H5VowyWqQ8yZbMSvLNuWOeg89DbHA49v-fSJiw2xHFICLtx-PAvn9Md82CfoPPr6_UBi-8OO6FmygaI6SnIGdEcw9BoiSkgEpN_IuN_g4s-ujhcQb.png) 
        - You get an interference pattern - telling us light acts as a wave not a particle. 
        - When we fire only a SINGLE photon at a time, we still get an interference patter - gives us wave particle duality. So a single photon can exist in superposition, a photon can go through both slits and appear to interfere with itself.
        - However, if you set up measurement apparatus at one slit or the other, light instead acts as a particle. I.e. measurement collapses a superposition.
    - The qubit
        - A classical bit is either equal to:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aDAj4gj8LJm0HFxdzzyCqXkLi33VOWNLbq1qTNU_VQduEJuXZj4bMpGS281H1RlPgCGrT7xXT28RdIgFhfPLp9ZhEkJy0Xkk-CROfq67L0-_L-6WZ1SJO-2dOpHETdOx.png) 
        - If we are uncertain whether a classical bit B is 0 or 1 we can charactersize it by a probability mass function: $$p(B=0) = p_1; p(B=1)=p_2$$ 
Then we know $p_0 + p_1 = 1$. 
        - A qubit is quite different, it can be in a  __superposition __ of 0 and 1 $$\ket{\psi} = \alpha \ket{0} + \beta \ket{1} = \begin{bmatrix}\alpha \\\beta\end{bmatrix} (\text{Vector notation of a qubit})$$
Where $\alpha, \beta$ are complex numbers s.t. $|\alpha|^2 + |\beta|^2 =1$.    
        - Which of a bra, ket is a row and which is a column?→A ket is the column and a bra is the row - for a ket $\ket a$, $\bra a$ is also the **complex conjugate of **$a$.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/X7n7SkhkEl5ZaIe3CabDHQW6MrAxfcayogt9DSi211O4deWexCkXiceutL1Y38IPApWR3-xrlgR2hrrKojWzk5E4RLutATV0sY8zBmnU_5jj1wkpmKdG7XS7mhrd4ymI.png) 
Turning a bra into a ket or vice versa is called a **conjugate transpose.**
        - Measuring a qubit
            - Any attempt to measure the state results in $\ket{0}$ with probability $|\alpha|^2$ or $\ket{1}$ with probability $|\beta|^2$. This is known as the born rule. After the measurement the system is **in **the measured statae. I.e. $\ket{\psi'}$ will be zero or one.  
            - Further measurement will always yield the same value, this means we can **only **extract one bit of information from the state of a qubit. 
            - The superposition of 0 and 1 states describe ** a physical structure, **and not merely a probability mass function over possible measurement outcomes 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/htAaKu6YEaCGAVbTfIWkS53lMyQnnsrvulHs5CuiWzGqryeuFgtyk5rfKjv9Tbt0VtaEAEOSsqjNK6pPdaLQHLzoZPWp29J3FdIBKEq7VVDEZGi3wvJrowg179qHIYkQ.png)
While all of these have a 50 50 chance of being in the 0 or 1 state if measured, all will result in the system evolving differently when quantum operations are performed. 
        - The Hadamard gate
            - Describe the Hadamard gate ↓ 
                - The Hadamard gate can take $\ket{+} or \ket{-}$ (which are $\frac{1}{\sqrt{2}} (\ket{0} + \ket{1})$ and $\frac{1}{\sqrt{2}} (\ket{0} - \ket{1})$) and map them to $\ket{0} or \ket{1}$ respectively.  
                - But it's main usage is the opposite direction where it takes $\ket{0}$ to $\ket{+}$ - this is useful for algorithms where starting states all mapped to zero are taken to all possible states with equal probability. (We see that even though + and - have equal output probs, they yield different results)
    - Entanglement and Bell inequalities
        - Describe the two qubit bell state ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/acnq1s6o8Biwmvhr4OfLTtLwlBBusqOH1LAluz-jCuZF_rYQHWibvht0o5AWaV4ZS_qoQIE35Y7vu0dH7u0y0mZoIKGkrdPezMKOuD9lnKuu9a1DsQtHCqo_f3-Qbev4.png) 
            - Entangle two qubits, and if one is measured and results in a 0 then the other will collapse to that same state.
- Lecture 2 - Linear Algebra
    - Linear algebra is→The study of vector spaces and the linear operations on those vector spaces. 
    - Useful properties of complex numbers
        - Conjugate: $z^*=a-ib$ 
        - Modulus: $\sqrt{zz^*}$ 
        - For two complex numbers:
$|z_1 z_2| = |z_1||z_2|$
        - Unit complex numbers lie on the unit circle of the argnad diagram and can be writeen in the form $e^{i\theta}$. Theta is periodic with period $2\pi$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AjtZADBfiDuAB2ACSptid77pZ9fl_rzQS_8PQXHNhtZ4E8wPh8Dk7-vT0tGz2JnWTf96Nz-Mc6u2d4RMJuXcI-6P0QFwWsNP-R7UZy1EceQtDdF1bGVvj8xtUdLtkaMD.png) 
    - Matrics
        - What would the vertically below $a_{12}$ in a matrix be?→$a_{22}$.
X is on the right, Y on the left. Annoying as fuck that it's like that. 
        - When can you do matrix multiplication?→When the width of the first is the same as the height of the second.
Remember, we turn the second on its side & combine.
Remember also - a 2x3 matrix is 3 wide and 2 high...
        - For $A$ being $n\times m$ and $B$ being $m \times l$ we have: 
        - $$c_{ik}=\sum_{j=1}^m A_{ij}B_{jk}$$
This is matrix multiplication, for $i=1, ...,n  \ \ \land \ \ j = 1, ..., l$.  
        - Which of these are true:
Matrix multiplication is associative.
Matrix multiplication is distributive.
Matrix multiplication is commutative→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/59JeIjd43_VE0_WNtQidTu8V8sg1Y8rhJ-QOBnmiL5ymCb7ivnfzg2lkep4wKwY9zB1MoRWfN8bakVFfzd8nuGN2SF8Lxm2sHbvOGD3KwUtCvJ6MAUeYjljPifJ6jkBl.png) 
        - Broadly how do we compute matrix multiplication?→Compute the dot project with row i of the first matrix with column j of the second. This gives the $(i,j)$th element in the resulting matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/aWh6I0lOCgCS7bt2YwdVNhHI3lt233INDGMElHObe0vhb6ySqoKsK5NLX-ZXTOASZfmzMXC0cbLn23gtleulq-dJa70znOIUwTFbaHhJtg0AfjNtsPClmArpP1BBlaRm.png) 
        - How do you compute tensor multiplication?→$$A \otimes B = \begin{bmatrix}a_{11} B \ \ldots \ a_{1m} B \\ 

\vdots \  \ \   \ \  \ddots \ \ \ \   \ \vdots  \\

a_{n1}B \ \ \ldots  \ \ a_{nm} B

\end{bmatrix}$$
I.e.: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qx8rBRhlYSh01nmtAOKBNZowzeUw-0nx0FBeSxI6mjp73obTF9rAhHcQBTi-bAOewUzN92WOm-FjP9bV56dZOiYSYjm07vzj3CmNDhb_PaHW7CgRbwz23QP4oZJOs6bk.png)
        - If A is nxm and B is n'xm'  then $A\otimes B$ is $nn' \times mm'$ 
        - The tensor product is **associative **so $A \otimes (B \otimes C) = (A \otimes B ) \otimes C$ 
        - Additionally:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H9_NrqEWgAWAtQzRcLSQC2ZRaY-oSso0X5XLSW00wGn-G14KXjckaPWz1kR7JSxGWiyNqiNbPB2PNIC9qcuXq3RtQjkkh_ttdt9gJTvngG_bigho4NA54tz8XrzBmkKB.png)
If A is $n \times m$, B is $n' \times m'$ and $x, y$ and $m, m'$ respectively. 
        - How do you transpose a matrix?→Swap it's rows and columns.  
        - What is the adjoint of a matrix? ($A^{\dagger}$)→$A^\dag = (A^*)^T$  
The conjugate transpose.
        - Note: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8xM6TvH_kqRu8IGtTtUgcHhFofbk0oHHLi3vICTuFwavzu3RrCf6r3mkUd1znvaxpj2cRbv9-o2MaDZ4TN-jzyQPh-yToUqr2n2AO11TuJtdOj394Sew9DHLr1hGnBRL.png)
    - Dirac notation
        - A ket is a column vector:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OzvI1m8arvl_tRpMbEBPSTkc14LDl_OYSYK-PC7ayvRAFi5ugzgi-HKypnUU7_AbYsidTDWN19LBTRQWPBa4qccZnop0_NMcODUh5-_S2cXLqaP0MXlyPOsHcFmOUryZ.png)
        - What is the corresponding Ket for a Bra?→It's conjugate transpose:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6_8oZ7_yfm7WApX-mtSjMjOHgO4BLneNvhznGyBUXL5C5cHgc6SkUT6kE_n_EnZqPWax5G6h59mJ2wrYr9D4qSxgfXdE7RBnH2u4hhVIChmXbECOJuAfBiXifWRa5HCN.png) 
        - Note: $$\ket{\psi} \otimes \ket{\phi} = \ket{\psi} \ket{\phi} = \ket{\psi \phi}$$ 
        - Note also that tensor multiplication is associative.
        - A **Hilbert space **is a vector space with {{a defined inner product.}} 
        - Inner Products
            - What is the inner product of two vectors?→$$\braket{u|v} = \braket{u | \times | v} = u^\dag \cdot v$$
I.e. the dot product between a the conjugate transpose of the first vector and the second vector on it's own:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c7ZrR6N4ZnQQi425nPEWpvqm0HNb6-Z2J7DjmMmwAbiECBHzTuRT6xOQVPBGLRK3897ciixeODG9o8wJMgk1RQF7HjYUcgmLuMhPd8ecbWu8ndFzm7x1mtXWqdo-mcsj.png) 
            - Note $\braket{a|b} = \braket{b|a}^*$ 
            - If $\braket{a|b}$ is zero what do we know?→The two vectors are orthogonal 
            - Note: $\braket{a|a} = \sum |a_i|^2$  - i.e. a positive real number.
        - Outer Products and projectors
            - What is the outer product?→We take the second vector to be conjucate transposed rather than the first - e.g. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AR0CqQzE-WJ7fwTkNlMh127OcQ5rMQA5xkHc8EFynsdiCa1Iwz27sxiUxs8D1E6lwlSThF1FFdDP_Dl_l_xCkQCzddPWSQS86N1JAAF4halIJH0R6NXH3bpWqUNxwJP_.png)
Note: This is the same as the tensor product but with a conjugate involved... Fuck me this subject.. 
            - What is a projector?→If $\ket{u}$ is a **unit vector** - then $\ket{u} \bra{u}$ is a projector that projects an arbitrary vector onto the subspace $\ket{u}$
I.e. If you imagine looking down from above a vector, we get the 'horizontal' component with $\ket{u}$ as the basis:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wftcdPlanjCnoWf6DpxPdjYbVF-PfJ3za_CFHQucK4iLMFoXGz1zcLRfAMmejXl2M0iHqkC9vI597023ww7u8Upkzrl8zQ667JMu7odfbF_RoNGTNeSwzSWBJYMGzo0b.png) 
            - Why does this hold and what does this say? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RRaV4cIVpa21u5DFAGNAPi5HXQccgn_Q4q225gXtKJSXNxVYe41hcTCp5DBwJ2HDP5_X_0aQTLsuwyDHhCHPjaiJBQpv9imwmQpeZ6nM3ex4afAiWODR5EGn1DUKU6L0.png) ↓ 
                - This holds because $\braket{u|v}$ is just some complex number, i.e. a scalar value so we can move it to the front. 
Also because the inner product is associative.
                - First we get the inner product, which is a measure of how much two vectors have in common. 
Then we project that amount in common along u.
        - Basis
            - A basis for $\mathbb{C}^n$ is a minimal collection of vectors s.t every vector in  $\mathbb{C}^n$ can be reached via a linear combination of those vectors.
            - Because the collection is minimal, that means that they are all linearly independent.
            - What is an orthonormal basis?→This is where each basis vector is a unit vector **and **all basis vectors are orthogonal. 
            - The computational basis is in general:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H050YCzvQSR5A9zGcweNHKb_DyZCP1xY4S4X1WIQiX9JKHkaJf2u9euus99d-9z1w6spYqiJE2GzoeKSCSIr6XzsOEbBr_GxbUrkN0GTvUWYnHBYhgTz_CZB24V8hPQ9.png) 
            - Describe the correspondence between the computational basis and two-level quantum systems?→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rDagdMm4RcaotAU9VENW2vuD2GUu9PjhaZdpBSbfZTHUhjfCuZkMQfYVqQE5eF8yN7lR1ho9U80K-v6dDBcXiwaphhqzyYx7G5sjUIICN6u-o-2czgK7AFmTNBy0aE7W.png) 
            - 
            - Any vector can be expressed as a double sum over the outer-products of standard basis vectors: $∑ ∑ (a_{ij} \ket{i} \ket{j})$ 
            - The i selects the right column and the j selects the right row.
        - Eigenvectors and eigenvalues
            - What is an eigenvector?→A vector for a given matrix, which when applied to that matrix comes out simply scaled by some λ. E.g. $A \ket{v} = λ \ket{v}$ 
I.e. After we apply the linear transform of the matrix, **that vector stays on the same line it was on beforehand.** 
You can view this as the **axis of rotation **for 3D rotations. 
            - What is an eigenvalue?→Eigenvalues give you the **amount **that eigen __vectors __ get extended when the relevant matrix is applied.
The eigenvalues of a matrix are the roots of the characteristic polynomial: $det(A - λ I) = 0$ Note: This is just a rewrite of the eigenvector equation $A \ket{v} = λ \ket{v}$ ⇒ $A \ket{v} = (\lambda I) \ket{v}$ ⇒ $(A  - \lambda I) \ket{v}=0$ ⇒ $\det(A  - \lambda I)=0$.  
            - Give the intuition for the function $\det(A  - \lambda I)=0$→If $\lambda$ is an eigenvalue, when $A - \lambda I$ is applied to an eigen**vector **that vector **remains in place. **
That means that when the determinant is zero (and thus the matrix squishes space onto a line (for 2D)) that vector will be mapped to zero (in order to stay along it's **own **line). 
            - How do you find eigenvectors?→First compute the eigenvalues. Use $\det(A  - \lambda I )=0$ which will give you a polynomial in $\lambda$. Solve this and sub into:
$(A - \lambda I) \vec{v} = 0$.
Solve for the x, y, z, ... components to get the eigenvectors. 
            - Intuitively, what does it mean for a matrix's determinant to be zero?→It means that the matrix squishes space to a lower dimension. For 2D, that would mean all vectors get mapped onto a line/point. For 3D, a plane/line/point.
            - Each square square matrix has at leach one eigenvalue.
            - The determinant of a matrix **IS THE PRODUCT OF ITS EIGENVALUES**.
            - The trace of a square matrix IS** THE SUM OF ITS LEADING DIAGONAL ELEMENTS** and is ALSO the sum of its eigenvalues (sum not product !)
        - Diagonal representation of matrices
            - What is a diagonal matrix?→Simply, it's a matrix with zeroes everywhere but the top-left to bottom-right diagonal. 
It can be considered to be a **basis consisting of only the eigenvalues.** These are easy to use as we can quickly compute multiple multiplications with these matrices - as each row affects one column in the multiplied matrix. 
            - If a square matrix can be expressed in the form:
$$A = \sum_{i=1}^n \lambda_i \ket{v_i} \bra{v_i}$$
where $\lambda_i$ is the $i$th eigenvalue of $A$
and $v_i$ is the ith eigenvector of $A$. 
Then it is said to be diagonalisable.
            - This is called the eigendecomposition or spectral decomposition of $A$. 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTvQ1kq4We7balM_pHBeXn_VgQVwQK1RqQWJ64HggLNDh2CTPl80vn5nh3W9x3YpwBun6mNi0wzk9nTUAsgm0_-y6icCzXnveP-NB8UF8k7gbCfTG78jyT5bY02xhe-4.png)
Note the empty space means zeroes elsewhere. 
            - When is a matrix normal?→If $A^\dag A = A A^\dag$. This is only the case if it is diagonalisable.
Note also that if $A = A^\dag$ then the matrix is  __Hermitian.__  
            - What is a  __Hermitian__  matrix?→A matrix $A$ where $A = A ^{\dagger}.$  
            - When is a matrix  __unitary__ →If $A^\dag A = A A^\dag = I$ 
All of the eigenvalues of these will have eigenvalue 1.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tFxd3u5495ZPsji_CTvPsMYEw1cdJJmOO5cQH9jRva9gsfep_b39x0QoQ76b8pAcpMZ6_-cuFtybbAnfkwVHOy0t2rhCl6QuuvZQq3snIRPHfIAK1F3HOLRGoNkMVfNc.png) 
    - 
- Lecture 3 - Quantum mechanics
    - Quantum mechanics is a **framework for the development of physical theories.**  
    - Bits are often abstracted away - whether we run a computer using a bunch of taps or a CMOS circuit you get the same result. Quantum computing is more concerned with the  physical reality.
    - The four postulates of quantum mechanics
        1. **State space:** how to describe a quantum state
        2. **Evolution: **how a quantum state is allowed to change with time.
        3. **Measurement: **the effect on a quantum state of **interaction **with a classical system that yields classical information
        4. **Composition: **How to compose multiple quantum systems
    - State space
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MdSqfkVrh_moeZdReil5yjW52SeTgRtPx_j5C4jtDCm1STKX9KZkrdwVPFUEp6lY75w6e88YOmtNJh-ZA2xOB5ds07efRvIwCaqWau_1nANe2QfO0dtlaJwOsm2AcbPS.png) 
        - We consider only qubits, 2 element unit vectors, and their composition. We form a larger state space from $\mathbb{C}^2$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H4-eKbzK1ps7WJKdQhduaV5006XvKHWK1XvMyBhC6fls7kHL3n6EY0et5_Kuht77E-vWoltDFhZ9Kb65P7_dlOKYStDSDh5lnJ5URnAI8t7rZH6rtgk9Hu0Zjj3L6cUk.png) 
    - Evolution
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ooj35ot5RJhtuHHLLUkcSxjBj11dgsmkq59pIp26bW-H112pi4lxL_nKUY8QqVwp_MQdBtwIJhBhtWVNvVxAlIaL_PA-SFkz0bJQh5l3wM8r9tIGMlvoRzFNu-CWlbfY.png) 
        - This describes how the system evolves (when it's closed, no classical intervention).
        - $$ih \frac{d \ket{\phi}}{dt} = H \ket{\phi}$$ 
        - We are interested in discrete time intervals - so we simplify to:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8QCF7FP5XBOZ93WrgqFDEm1dyh5GE6dRELv836gN-xbnBj7KhNF-tRAng1mtYcjWjf48MaIyRuF8inOdJ5-wVMSZ8Esq6v9MSJxe9DNUjTARlHOii8C2KhyG8rTXTxhP.png)
        - What does postulate 2 (regarding evolution) tell us?→Quantum states evolve **by unitary transformations**. $$\ket{\phi_{t_1}} = U\ket{\phi_{t_0}}$$
Where:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YafqEUbsabYVa5cnlUMnuBD_eg9yj_pKCkTamFK_GK4DoCyE_plAkib2vetntU0WKsbNJrbmzdwrLwOQecLaXssr79mScsydZg3WVbA0xdBZDHaS5LPYxEPtigTyMXJK.png)
        - The significance of unitary transformations
            - Unitary operators are the unique linear maps that **preserve the norm**. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tGZCsWU7flckSIp9sFBpHJENPr9j95DJ8agZmCCi8y1mouZ5n7I2kvvIW0bf5xSmriSdX4X5SpfMU6zsAA0mUZ_lX2MVIuKPL1d3DtSUvnwKLYyow91IrlcKeIlzl7OZ.png)
            - This means that unitary operations **map an** **n-qubit state to another n-qubit state. **
Remember: [When is a matrix unitary](../♊ Part II Lecture notes/⚛️ Quantum Computing/Lecture 2 - Linear Algebra/Dirac notation/Diagonal representation of matrices/When is a matrix unitary.md)

            --------------------- Portal ---------------------
                - ♊ Part II Lecture notes
    - The Pauli Matrices
        - These are important one-qubit unitary matrices.
        - The Pauli X matrix is a **not gate **-> 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zhXHHsVhJ5TTGr1jcIydZXoXWipTfqd0v-GrO5SB3CCgebtTnwTnLPNCYmWxZuTbEUiW3pEUEAOBw6YEIYQQB2WgrB0aG6AT-RyzMeU_HvXZw-XLyR2qNnQFLJFh6oLm.png)
        - The Pauli Y matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ji0uQtMs7Or3taYrHm3et6uSJU3HXUfNdK5oCadDYIwY3UtZHdo4kmNaUcF2dVvcIo_vEjYjpyFiXwls409p8P8flK17LrAXarI5SkmZmsO9RuaBX2rHJdE2-ILMZ43E.png)
        - The Pauli Z matrix:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ViulbVdw6-2czf-ftN2XFKO69ZA99bLsfSJJQ3EzmuBHQWsaeIivGIIbBlbPdcJZgEcTTSkV9z06BtKh9IEMMc-Sv2YlzFge36_JL_2ILLeSeNBUZ0cjrYIoCh3aRAwS.png) 
    - The Hadamard matrix
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JGiu0r5eJz57JEp_ZmIUG-eXNNhplYDDQOqh1gP9sHqz6V0-D6WCQEZ_5JsHnUPDqS8SPiR8wt8-1IWowM6D2P6NnMszt28d-kHuFZyz__XzhLersNfTu8djlSsNZM6o.png) 
        - Turns a classical state (0 or 1) into a superposition. These superpositions are different depending on the starting state.
    - Unitaries applied to superpositions of basis states
        - Consider a general one-qubit state,  $$\ket\Psi = a \ket 0 + b \ket 1$$
As the application of unitary matrices is distributed we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OEVSDUuvl_Bhi88rrE7Pkf3vmSNdBDqr-p1Nv6U5C9_uxaGBDeppc6C0ZN31yAOaAwGWAMqPluqoyeHl5g80P3HLs3ncx3mj5YWpny6tflvpcALPULpxrWAMKoFPz70y.png)
We apply to each of the computational basis states in turn. For example:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bzbCuRsRNYPUnNuzjQfY6-0-XiXvqxfi9D-68LPFfoiqoYMPYx6UigcU4GQJPjVxYbG7m0mhQbkrArO_oFR9y-BhGWDaM7sSfr5i9TRNszIGIouhGovgzx7o5On8ZtB4.png)
        - This principle continues to apply to cases of $n>1$.  
    - Measurement
        - We now give the general measurement postulate:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5L4Mq25lmBP_mYc3mwXIhW8KxjBD6jgFPzeC3m82-wm9ceko0IUUxuBi1Tpm70kb2H1mqzxTLXQg1V_Fm_M8Xcers8yaywJISK5vXyQPdJuINPHjKm0JjidH9-RJXdTi.png)
Importantly this is a **non-unitary tranformation.**
        - If the state of the quantum system is $\ket \psi$ before the measurement, the probability of the $m$th outcome is given by:$$\Pr (m) = \bra \psi M^{\dagger}_m M_m \ket \psi$$
The state of the system after the measurement is:
                                   ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_4jRrfGu2AGhhrZzLc7LevR1KuUqug3Jxn1eUW9_DUTVwzGDYNpWvwK9mbe6tzOOQ5ds1pyfruGnjWWDdAgyvKEUqaE5lrE9_2w-jRKPyXkvSpYofPf0SJ-rfW7_yVmu.png) 
I.e. $M_m$ applied to the state, with re-normalisation to ensure it remains a qubit.
        - These probabilities sum to 1, e.g.:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YD9x0xfHdMZNZ2yNeZNmnb084g3c_uy5u5cBjBh-Ysp_TLifIqAECYPeqWj_czYmrfiG5APMeQq8GgPzgd8j9YIsItCff_TEbicY1SSKHKPImplPzi1H0Yke5uC5zvVD.png)
This is only the case iff:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/L8L7Aow0drffjIWEOakkQFqm9pWfoBp53to1kOd0T0UJ33BLA_bcTajwNzltLhynsW4jrZpgqBcy-zcvSb87qeDkMcfPdv2ll7_ks-BMS2CXDwjy_FAj5Ukz7tI9RSjc.png)
Because m only applies to the central part of the braket:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Jr3ZQ-Uw55MnKoTHkJ5f-eKriCRTGUDWW162StV2U5SPAA5mSDpeP_1hZXxl3MpP0WAcC0zvuLessQG9rU84EQ61cCA3SeuX_OWuC7Mrp0b8z04QoEq5_Ue0cbzRfr8q.png) 
        - Measurement in the computational basis
            - We usually implicitly mean single qubit measurements in the computational basis when we say measurements. 
            - What are these?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wk-ymJxW7FBGgt2s-21yEhtZrXzMSGk0S8YmZAoBKjTFy_qPpMuhsAxARVFhdleVw3PFp2_LlmxoQYPdCdtn0B8Zikjeja2fuTnXF3MziOcvmPZSRJnUmAgQ8Us19Fd4.png)→These are our measurement operators, the first is for the 0 outcome and the second is for the one outcome.  
Note that $\ket 0 \bra 0$ is just the same as: $\begin{bmatrix} 1\\ 0\end{bmatrix} [1 \  0]$ 
These operators are used to project onto $\ket 0$ and $\ket 1$- they are known as projective measurement.

            - What is the Born rule?→For $$\ket \psi = \alpha \ket 0 + \beta \ket 1$$The probabilities of the measurement OUTCOMES $M_0$ and $M_1$ are:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/rxvUP44M3sfH70PMp1zSXSpTrqADtfveUSaoE2Cm7XfxNnS9ITtnkCq3Dm9HZal9dAORTVklY7rlL7XVpcEU8VvJ_U_Xv4ElAu0F8e2TQFWrRC2gHB2xpNohSmxTteSp.png)

            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9BERKbCIiZCFssnLSThsewc_h1qiu8apv-HcnJXARl4CrPzbXW5F8z6S4336T_MRISP3CSwu3Ig4XwZ1fggYCpE5wWfXfH6PNttJdjlWvODR-9qjKj8JBOcVB7WbZGAk.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ErU5MeBHzhgnQI_C49-FpIBCkPFEMNfXmSCV26ZWo4YTy47Rkq7qEgfaAy4-UkZGacgrQRquse6F3Pom5qEdHrWSMUywDRniN8UedKib7jAIFnbUn2q5CJuNqztaJJ3X.png) 
    - Global and relative phase
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zc-1ynqUl_msOxDownFy6UXcjwkalllCdtZYGhQo_sNxOOszv2TecfxuFLKp6PyMEZNLyLvBNZF7zFBkEKQoqxxHzvqp7YC8A_uGKGrZwAoP68cf0siFmYkysQPf6YUl.png) 
        - What is the global phase?→If we write a one-qubit state as $$\ket \psi = e^{i\theta} ( \alpha \ket 0 + \beta e^{i \phi} \ket 1 ) \equiv e^{i \theta} \ket {\psi '}$$
$\theta$ is called the **global phase **and has **no observable consequences**. Whenever we measure we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D4Rtbe1ajd1HOAubLK2ojxTcWkyl8Rzp4FbTVpoovmkrJ6zTRILkVWSW5A4R1FANl0B4CApN2n4mu_pB1Sm3f-9s08GVCLt0iSpNT-tMLQhaq_giyEkyfFmUrtFeKm7l.png)
So we neglect global phase. So we can treat $\alpha$ as **always being a positive ** __**real number. **__ If it wasn't, we could just pull it out.
The same cannot be said for the relative phase $\phi$, consider that the difference between $\ket +$ and $\ket -$ depends on this relative phase. 
    - Composition
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/B1PcYKrFGCJgKrNMXdEbM6tlzcemccjtr2YNdvEa6lujG9Iw_lNglc1sKQcPe2dH2-DwFSzquQrEtR2vKcJlbc5PxQNZVRD-qJGabpYG2N8x6-yKQS2-Q5VdFOUyMmQ4.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V7s_iKu42pQ93XL0FWQfGNjyBh4_vl-vbnj5Wj-XixMvk5C90dsM9lEaxXTk-QEHwsGXr7dnD2VhkJcbUzougLrOA97Z5yPDCx8DUB1jYtF1ByU_jMDd2r3bCMZlvS1_.png) 
- 
- . If there's currently any text highlighted, then that will be added to the search bar.  Triggered by the forward. If there's currently any text highlighted, then that will be added to the search bar.  Triggered by the forward
