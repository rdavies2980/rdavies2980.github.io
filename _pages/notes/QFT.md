---
title: Quantum Field Theory
mathjax: true
permalink: "/QFT/"
classes: single
excerpt: "Calculating correlators - or what you can ask from a theory."
author_profile: false
header:
  overlay_image: "../images/QFT/FiniteTContour.png"
  overlay_filter: "rgba(228,157,249,0.9)"
  actions:
  - label: "Full Thesis"
    url: "../assets/RoseDaviesFinalThesis.pdf"

read_time: true
---

<aside class="sidebar__right sticky">
<nav class="toc" markdown="1">
<header><h4 class="nav__title" style="background:rgb(228,157,249)"><i class="fas fa-list"></i>
Contents</h4></header>
*  Auto generated table of contents
{:toc .toc__menu}
</nav>
</aside>

<i>This page is adapted from chapter 2 of my thesis. The point is to introduce the foundations of quantum mechanics and how quantities would be calculated. The idea of ordering on a contour is introduced with the rules of zero-temperature and finite temperature equilibrium QFT shown to come from this contour ordering. Although no explicit calculations are presented, this is meant to be a way to understand the reasoning behind why the objects are required - therefore this should be read after you have come across quantum field theory for the first time! </i>


Introducing the ideas of quantum field theory in a way that is self-contained is a challenging task: the multiplicity of the subject spills from the seams. For every class of models that can be solved, there are substantially more models that require radically different techniques to extract any information. Condensed matter contains this same multiplicity, with microscopic and phenomenological models inextricably tied together to both provide insight. Through all of these theories, there is a thread that ties them together - a Hamiltonian acting on a Hilbert space of states. High-energy physics does not often concern itself with finding eigenstates but they are still hidden beneath their fundamental Lagrangian approach. This diversity of approaches is precisely why an introduction is so difficult!

Observables are obtained through taking appropriately defined averages of operators and these observables encompass all the information that can be extracted from the theory. Obtaining a complete understanding of the states and averages - and how they evolve in time - is the goal of studying a model. Often this is only possible, however, where the model is so simplistic that it describes nothing! Therefore the techniques developed must be flexible enough to allow information to be extracted, even if a full description of the states is not available.

Here the understanding of how these observables can be calculated will be developed, culminating in the contour-ordered Green's function. Familiarity with second quantised operators and their commutators will be assumed. For the start, zero temperature QFT will be considered, where the average of an operator is given by the trace over the normalised eigenstates $$\vert n\rangle$$ of the underlying Hamiltonian,

$$
    \langle \hat{O}\rangle = \sum_n \langle n\vert \hat{O}\vert n\rangle
$$

The trace of an operator is independent of basis, so any suitable orthonormal set of states can be chosen. This schematic way of showing the average overlooks a crucial point - that the eigenstates and operators can have time dependence, resulting in a time-dependent observable. There are three common ways of including this dependence into quantum mechanics, which will be introduced in the next section.

## Pictures of Quantum Mechanics

Offloading all of the time dependence onto the states, $$\vert\psi(t)\rangle_S$$, is known as the Schrodinger picture. The dynamics of the system are governed by the Schrodinger equation, where $$\hbar = 1$$, in which application of a time-independent Hamiltonian evolves the states in time,

$$
    i\partial_t\vert\psi(t)\rangle_S = \hat{H}\vert\psi(t)\rangle_S.
    \label{eq:2:SchrodingerEq}
$$

Any quantum state can be expressed in the basis of the eigenvectors of the Hamiltonian, which are stationary states and only change by a phase. This disentangles the matrix aspect of the above equation into multiple independent problems. The formal solution is the time evolution operator $$\hat{U}$$ which connects states at different times,

$$
    \vert\psi(t)\rangle_S = \hat{U}(t,t_r)\vert\psi(t_r)\rangle, \quad \quad \hat{U}(t,t_r) \equiv \exp{-i\hat{H}(t-t_r)}.
$$

