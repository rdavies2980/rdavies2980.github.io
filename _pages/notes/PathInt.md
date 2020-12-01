---
title: Introduction to Path Integrals
mathjax: true
permalink: "/PathInt/"
classes: single
excerpt: "An intuitive, appealing alternative construction of Quantum Mechanics and Field Theory"
author_profile: false
header:
  overlay_image: "../images/PathInt/SLITS%3F.png"
  overlay_filter: "rgba(150,220,140,0.9)"
  actions:
  - label: "Download PDF Version"
    url: "../assets/notes/Path_Integral_Introduction.pdf"

read_time: true
---

<aside class="sidebar__right sticky">
<nav class="toc" markdown="1">
<header><h4 class="nav__title" style="background:rgb(150,220,140)"><i class="fas fa-list"></i>
Contents</h4></header>
*  Auto generated table of contents
{:toc .toc__menu}
</nav>
</aside>

The path integral formulation of quantum mechanics compliments and contrasts with the second quantised operator construction. These two formalisms offer different ways, each with their own advantages and disadvantages, to approach the intimidating topic of QFT. Reformulating the ideas of Quantum in this formalism offers another way to interpret quantum mechanics with the 'sum over histories' idea. The main reasons why the path integrals still being used is that the classical limit is much easier to obtain, it has a clear connection to classical statistical mechanics and that it naturally lends itself to infinite order perturbation summations (non-perturbative problems). These three reasons make it clear why its use in condensed matter is such a natural fit.

These notes will show what this path integral is and how to use the formalism to extract the wanted information. This assume knowledge of second quantised operators and quantum mechanics but not in calculating Feynman diagrams and the more sophisticated techniques. We will first look into the idea of the path integral and how this is applied to quantum mechanics with the explicit form being derived. The techniques of Gaussian integration will then be looked at, giving all the information needed to start using path integrals in QM. Finally, it will conclude with the much harder field integrals that are the foundations of Quantum Field Theory.

## Quantum Mechanical Paths - Sum Over Histories

To start to understand what is happening in a path integral, it is best to start at the beginning of many a quantum mechanics course - Young's double slit experiment. The diffraction that is unique to wavelike behaviour is described by summing the amplitudes at a point $$O$$ that come from each slit, $$A(0) = \sum_i A(i \rightarrow0)$$ , as shown in the figure below[^1].

<figure class="align-center">
<img src="../images/PathInt/2slits.png" style="width: 70%" class="align-center">
</figure>

where the intensity at any point is the square of the amplitude. This is in contrast to particle-like behaviour where the total intensity is the sum of the individual intensities. However, in one lesson, many years ago (as the apocryphal story goes), a young Feynman asked what would happen if there were more holes and gratings[^1].

<figure class="align-center">
<img src="../images/PathInt/moreslits.png" style="width: 70%" class="align-center">
</figure>

The total amplitude would then become a more complicated sum, having to take into account more slits, $$A(O) = \sum_iB(i\rightarrow0) \sum_jA(j\rightarrow i)$$. Taking this idea to its conclusion, if there were an infinite number of slits then there would be an infinite number of amplitudes to sum over. An infinite number of gratings would mean that the the 'paths' that the particle takes is now a continuous function (imagine spacing between gratings and spacing are two independent coordinates that both shrink to an infinitessimal). This resultsin the total amplitude is summed over all possible paths from the source to the point $$O$$[^1].

<figure class="align-center">
<img src="../images/PathInt/SLITS%3F.png" style="width: 70%" class="align-center">
</figure>

The final part is that infinitely many slits means that there is no grating! So somehow calculating the amplitude at a single point takes into account all the possible histories of that particle at once and this is the heart of the path integral.

At this point, nothing has been said about quantum mechanics and all these paths that we were considering were 'classical' - so how can the two be mixed? Noticing the similarities in the structure of this set up (fixed start and end points), we invoke the concept of action. The classical path corresponds to a minimisation of this functional so we can try weighting each possible path by a phase related to the action. We will derive it explicitly in the next section but first let us examine the repercussions of weighting each path by $$\exp(iS[x(t)]/\hbar)$$.