The $$S$$ subscript is dropped for $$\vert\psi(t_r)\rangle$$ because this is a state at a given reference time $$t_r$$. The operator has the property that any evolution in time can be split up into successive evolutions, $$\hat{U}(t_1,t_2)\hat{U}(t_2,t_3) = \hat{U}(t_1,t_3)$$. Its conjugate evolves bra states $$\langle\psi(t)\vert  = \langle\psi(t')\vert \hat{U}^{\dagger}(t,t')$$ in a similar way. Requiring that the states are normalised at all points in time means that the evolution must be unitary, and that the conjugate is the inverse of the evolution, $$\hat{U}^{\dagger}(t,t') = \hat{U}^{-1}(t,t') = \hat{U}(t',t)$$,

There is no inherent reason to consider states as the objects that evolve in time. An alternative picture emerges when considering matrix overlaps,

$$
   \langle \psi(t)\vert  \hat{O} \vert \psi(t)\rangle_S   = \langle \psi(t_r)\vert \hat{U}^{\dagger}(t, t_r) \hat{O} \hat{U}(t,t_r)\vert \psi(t_r)\rangle \equiv \langle \psi(t_r)\vert \hat{O}_H(t)\vert \psi(t_r)\rangle
$$

where the time dependence can be shifted onto the operators rather than the states. This defines operators for the Heisenberg picture, $$\hat{O}_H(t)$$, that time evolve the state from the reference time, act with the Schrodinger operator at time $$t$$, then evolve back. The dynamics of the operator are described by the Heisenberg equation of motion,

$$
    \frac{d\hat{O}(t)}{dt} =  -i [ \hat{O}, \hat{H}(t)].
$$

Although this seems like a redundant change of emphasis, the apparatus of many-particle quantum mechanics is built from time-dependent creation and annihilation operators. These operators encode the statistics of the system much more naturally than explicitly considering the (anti)symmetrised state space for the Hilbert space of every particle number. 

The time evolution operator can be generalised for a time-dependent Hamiltonian,

$$
    \hat{U}(t,t_r) = \mathcal{T}\exp( -i \int_{t_r}^t d\tau \hat{H}(\tau) ),
    \label{eq:2:TimeDependentU}
$$

where $$\mathcal{T}$$ is the time ordering operator. It denotes that the string of operators within are ordered to have them act by whichever operator is earliest in time, the earliest put to the right. This can be explicitly formulated by using Heaviside functions $$\Theta(x)$$,

$$
  \mathcal{T}\{\hat{A}(t_1)\hat{B}(t_2)\} = \theta(t_1 -t_2) \hat{A}(t_1)\hat{B}(t_2) \pm \theta(t_2-t_1)\hat{B}(t_2)\hat{A}(t_1),
$$

where the $$\pm$$ refers to the sign produced by the commutation relations of bosonic or fermionic operators.

Generalising this ordering to a string of $$n$$ operators requires each of the $$n!$$ possible combinations of times to be enforced by increasingly intricate Heaviside functions. The derivation of the time evolution operator can be seen <a href="{% post_url 2023-05-23-TimeEvolution %}">here</a>. The conjugate of $$U(t,t_r)$$ will be anti-time ordered, where the latest time operators act first by putting them at the right of the operator string. This is the first encounter with the time ordering operator which arises naturally from solving the Schrodinger equation for a time-dependent Hamiltonian. This ordering of operators turns out to be at the heart of QFT and the concept will be contorted into even more bizarre forms throughout this section. 

There are two hurdles with calculating using this machinery built so far; the first is that to calculate anything, the full eigenstates are needed. This is not a simple task, even for a time-independent Hamiltonian. The second issue is that the average of multiple operators acting at different times will be described by a string of time evolution operators with different ordering rules. The aim is to find an ordering rule which applies to the whole expression, regardless of how many operators there are. The process of trying to accommodate for these two things will guide the following section.

### Interaction Picture

When the eigenstates are not fully known, the interaction picture is the most convenient way to include the time dependence[^1]. It is a halfway house between the previous two pictures, where the operators and states both evolve in time. This complexity appears to have neither benefit of the other pictures, but is crucial to building a robust theory.

The Hamiltonian is split up into two parts, one part for which the eigenstates are known and a second interacting part that depends on time, $$\hat{H} = \hat{H}_0 + \hat{V}(t)$$. This is the situation throughout physics where we often have an idea of what the rudimentary description should be, with complications being additionally included. This splitting of the Hamiltonian parameterises our ignorance of the full eigenstates into $$\hat{V}(t)$$.

Mathematically, the idea is to overcompensate in the time evolution of states by the time evolution that is known. So defining

$$
\vert \psi(t)\rangle_I = e^{i\hat{H}_0(t-t_r)}\vert \psi(t)\rangle_S,
$$

and putting this into the Schrodinger equation results in,

$$
 i\partial_t\vert \psi(t)\rangle_I = e^{i\hat{H}_0(t-t_r)}\hat{V}e^{-i\hat{H}_0(t-t_r)}\vert \psi(t)\rangle_I \equiv \hat{V}_I(t)\vert \psi(t)\rangle_I.
$$

This gives a new Schrodinger equation that defines a new time evolution operator $$\hat{U}_I(t,t,r) = \mathcal{T}\exp(-i\int_{t_r}^t \hat{V}_{I}(t))$$. Ensuring that averages give the same result regardless of picture chosen, all operators must evolve like in the Heisenberg picture but with $$\hat{H}_0$$ instead of the full Hamiltonian

$$
  \hat{O}_I(t) = e^{i\hat{H}_0t} O e^{-i\hat{H}_0t}.
$$

This completes the tour of the pictures of quantum mechanics, each with their merits. The Schr\"{o}dinger picture often forms the easiest route into quantum mechanics - relying on a wavefunction that describes the system at any point in time, similar to a classical mechanics description but with a new probabilistic object. The Heisenberg representation leads much more naturally into the language of second quantised operators, but it is the interaction picture in which a rigorous perturbation theory can be formulated.


## Time Evolving Averages

The next focus will be on how averages evolve in time which will be independent from the picture chosen. Writing out an average in every picture, where the hat notation of the operators is now dropped, 

$$\begin{align}
  _S\langle \psi(t)\vert O_S \vert \psi(t)\rangle_S &=  \langle \psi(t_r)\vert U^{\dagger}(t,t_r) O_S  U(t,t_r)\vert \psi(t_r)\rangle = _I\langle \psi(t)\vert O_I(t)\vert \psi(t)\rangle_I \nonumber \\
  & = \langle \psi(t_r)\vert U^{\dagger}_I(t,t_r)O_I(t)U_I(t,t_r)\vert \psi(t_r)\rangle. \label{eq:2:InteractionOperator}
\end{align}$$

Comparing terms, the full Heisenberg time evolution is related to the interacting time evolution by,

$$
  U(t,t_r) = e^{-iH_0(t-t_r)}U_I(t,t_r).
$$

This can be interpreted as beginning with the reference state and evolving it to time $$t$$ using $$U_I(t,t_r)$$ as shown in the figure below.

<figure class="align-center">
<img src="../images/QFT/OperatorEvolve.png" style="width: 70%" class="align-center">
<figcaption>An average can be interpreted as evolving an underlying state up to where an operator acts on it and the state is then time evolved back with the inner product taken. The forward and backwards paths have been displaced in the y axis to show the two different directions.</figcaption>
</figure>


With this in mind, one of the goals of this section can now be completed for single operator averages. Instead of having time ordering evolving out to time $$t$$ and anti-time ordering on the way back, all times could be described as existing on a contour in time [^2]. Using $$\tau$$ to indicate that these times are now on the contour $$C$$ of the figure, which extends from $$t_r$$ to $$t$$ and loops back round. This gives for an operator acting at a specific time $$t$$,

$$
  O_H(t) = \mathcal{T}_C \big\{ e^{-i\int_{C} V_I(\tau)d\tau} O_I(t) \big\}.
  \label{eq:2:SingleOperatorT_C}
$$

The contour ordering operator, $$\mathcal{T}_C$$, orders all operators within to act first at the earliest time along the contour. It has the same form as time ordering but is only in reference to the parameterised time on the contour rather than over the full range of time

$$
\mathcal{T}_C \{A(\tau_1)B(\tau_2) \}= \theta(\tau_1 - \tau_2)A(\tau_1)B(\tau_2) \pm \theta(\tau_2 - \tau_1)B(\tau_2)A(\tau_1).
$$

It should now be possible to understand why there was the goal of rewriting the problem in terms of one ordering rule. If there was a small parameter in the interacting part of the Hamiltonian, the exponential in the Heisenberg description can be expanded to give perturbative corrections. All of these corrections obey the same ordering rule so a robust perturbation theory can be formulated. Finding how to actually calculate these contour-ordered correction is examined next chapter. The important thing to see is that everything can be expressed in terms of the same type of object.


### Evolving Two-Point Functions


From this point onward, the analysis will only becomes more complicated - as is natural for an introductory chapter.  The natural progression is to consider how to express two operators acting at different times. From the previous section, each operator can be described in terms of a contour ordering

$$
\begin{align}
  \langle A_H(t_1)B_H(t_2)\rangle &= \langle \mathcal{T}_{C_1}\{A(t_1)e^{-i \int_{C_1} d\tau V_I(\tau)}\} \mathcal{T}_{C_2}\{B(t_2)e^{-i \int_{C_2} d\tau V_I(\tau)}\}  \rangle \nonumber
 \\
  &= \langle  \mathcal{T}_{C'} \{ A(t_1)B(t_2) \exp(-i\int_{C'} d\tau V_I(\tau))\}\rangle,
\end{align}
$$

where $$C_1$$ is the contour shown previously that evolves up to $$t_1$$ and $$C_2$$ evolves up to $$t_2$$ assuming that $$t_1>t_2$$. This double-peaked contour can be deformed into just one, as shown in the figure below. 

<figure class="align-center">
<img src="../images/QFT/2OperatorEvolve.png" style="width: 70%" class="align-center">
<figcaption> The evolution along a complicated double-peaked contour is equivalent to two operators acting on a single peaked contour. This figure demonstrates the case where t_1 < t_2 , where the shaded box shows the two parts of the contours that cancel out. </figcaption>
</figure>

This can be seen within the maths by writing the ordering explicitly,

$$
  \langle A_H(t_1)B_H(t_2)\rangle = \langle U_I^{\dagger}(t_1,t_r)A_I(t_1)\underbrace{U_I(t_1,t_r)}_{U_I(t_1,t_2)U_I(t_2,t_r)}U_I^{\dagger}(t_2,t_r)B_I(t_2)U_I(t_2,t_r)\rangle.
$$

The cancellation of the overlapping parts of the contour appears when the full evolution is split into two parts, which due to the unitarity of the operator cancels the the previous evolution. This overall contour can be therefore deformed to a single contour $$C'$$ that goes from $$t_r$$ to $$t_1$$ and back again with the operator $$B$$ acting on the forward evolution branch. The opposite case of $$t_1<t_2$$, when the order of operators stays the same, will have a contour that extends to $$t_2$$ and the operator $$A$$ will act during the backwards evolution.