Expanding the functional around the minimum, we end up with an expression,

\begin{equation}
    S[x(t)] \approx S[x_0(t)] + \frac{1}{2}\int\int dx dx' \frac{\delta S[x_0(t)]}{\delta x(t) \delta x(t')} u(t)u(t')
\end{equation}

where $$u(t)$$ is the deviation of the path from the minimum. Performing the sum over the minimum will kill off all the higher terms and leave us just with an $$\exp(iS[X_0(t)]/\hbar)$$ term and then all of the path dependent sums to do. In these terms if we consider two terms that are close together but both deviations from the minimum path and then take the limit that $$\hbar\rightarrow 0$$, then these two infinitessimally close paths with have drastically different phase. This leads to cancellations of all the higher order terms and only our minimum path contributing, which is just classical mechanics!

This is what makes semiclassics 'easy' to extract in this formalism, that the paths that contribute the most are the paths that are within $$\hbar$$ of the action. Above this, the differing paths will interfere and destroy each other. The way how the correspondence principle is clear in this picture is one of the appealing aspects of path integrals.

### Deriving the Integral

Considering the question we are asking is what is the wavefunction at a certain time and place, we use the QM time evolution operator to go from a state $$ \vert q_i \rangle $$ to a state $$ \vert q_f \rangle $$. The matrix element will give the probability of this occurring so we are attempting to find the matrix element

\begin{equation}
    \langle q_f|U(t)|q_i(t=0)\rangle = \langle q_f| \exp(-iHt/\hbar) |q_i \rangle = \langle q_f| \exp(-iH\delta t/\hbar) \cdots \exp(-iH\delta t/\hbar)  |q_i\rangle
\end{equation}

To tackle this integral the operator is split up into $$N$$ time chunks, a process known aptly as time slicing. Letting $$t = N\Delta t$$, with $$\Delta t = t_2 - t_1$$, where this gives us a parameter that is small (compared to the eigenvalues of the operator).

Assuming that the Hamiltonian is of the form: $$H=P^2/2m + V(x)$$, and using the BCH relation $$e^Ae^B = e^{A+B}e^{O([A,B])}$$, we can split up the exponential of the Hamiltonian in the following way:

\begin{equation}
    e^{-i\Delta t H/\hbar} \approx e^{-i T\Delta t / \hbar}e^{-iV\Delta t/\hbar}
\end{equation}

as the commutators in the BCH relation will contain higher powers of $$\Delta t$$. So denoting the states at each of the time evolution as $$ \{ \vert q_i\rangle\}$$ with $$\vert q_0\rangle$$ being the initial state.

$$\begin{align}
    P &= \langle q_N e^{-i T\Delta t \hbar}e^{-iV\Delta t/\hbar} \cdots e^{-i T\Delta t / \hbar} |q_0\rangle e^{-iV(q_0)\Delta t/\hbar} \nonumber \\
    &= \int dp_0 \langle q_N| e^{-i T\Delta t \hbar}e^{-iV\Delta t/\hbar} \cdots e^{-i T\Delta t  \hbar}|p_0\rangle\langle p_0|q_0\rangle e^{-iV(q_0)\Delta t/\hbar} \nonumber \\
    & = \int dp_0  \langle q_N| e^{-i T\Delta t \hbar}e^{-iV\Delta t/\hbar} \cdots  |p_0\rangle e^{-i T(p_0) \Delta t / \hbar}e^{ip_0q_0/\hbar}e^{-iV(q_0)\Delta t/\hbar} \nonumber  \\
    & = \int dp_0 \int \frac{dq_1}{2\pi} \langle q_N| e^{-i T\Delta t \hbar}e^{-iV\Delta t/\hbar} \cdots  |q_1\rangle e^{-ip_0q_1/\hbar}e^{ip_0q_0/\hbar}e^{-i T(p_0) \Delta t / \hbar -iV(q_0)\Delta t/\hbar} \nonumber
\end{align}
$$

Continuing on in this fashion we end up with the result

\begin{equation}
    P = \int \prod_{n=1}^{N-1} \frac{dq_n}{2\pi} \prod_{n=0}^N dp_n \exp( -\frac{i\Delta t}{\hbar} \sum_{n=0}^{N-1} V(q_n) + T(p_n) - p_{n}\frac{q_{n+1} - q_n}{\Delta t})
\end{equation}


This integral is a $$(2N-1)$$ dimensional integral over position and momentum at each of these time slices. In taking the limit that $$N \rightarrow \infty$$ and $$\Delta t \rightarrow0$$ such that $$t$$ is finite, these integrals become infinite dimensional - called functional integrals. Explicitly, the measure on these integrals are:

\begin{equation}
    \lim_{N \rightarrow \infty} \int \prod_{n=1}^{N-1}dq_n \prod_{n=1}^{N} dp_n/2\pi \equiv \int_{q(0) = q_0}^{q(t) = q_n} \mathcal{D}p\mathcal{D}q
\end{equation}

 This finally can be turned into the Hamiltonian formalism of the path integral, or if the potential is assumed to be only in terms of position then the functional integration can be done (which we will see in the next chapter) to integrate out $$p$$. This gives two (normally) equivalent representations of the path integral where the transition probability between states has been expressed as an infinite dimensional integral over coordinate or phase space.

 \begin{equation}
     P = \int \mathcal{D}p\mathcal{D}x \exp(\frac{i}{\hbar} \int_0^t p\dot{q} - \mathcal{H}(x,p)dt) = \int \mathcal{D}x \exp(\frac{i}{\hbar} \int_0^t\mathcal{L}(x,\dot{x})dt)  
 \end{equation}

Notice here that simply performing the integral will give us propagator, which will not be the case when we move onto the field integrals.

## Gaussian Integration

So having seen this process it is obvious that we must deal with these new \textit{funky} integrals but how can we calculate these infinite dimensional integrals? The Gaussian integral turns out to be key so by generalising the usual form we can find out how these new integrals can be evaluated. Starting with a more generic form of the Gaussian Integral (with a linear term that can be solved by completing the square) for both real and complex integration.

\begin{equation}
    \int_{-\infty}^{\infty} dx e^{-ax^2/2 + bx } = \sqrt{\frac{2\pi}{a}}e^{b^2/2a}, \quad  \quad   \int_{-\infty}^{\infty} d\bar{z}dz e^{-\bar{z}\omega z + \bar{u}z + \bar{z}v } = \frac{\pi}{\omega} e^{\bar{u}v/\omega},
\end{equation}

where the constant related to the quadratic term has the correct sign to ensure convergence of the integrals. These can be quite easily generalised to an $$N$$ dimensional integration as this just amounts to evaluating $$N$$ of the above integrals.

\begin{equation}
    I = \int_{-\infty}^{\infty} d\boldsymbol{v} e^{-\boldsymbol{v}^T A \boldsymbol{v}/2 + \boldsymbol{j}^T \cdot \boldsymbol{v} } = (2\pi)^{N/2} (\det A)^{-1/2} e^{\boldsymbol{j}^T A^{-1} \boldsymbol{j}/2}
\end{equation}

where the matrix $$A$$ must be positive definite real symmetric matrix. The least obvious step in this is the appearance of the determinant which is from diagonalising the matrix to perform the $$N$$ individual Gaussian integrations. It comes from that the product of the eigenvalues is the determinant and this is unchanged by diagonalisation. The most important property is that this integral serves as a generator for other identities - importantly the weighted average of specific components of **v**.

So differentiating the above equation by $$j_m$$ and $$j_n$$ and then setting the whole $$j$$ vector to zero gives:

\begin{equation}
    \int_{-\infty}^{\infty} d\boldsymbol{v} e^{-\boldsymbol{v}^T A \boldsymbol{v}/2} v_m v_n =  (2\pi)^{N/2} (\det A)^{-1/2} A^{-1}_{mn}
\end{equation}

which through defining the average of as:

\begin{equation}
    \langle \cdots \rangle =  (2\pi)^{-N/2} (\det A)^{1/2} \int_{-\infty}^{\infty} d\boldsymbol{v} (\cdots) e^{-\boldsymbol{v}^T A \boldsymbol{v}/2}
\end{equation}

then we can formulate the result as $$\langle v_nv_m \rangle = A^{-1}_{nm}$$. From defining the average in this way, Wick's theorem just pops out from differentiating the generating expression further and further. Finally we can take the limit that $$N\rightarrow\infty$$, and due to the definition of the average we will end up with a finite result because of the coefficient that becomes infinite (the $$(2\pi)^N$$ term), gets cancelled out. So finally we express a functional integral:

$$\begin{align}
    \int \mathcal{D}v(x) \exp\Big(-\frac{1}{2}\int dxdx'v(x)A(x,x')v(x') + \int dx j(x)v(x) \Big) \\
    \quad \propto (\det A)^{-1/2} \exp( \frac{1}{2} \int dxdx' j(x)A^{-1}(x,x')j(x'))
\end{align}
$$

where $$A^{-1}$$ must now satisfy:

\begin{equation}
    \int dx' A(x,x')A^{-1}(x',x'') = \delta(x-x'')
\end{equation}

making it the Green's function of the operator kernal (or propogator). This means that the weighted averages are now equal to the Green's functions and this is a crucial link that will turn out to be useful and is the connective tissue between the two formalisms. In the usual second quantised formalism Green's functions are reduced into a simple form by Wick's theorem, but here it is by reducing complicated actions to averages of quadratic actions through some expansion.

### Partition Functions as Functional Integrals

Having obtained the path integral, why is it a good formalism? The main answer to that lies when we recast the formalism to become field integrals but there are still useful things that can be found from this. The connection to classical can be seen with a bit of generalising of the partition function. Normally the partition function involves a sum of $$e^{-\beta V}$$ over all possible states of the system, where $$V$$ is the suitable energy functional. Supposing that the energy functional is an integral over space (for example a string in a potential), and that there are an infinite number of possibilities the system can be in. If the string is length $$L$$ in the $$x$$ direction and the potential is in the $$u$$ direction we can find the partition function as:

\begin{equation}
    \mathcal{Z} = \int \mathcal{D}u \exp(-\beta \int_0^L dx(\sigma(\partial_xu)^2 + V(u)) ) = \int dq \langle q| e^{-it H/\hbar}|q\rangle
\end{equation}

where the final equality is from letting $$\hbar = 1/\beta$$ and $$t = -iL$$ and allows us to express the partition function of a classical system with a quantum mechanical amplitude. This will turn out to be usefl when considering actual systems, allowing the existance of imaginary time allows us to consider statistical effects. The link between $$d$$ dimensional quantum mechanics and $$d+1$$ dimensional statistical mechanics, is true in general. The strength of fluctuations is given by $$\hbar$$ and $$\beta$$ and the 'extra' dimension is absorbed into the time.

This however is even useful for quantum mechanics of a single particle, where the partition function is the trace over the exponential of the Hamiltonian as an operator. From the connection, this can be reformulated as a trace over the transition amplitude evaluated at an imaginary time. So the real time dynamics and statistical ascepts can both be formulated from the same thing, providing that imaginary time is allowed.

## Field Integrals

Our task is to now extend the idea of a path integral to quantum field theory. In a quantum mechanical sense, we elevated a single point particle to an integral over all time-dependent configurations. In field theory, the demotion of position from a dynamical variable to a label means the degrees of freedom are already continuous. A path integral over this will be integration over a single copy of these variables at each instant of time. We are integrating over surfaces that are mappings from space-time to the field manifold [^2].

<figure class="align-center">
<img src="../images/PathInt/FieldIntegral.png" style="width: 70%" class="align-center">
<figcaption>A table to illustrate the difference between the number of degrees of freedom in quantum mechanics and quantum fiel theory.</figcaption>
</figure>

This means dealing with even more infinities so only the averages will be well defined so we should start from the generating functional picture. Essentially we are splitting up the Hamiltonian into discrete time slices and absorbing the quantum dynamical phase into eigenstates. In the quantum mechanics version, the Hamiltonian structure suggests that momentum and coordinate representation should be used. However in the second quantised picture uses creation/annihilation operators, so is it possible to use this as a basis?

It is possible and the way to do it is by using coherent states. These are defined as being eigenstates of the annihilation operator:

\begin{equation}
    a_i | \phi \rangle = \phi_i |\phi\rangle, \quad \quad |\phi\rangle = \exp( \sum_i \phi_i a^{\dagger} ) |0\rangle
\end{equation}

It is clear that the eigenstate must be an infinite sum of all the various energy states so annihilating a state has no effect in total. Also it should be noted that these are not Hermitian operators and these are acting in Fock space, with there being no eigenket of the creation operator. There, however, is an eigenbra of the creation operator but no eigenbra of the annihilation one. Interestingly these correspond to the most 'classical' states as removing a single particle has no effect on the system.

These have funky properties but the reason that we want to use these as our implicit basis when we use the path integral is that it makes identifying the Largrangian from the microscopic Hamiltonian a lot easier. In condensed matter, we normally start from a microscopic Hamiltonian and so this is super useful. In contrast, particle physics normally starts from the Lagrangian (more "fundamental" and all that), so this issue is not really brought up.

To be explicit, what these states do is diagonalise the annihilation operators allowing us to express the fields as complex numbers (the eigenvalues) meaning our final path integral can do away with any awkward operators and simply deal with complex numbers. Therefore if we have a microscopic Hamiltonian (that is normal-ordered)

\begin{equation}
    H = \int dx \mathcal{H}(a^{\dagger}, a)
\end{equation}

we can replace if with the fields that are just complex numbers and no longer have to keep track of the order!

\begin{equation}
    L = \int dx \mathcal{L}(\bar{\psi}, \psi), \quad \quad \mathcal{L} = \bar{\psi} \partial_{t} \psi - \mathcal{H}(\bar{\psi},\psi)
\label{NewLag}
\end{equation}


### Over-complete Basis

Crucial to using this is that we use an over-complete basis which allows us to transform from countably infinite states into a true continuum. To see this point, consider the resolution of identity for a system with spin $$S$$:

\begin{equation}
    I = \sum_{-S}^{S} |S_z\rangle\langle S_z|
\end{equation}

we now want to consider the spin coherent state $$\vert \Omega\rangle$$ which is a state obtained by rotating the fully polarised state by an angle $$\theta$$ around the $$x$$ axis and an angle $$\phi$$ around the $$z$$ axis. This state is no longer an eigenfunction of the spin operator, instead it more obviously has a classical interpretation as a spin point in a certain direction! This state can then be used as our basis. This, however, is only okay to do if we are in the large spin limit due to a lack of kinetic energy term damping the change in our states (so derivatives are v dodgy when we calculate a path integral for spin).  

So returning to our coherent states as the eigenfunctions of the annihilation operator, we end up with a new resolution of identity:

\begin{equation}
    I_F = \int \prod_i \frac{d\bar{\phi}_id\phi_i}{\pi} e^{-\sum_i \bar{\phi}_i\phi_i} |\phi\rangle\langle\phi|
\end{equation}

with this now showing how these states are not pairwise orthogonal and the weighting that appears in this resolution compensating for this over-counting. In the coherent basis, the overlap between two states is given by $$\langle\phi \vert \theta\rangle = \exp(\sum \phi^*_i\theta_i)$$. The way to show that this is that it this operator must commute with all operators in the Fock space (which can be represented through creation/annihilation operators).

### Fermionic Fields

We can now introduce the proper field integral where we are performing a similar calulation to the one done before, but now in this new coherent basis. The same steps are followed, $$\langle\theta_N\vert\exp(-it/\hbar :H:) \vert \theta_0\rangle$$ is evaluated by time slicing and using the resolution of identity when needed. Doing this results in the same result as it did before but now with the Hamiltonian given by our microscopic Hamiltonian where the normal ordered operators are replaced by fields (with these fields being defined for an over-complete basis). Therefore thats all the problem solved right? Finding correlators is as easy as using this path integral as a generating function and then that is all physics solved - it is just a question of how to evaluate the correlators through expansions.

There is one small snag which is that we have not yet dealt with fermions. The problem with doing away with all the operators and their commutation relations is that it now becomes possible to lose the fact that fermions will Pauli exclude each other. The way to deal with this is introduce Grassmann variables. Starting in a similar way to the bosonic analysis, we define states that for all $$i$$ must satisfy

\begin{equation}
    a_i |\eta\rangle = \eta_i \\eta\rangle, \quad \quad \eta_i\eta_j \ne \eta_j\eta_i
\end{equation}

where the second equality is required due to the anti-commutivity of the fermionic operators. This property cannot be ordinary numbers, but must form an alegbra like they do - Grassmann alrgebras! Now all the usual non-arithmetic stuff (differentiation, integration etc) must be figured out for these new objects. The basic properties are defined as:

\begin{equation}
    \partial_{\eta_i}\eta_j = \delta_{ij}, \quad \int d\eta_i = 0, \quad \int d\eta_i \eta_i = 1
\end{equation}

A bizarre thing about this is that defined like this, integration and differentiation become the same? A lovely feature is that the most generic states can be written as $$\vert \eta\rangle = \vert 0\rangle + \eta\vert1\rangle$$ as the repetition of the same $$\eta$$ will result in zero. This allows us to exponentiate things that do not look like an infinite sum, and we can make everything look like the bosonic case. One of the benefits of Grassmann fields is that the Taylor expansion will always contain finitely many terms and integrals will always converge! Therefore fermionic coherent states are:

\begin{equation}
    |\eta\rangle = \exp( - \sum_i \eta_i a^{\dagger}_i) |0\rangle
\end{equation}

The biggest difference between the two cases is that the Gaussian integral no longer give the inverse of the determinant, but the determinant itself. So in the $$N$$ dimensional case, where $$\phi$$ are $$N$$ component vectors of Grassmann variables.

\begin{equation}
    \int d(\bar{\phi},\phi) \exp(-\bar{\phi} \boldsymbol{A}\phi ) = \det{ \boldsymbol{A}}
\end{equation}


Therefore the fermionic/bosonic formulation is the same, but the result of the integration differs by an inverse and what the fields are actually over. This should be all the required information needed to be able to dive into the more specific literature. Instantons can now be analysed with the QM version of the path integral and basic semiclassical analysis can be done by performing the functional integral on the quadratic terms. The field theoretic problems require a little more subtle analysis, especially the inclusion of temperature requiring matsubara frequencies. This however should suffice as quick introduction to the ideas.

## Further Reading

Most of this introduction was based off the bible that is Altland and Simons, Chapter 3 and 4 especially. Shankar's Condensed Matter and QFT book is also useful with a clear section on over-complete basis (the first 6 Chapters or so). Both of these books provide examples and problems that are at this level. QFT for gifted amateurs as always gives a very readable version of the ideas, but it comes after a lot of the work on Green's functions so some of it is at a weird level.

Most of this is focused on Condensed matter ideas but there are a wealth of QFT books where this process is well explained. Zee, Peskin and Schroeder and Feynman's own book on the topic are all good resources.

[^1]: Quantum Field Theory in a Nutshell, Zee
[^2]: Condensed Matter Field Theory, Altland & Simons  