It turns out that although this procedure can be generalised to larger strings of operators, often all that is needed is the two-point averages due to Wick's theorem which will be covered shortly. The newly ordered Equation not only describes $$\langle A_H(t_1)B_H(t_2)\rangle$$ when $$t_1>t_2$$, but also $$\langle B_H(t_2)A_H(t_1)\rangle$$ for $$t_1 <t_2$$.

The bedrock of QFT, the Green's function, can now be defined. This is the average of a creation and annihilation field operator, with the appropriate bosonic ($$-$$) or fermionic ($$+$$) commutation relations between them,

$$
    [ \psi(x,t), \psi^{\dagger}(x',t) ]_{\pm} = \delta(x-x').
$$

The contour-ordered Green's function becomes,

$$
    \langle \mathcal{T}\{\psi_H(x,t)\psi^{\dagger}_H(x',t')\}\rangle = \langle \mathcal{T}_C\{ \psi_I(x,t)\psi^{\dagger}_I(x',t')e^{-i\int_C d\tau V_I(\tau)}\}\rangle = iG_C(x,x';t,t').
    \label{eq:2:GFContour}
$$

It is worth recapping what has been achieved here. The appearance of all of these ordering operators stems from the time evolution operator containing time ordering. The interaction picture is used due to the possibility of not knowing the full eigenstates. In trying to express the ordering as acting on all operators in the same fashion, contour ordering was introduced.

### A Time-Ordered Theory

Having seen all these complicated things about time contours, it is natural to wonder why this rigorous of a treatment is not normally required. Time ordering by itself is actually sufficient for zero temperature QFT, but the full non-equilibrium nature to be explored in the next chapter necessitates this time-contour description.

Moving from contour ordering to time ordering, requires a way to relate the states at the reference time to a time beyond the contour. For averages at zero temperature, the system will always be in the ground state $$\vert GS\rangle$$, which may not be fully known. Knowing the evolution of the ground state along the time contour provides all the information required to compute averages.

The reason for switching into the interaction picture is to utilise the fact that there is a solution to a part of the problem, $$H_0$$. It is only when introducing the interaction $$V(t)$$, that the exact ground state is not known. If there was a time that $$V(t^*)=0$$, then there is a complete description of the state at that time. Therefore, consider a system that slowly turns on and off the interacting part[^1], such that

$$
    V(t) = e^{-\epsilon\vert t\vert } \tilde{V}(t).
$$

Changing the value of $$\epsilon$$ allows control over how fast or slow the interactions are turned on. The limit that $$\epsilon\rightarrow 0$$ corresponds to adiabatically switching on the interactions, where the slow change means that the system will always be in the same ground state. Providing that there are no crossings of energy levels or a phase transition as the interactions are varied, then the Gell-Mann and Low theorem relates the ground states at the different asymptotic times. All the caveats are included simply to ensure that the ground state remains the same ground state after the infinite time evolution.

The theorem states that the ground state after turning the interactions off at $$t=\infty$$ is related to the original ground state by a phase, $$\langle GS(t=\infty)\vert GS(t=-\infty)\rangle= e^{i\phi}$$. This is proven by expanding the time evolution operator for this specific form of interaction.

By extending the time contour beyond $$\text{max}(t_1,t_2)$$, using the previous way of cancelling contours, the contour can now stretch from $$t=-\infty$$ to $$t=\infty$$ and back again. This contour will have both operators occurring on the section that goes forward in time. The ordered average can be split into a part that orders everything in real time and a final evolution back, $$\langle U^{\dagger}(\infty,-\infty)\mathcal{T} \{ A_I(t_1)B_I(t_2)U_I(\infty,-\infty)\}\rangle$$. The final evolution back is exactly the phase factor which can be cancelled out by introducing a denominator. Contour ordering only along the forward contour is equivalent to normal time ordering. Therefore the contour average of two operators becomes,

$$
\begin{align}
  &\langle \mathcal{T}\{\hat{A}_H(t_1)\hat{B}_H(t_2)\}\rangle \\
  &\quad=  \frac{\langle GS(t=-\infty)\vert \mathcal{T}\{ A_I(t_1)B_I(t_2)\exp(-i\int_{-\infty}^{\infty} dt V_I(t))\}\vert GS(t=-\infty)\rangle}{\langle GS(t=-\infty)\vert \mathcal{T}\exp(-i\int_{-\infty}^{\infty} dt V_I(t))\}\vert GS(t=-\infty)\rangle}.\nonumber
\end{align}
$$

When time is treated as a real time, instead of the contour-ordered time, a Fourier transform to frequency space can be performed to diagonalise the expression. Often systems have time translational invariance so the two-point average will often depend on $$t_1-t_2$$ (which is shown using the cyclic nature of the trace) resulting in only one frequency variable.

## Finite Temperature - Time to Get Complex

The effect of finite temperature is to weight each eigenstate in an average by the Boltzmann factor $$e^{-\beta\varepsilon_n}$$ for the inverse temperature $$\beta$$. Allowing for variation in particle number is achieved by introducing chemical potential $$\mu$$ and weighting the eigenstates with $$N$$ particles by $$e^{\beta\mu N}$$. The total average schematically then becomes 

$$
    \langle \hat{A}\hat{B}\rangle = \frac{1}{\mathcal{Z}}\sum_n \langle n\vert \hat{A}\hat{B}e^{-\beta(\hat{H} - \mu \hat{N})}\vert n\rangle, \nonumber
$$

where the partition function $$\mathcal{Z}=\sum_n \langle n\vert e^{-\beta(\hat{H} - \mu \hat{N})}\vert n\rangle$$ normalises the average and $$\hat{N}$$ is the number operator. The sum over eigenstates now includes all states with all possible number of particles in those states. 

If the operators were time-ordered, it strongly resembles the previous formulation. The main difference is that to obtain the Boltzmann weighting, time evolution would have to evolve in imaginary time. Writing the factor as $$\exp(i\int_0^{i\beta} dt (H-\mu N))$$, makes this connection explicit. But what does it mean for operators that are defined in real time to be evolving through imaginary time? This question is answered by changing our entire description to be in terms of imaginary time.

Performing a Wick rotation[^1] into imaginary time will cause $$t \rightarrow i\tau$$ for all instances of time. This technique works best for time-independent Hamiltonians, so this form will be assumed for the rest of this section. The Heisenberg time dependence of the operators then becomes,

$$
O_H(\tau) = e^{H\tau }Oe^{- H\tau},
$$

where the reference point is taken as $$\tau_r=0$$. Having done this, an analogous interaction picture in imaginary time can be defined relating the time evolution operators in these two pictures

$$
 e^{-H\tau} = e^{H_0\tau}\mathcal{T}_{C^*}\exp(-\int_{0}^{\tau} V_I(\tau') d\tau') \label{eq:2:FiniteTInteractionPicture}
$$

where the contour time ordering now is for imaginary times, denoted by $$C^*$$. All the ideas of this chapter can be used again to express the average of two operators,

$$
e^{-\beta H}\mathcal{T}_{C^*}\{A_H(\tau_1)B_H(\tau_2) \}= e^{-\beta H}\mathcal{T}_{C^*}\{A_I(\tau_1)B_I(\tau_2)\exp(-\int_{C^{'*}}V(\tau')d\tau')\}.
$$

<figure class="align-center">
<img src="../images/QFT/FiniteTContour.png" style="width: 70%" class="align-center">
</figure>

The figure above shows the contour followed in imaginary time by the time evolution of the operator $$e^{-\beta H} O_I(\tau_1)O_I(\tau_2)\vert \psi(0)\rangle$$ in the case that $$\tau_1 > \tau_2$$. The contour could be deformed to give just a single line by cancelling the inverse evolution of $$U^{\dagger}_I(\tau_1,0)$$ with the part of $$U_I(\beta,0)$$ that goes between $$0$$ and $$\tau_1$$. 

Splitting up $$e^{-\beta H}$$ reveals a final forward evolution and an remaining factor of $$e^{-\beta\hat{H}_0}$$. This contour is shown the figure above, and can be deformed into just a single line. The time ordering on this line results in normal time ordering but in imaginary time. Our final expression is therefore,

$$\begin{align}
&\langle \mathcal{T}_C \{A_H(\tau_1)B_H(\tau_2)\}\rangle\label{eq:2:FiniteTTwoOperator} \\
&\qquad= \frac{1}{\mathcal{Z}}\sum_n \langle n(\tau=0)\vert e^{-\beta H_0}\mathcal{T}\{A_I(\tau_1)B_I(\tau_2)\exp(\int_0^{\beta}V(\tau)d\tau)\}\vert n(\tau=0)\rangle. \nonumber 
\end{align}$$

The weighting of the eigenstates is now with respect to the quadratic part of the Hamiltonian, which should be possible to calculate. In order for the averages to not diverge, $$\tau_1 - \tau_2 < \beta$$. Everything is still in imaginary time though, so the final part is to analytically continue from imaginary time back to real time.

This continuation procedure can be more clearly seen for the imaginary time Green's function, where the two operators are the creation and annihilation field operators introduced earlier. The spatial index is not affected by switching to imaginary time so can be safely ignored. If the Hamiltonian is time-independent, the Green's function only depends on the difference $$\tau \equiv \tau_1-\tau_2$$. Now a curious periodicity in imaginary time appears, with the Green's function being periodic at $$\tau = 0, \beta$$ if the field operators are bosonic. A fermionic Green's function produces an anti-periodicity at these same points.

This permits a transformation to a Fourier series in terms of the Matsubara frequencies, which have a different form for fermions and bosons

$$
    \omega_n = \begin{cases} 2\pi n \beta \quad \quad &\text{for bosons}\\
    2\pi \beta(n+ \frac{1}{2}) \quad \quad &\text{for fermions}
    \end{cases}, \quad \quad \text{where  } n \in \mathbb{N}.
$$

In the low temperature limit, the replacement of $$\omega_n \rightarrow i\omega$$ takes the problem back to real time. If the Green's function has poles or branch cuts in the complex plane, a more complicated continuation may be necessary.


## Wick's Theorem

Returning to the question of why two-point averages can form a basis for an entire theory; this is due to Wick's theorem. It states that the average of a string of contour-ordered creation and annihilation operators with respect to a quadratic Hamiltonian is equal to the sum of the products of the average of only two of these operators. This is true for any of the contours dealt with in the previous section. That is to say, for a generic operator $$c$$,

$$
  \langle \mathcal{T}_C \{ c(\tau_n) \cdots c(\tau_1)\}\rangle_{H_0} = \sum_{\text{Pairs}}\prod_{q,q'} \langle \mathcal{T}_C\{c(\tau_q)c(\tau_{q'})\}\rangle_{H_0},
$$

where $$H_0$$ is there to indicate that these averages are taking place with respect to a quadratic Hamiltonian where the eigenstates are known. 


As an example of the pairing, consider the average of a four-point function of bosonic operators, $$b(t)$$. Bosonic operators are chosen to avoid signs arising when operators are commuted through. The contour ordering and quadratic Hamiltonian notation is dropped here for clarity of the pairing process. The pairing then proceeds in the following way,

<figure class="align-center">
<img src="../images/QFT/WickFull1.png" style="width: 70%" class="align-center">
</figure>

To reiterate, each pair of operators in the original expression produces a two-point average that is multiplied into all of the other averages from the pairings for a given configuration. Summing over all configurations gives the full answer, which in this case will be just the sum of these three terms,

$$\begin{align}
  \langle b^{\dagger}(t_1)b(t_2)b^{\dagger}(t_3)b(t_4)\rangle =& \langle b^{\dagger}(t_1)b(t_2)\rangle\langle b^{\dagger}(t_3)b(t_4)\rangle + \langle b^{\dagger}(t_1)b(t_4)\rangle\langle b(t_2)b^{\dagger}(t_3)\rangle \nonumber \\
  & \quad\qquad + \langle b^{\dagger}(t_1)b^{\dagger}(t_3)\rangle\langle b(t_2)b(t_4)\rangle.
\end{align}$$

Often some of the resulting averages can be ignored. Averages with two annihilation operators will not have any matrix elements connecting them in a quadratic Hamiltonian, so the final term can be set to zero. This is unless the system is superconducting. Wick's theorem will not be proved here as the proof for contour ordering is quite involved[^2]. In many places this theorem is shown for time ordering by swapping to normal ordering - where annihilation operators act first[^3]. Functional integrals also form another path to showing this result[^4].

Here we've introduced the idea of expressing operators in terms of a contour-ordered interaction picture. This is the most general form of the problem that is designed to deal with models when the eigenstates are not exactly known. Wick’s theorem gives a procedure whereby which larger strings of contour-ordered operators can be ground up into smaller expressions. The detour to relate this contour ordering to the time ordering of zero and finite temperature equilibrium QFT highlights that all techniques here apply equally. It is going from the contour to real time where the difference between the methods appears.


## References

[^1]: Mahan, Many-Particle Physics - The original book, its a bit hard to read compared to newer texts but its got everything there.
[^2]: Rammer, Quantum Field Theory of non-equilibrium states - Super thorough and has an in-depth introduction into how all the maths works.
[^3]: Peskin and Schroeder, An Introduction to Quantum Field Theory - One of best 'modern' quantum field theory books but is much more focussed on a high-energy physics perspective. 
[^4]: Altland and Simons, Condensed Matter Field Theory - A just all round great book.