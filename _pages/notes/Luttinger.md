---
title: Luttinger Liquids
mathjax: true
permalink: "/Luttinger/"
classes: single
excerpt: "Understanding one-dimensional systems"
author_profile: false
header:
  overlay_image: "../images/Luttinger/Linearisation.png"
  overlay_filter: "rgba(118,72,115,0.9)"
  actions:
  - label: "Full Thesis"
    url: "../assets/RoseDaviesFinalThesis.pdf"

read_time: true
---

<aside class="sidebar__right sticky">
<nav class="toc" markdown="1">
<header><h4 class="nav__title" style="background:rgb(118,72,115)"><i class="fas fa-list"></i>
Contents</h4></header>
*  Auto generated table of contents
{:toc .toc__menu}
</nav>
</aside>


<i>This is adapted from a chapter in my thesis, which introduces Luttinger liquids along with extra notes that got cut. This will mostly go through how to set up the model rather than calculating correlations, focussing on the bosonisation proceedure needed to get to that point. The first half of this page is mostly descriptive and doesnt require too much QFT maths, but from the bosonisation section onward both operator and path integral methods are used extensively. </i> 

This chapter will go through the paradigm of 1D physics - the Luttinger liquid which describes the gapless low-energy excitations as a bosonic density wave. First we will explore how physics is altered in this reduced dimensionality and why conventional descriptions of continuum fermionic systems fail. The process of linearisation is examined to understand why this technique is so widely applicable, which results in a new effective model of the low-lying excitations. This effective model is then converted to the Luttinger liquid description by bosonisation. Additional electron species, in this case spin, will then be included into the description. Most of this chapter draws from Giarmachi's authoritative book on 1D physics[^1].

## One-Dimensional Idiosyncrasies

The defining feature of one-dimensional physics is that all motion must be collective. Consider a chain of particles where one particle collides with a neighbouring particle, causing some displacement. The neighbouring particle will then interact with its neighbour and create a cascade of interactions between pairs of particles that travels along the chain - a propagating longitudinal density wave. In higher dimensions, a particle can avoid or lessen a collision by going around other particles. This leads the influence of a disturbance fizzling out over shorter distances in higher dimensions for similar interaction strengths. The requirement to interact in 1D results in all excitations being density fluctuations, which are bosonic and therefore there must be a bosonic description of a fermionic 1D system. Obtaining this description is what bosonisation achieves. Tomonaga[^2] was the first to attempt to describe a one-dimensional system in this way, paving the way for the linear model introduced by Luttinger [^3] that was grouped into the `Luttinger liquid' collection of models by Haldane [^4] [^5].


The necessity to consider collective motion elevates the importance of interactions to a system; changing the statistics of particles and amplifying the effect of fluctuations. Quantum fluctuations will have their effect felt over larger distances, resulting long-range order being unable to form even at zero temperature. Statistics upon particle exchange are not only determined from the particle's inherent statistics, but also from the phase shift from collisions. This means there is a parameter related to the interactions that can be smoothly changed to describe systems with different statistics, shown in the figure below, where the parameter $$K$$ will get an explicit formulation later.

<figure class="align-center">
<img src="../images/Luttinger/LuttingerParam.png" style="width: 70%" class="align-center">
<figcaption>Varying the Luttinger parameter changes what underlying model our Luttinger liquid description corresponds to. Certain common models coincide with specific values of K that are shown here.</figcaption>
</figure>


My interest is normally in fermionic systems. The underlying solution from which interactions are adiabatically introduced differs for low-dimensional systems. In dimensions larger than two, Fermi liquid theory permits the absorption of electron-electron interactions into a renormalisation of the electron mass in the quadratic Fermi gas dispersion. The Tomonaga-Luttinger model serves as the point from which to introduce interactions in 1D.

One of the reasons that Fermi liquid theory fails in 1D is due to an inherent instability in the description. Considering the susceptibility of an equilibrium system of volume $$\Omega$$ to a static perturbation of momentum $$q$$,

$$
    \chi(q) = \frac{1}{\Omega} \sum_k \frac{f(\xi(k)) - f(\xi(k+q))}{\xi(k) - \xi(k+q)},
$$

where $$f(k)$$ is the Fermi function and $$\xi(k)$$ is the energy measured relative to the Fermi surface. This form follows from an application of Kubo formalism to a perturbation in density. For a specific $$k$$ and $$q$$ that links two points on the Fermi surface, $$\xi(k) = \xi(k+q)=0$$ resulting in a divergence in the summand. There are pairs of points in all dimensions where this `nesting' condition is met, but the divergence is smoothed out by the additional factors that appear upon exchanging the sum for an integration, such as $$k^{D-1}dk$$ when integrating an isotropic distribution in $$D$$ dimensions.

In one dimension, this divergence is not cancelled and the entire Fermi surface is nested as there are only two points. This means that the system is infinitely susceptible to a perturbation where $$q=2k_F$$. A diverging susceptibility is an indication of the original non-interacting ground state being completely different to the interacting one, as any interaction with an infinitesimal $$2k_F$$ momentum component will result in an infinite response of the system. This will change the underlying description to one that is non-trivially related to the original description. For fermions at half filling on a lattice this instability causes the Peierls transition where pairs of electrons bunch up and double the periodicity of the chain. This was looked at in more detail in the <a href="/Peierls/">Peierls notes on this website</a>.The system is not just unstable towards this process, as there is also a superconducting instability that competes with the dimerisation. The 1D system is also cursed to never be able to achieve long range order, as mentioned earlier, so these two processes compete and leave the system on the verge of instability.

It will be shown that the elementary excitations of a class of 1D models are density waves of spin and charge. Any fermionic excitation, like creating an additional electron, must necessarily split up into constituent spin and charge components. This spin-charge separation is the simplest example of charge fractionalisation, the extension of which are fractionally charged excitations.

## Tomonaga-Luttinger Model

To see how bosonic density excitations could form the low-energy excitations of a fermionic 1D model, first consider a gas of non-interacting electrons. Density fluctuations are particle-hole pairs that destroy a particle at momentum $k$ and create a particle at a new momentum $$k+q$$, denoted as $$c^{\dagger}_{k+q}c_k$$. The dispersion of a Fermi gas measured about the Fermi surface is $$\xi(k) = (k^2 - k^2_F)/2m$$, so the excitations have an energy of,

$$
    E_k(q) = \xi(k+q) - \xi(k) = \frac{2qk + q^2}{2m}.
    \label{eq:4:LuttingerModelDispersion}
$$

The average value of the energy $$E(q)$$ over the region $$[k_F - q,k_F]$$, and the variation in the energy $$\delta E(q) = \text{max}(E_k(q)) - \text{min}(E_k(q))$$ in the same segment, can be calculated. This particular region is chosen so that $$c_{k+q}^{\dagger}$$ does not act on an already filled state. This gives,

$$
    E(q) = k_Fq/m = v_Fq, \quad \quad \delta E(q) = q^2/m = E(q)^2/mv_F^2.
    \label{eq:4:Dispersion}
$$

Provided that there is a finite slope at the Fermi level (so $$v_F\ne 0$$), the average energy of an excitation only depends on the momentum of the particle-hole pair. The variation in energy goes to zero faster than the average energy. Therefore these particles will have a well defined momentum and energy that become long lived as the energy tends to zero. The independence of the above equation from the original $$k$$ means that the mapping to particle-like excitations will hold for all fillings away from the bottom of the band.

Having seen how the density fluctuations are well-defined particles, the Tomonaga-Luttinger model can now be introduced. The energy spectrum is that of a relativistic fermion, travelling at a speed $$v_F$$ instead of $$c$$

$$
    \varepsilon_q = \eta v_F q \quad \text{where }\   
    \eta = \{R=1,L=-1\}.
$$

There are two branches of the dispersion that correspond to right movers for positive $$\eta$$ and left movers for negative $$\eta$$. An excitation with negative $$q$$ (so moving to the left) will then have a positive energy, hence the extra minus sign in the dispersion. This directionality causes the branches to act as two different non-interacting fermion species if $$k_F$$ is large. Then only a large momentum scattering of $$2k_F$$ would allow a change of direction. In this model, for all possible $$q$$ to be considered, an infinite number of negative energy states must be introduced that are filled up to a certain energy - much like the Dirac sea. 

This model can be seen to represent the low-energy excitations of a Fermi liquid in 1D with electron and hole symmetry. Expanding the dispersion around the two Fermi points of the Fermi surface $$k = \pm k_F$$, where $$q= k-k_F$$, gives a dispersion of,

$$
    \xi_k = \frac{1}{2m}(k-k_F)(k+k_F) = \begin{cases} v_Fq, \quad &\text{for} \ \ k \approx k_F, \\
    -v_Fq, \quad &\text{for} \ \ k \approx - k_F.
    \end{cases}
$$

This expansion is only valid if $$k_F \gg q$$. For fluctuations caused by temperature, this condition becomes $$T \ll \epsilon_F$$. Although the increase to the infinite number of electrons in the Tomonaga-Luttinger model is unphysical, it will not affect the low-energy behaviour. The exclusion principle means that in order for electrons at a large negative energy to be able to contribute, they must be excited above the Fermi surface. This would cost a lot of energy and so the original approximation of low energies would be violated. The figure below shows this process of linearisation.

<figure class="align-center">
<img src="../images/Luttinger/Linearisation.png" style="width: 70%" class="align-center">
<figcaption>Linearising the Fermi gas dispersion about the Fermi points results in the two linear branches of the Tomonaga-Luttinger model. The solid lines indicate that the states are occupied and the dashed lines are unoccupied states, with the occupation in the Tomonaga-Luttinger model extending to $$\epsilon \rightarrow-\infty$$</figcaption>
</figure>

The reason for this extension to a Dirac sea is that the model has a complete, infinite dimensional Hilbert space with an energy spectrum that is unbounded from above. To have an exact mapping from fermions to bosons this must be the case as bosons can infinitely occupy a single mode. 

There are various different ways of mapping this model onto a bosonic one: through functional [^6] [^11], operator [^7] or phenomenological methods [^4] [^8]. The operator route is often used as there is an exact Fock space operator identity [^9], though the phenomenological pathway provides a lot of intuition as to what the bosonic fields correspond to. 

## Bosonisation
### Functional Integrals
 
The action of the Tomonaga-Luttinger model without interactions is,

$$ \begin{align}
    S_0 = S_L + S_R = \sum_{\eta}\int  dxdt \ \bar{\psi}_{\eta}(x,t) i \partial_{\eta} \psi_{\eta}(x,t), \quad \quad \partial_{\eta} = \partial_t + \eta v_F \partial_x,
    \label{eq:4:FermionicBareAction}
\end{align} $$

where there are separate fermion fields for the different chiralities. The dispersion of the linearised model is linear in momentum and therefore gains a single spatial derivative along with the usual $$p\dot{q}$$ term from the action. To reiterate that this description is equivalent to the low-energy model of the quadratic model, consider the chiral fields $$\psi_{\eta}(x,t)$$. These fields can be derived from the fields of the quadratic dispersion by considering the general Fourier transform of the field $$\psi(x,t)$$ and removing a factor of $$e^{ik_Fx}$$ to get in the vicinity of $$k = \pm k_F$$,

$$ \begin{align}
    \psi(x,t) &=e^{ik_Fx}\psi_{R}(x,t) + e^{-ik_Fx} \psi_{L}(x,t),\nonumber \\\psi_{\eta}(x,t) &= \int_{-\infty}^{\infty} \frac{d\omega}{2\pi} \int_{\eta k > 0}^{\infty} \frac{dk}{2\pi} e^{i(k-\eta k_F)x- i\omega t}\psi_{k,\omega}. \label{eq:4:chiralfield}
\end{align} $$

Therefore $$\psi_{\eta}(x,t)$$ will only have slow oscillating components when $$k \sim k_F$$. 

The density operator becomes split into chiral components,

$$
\rho = \psi^{\dagger}\psi = \rho_R + \rho_L+ e^{2ik_Fx}\psi^{\dagger}_{L}\psi_R + e^{-2ik_Fx}\psi^{\dagger}_R\psi_L, \quad \quad \text{where} \quad \rho_{\eta} = \psi^{\dagger}_{\eta}\psi_{\eta}.
\label{eq:4:DensityOperatorOscillating}
$$

The cross terms contain an rapidly oscillating component that will cause the term be negligible for any integration over space, such as the one in the action. This cannot be ignored if a large momentum scattering interaction $$2k_F$$ is relevant.

Now the foundational equation of bosonisation is introduced, which is a mapping between the fermionic field and a bosonic field $$\theta_{\eta}(x,t)$$,

$$ \begin{align}
    \psi_{\eta} = \chi e^{i\theta_{\eta}(x,t)}, \quad \quad \bar{\psi}_{\eta} = \chi e^{-i\theta_{\eta}(x,t)},
    \label{eq:4:Bosonisation}
\end{align} $$

where $$\chi$$ is a global Majorana field, included to ensure the proper anticommutation of fermionic fields while commuting with the bosonic fields. From an operator perspective, this factor here should also reduce/raise the number of fermions in the system by one, amounting to a shift in $$k_F$$. In the thermodynamic limit, this shift is very small so can be ignored. When calculating averages that have an equal number of creation and annihilation operators, the raising and lowering operator take us back to the original particle number subspace and can therefore be left out. This is why despite seeming crucial to this derivation, they do not often appear. Majorana fields have the property that they are their conjugate, so $$\bar{\chi} = \chi$$. The anticommutation implies that $$\chi^2 = 0$$.

Naively substituting this transformation into the action results in the action becoming zero due to both $$\chi^2=0$$ and $$\partial_x\chi=0$$ with the latter caused by the global nature of the Majorana field. In all methods of bosonisation, there are spurious zeroes that occur that upon closer inspection, have a finite value. When using functional bosonisation, this is a manifestation of the QFT anomaly. The way to obtain a non-zero action is to look at the measure of the partition function when changing variables. The anomaly arises as the symmetry of the classical action under this chiral transformation $$\psi_{\eta} \rightarrow \psi_{\eta} e^{i\eta\theta_{\eta}}$$ (suppressing the variables of the fields from now on) is not obeyed by the Jacobian of the transformation, which affects the measure $$\mathcal{D}\psi_{\eta}$$ in the partition function. 

To understand how this symmetry is preserved in the measure, consider the gauge transformation $$\psi_{\eta} \rightarrow \tilde{\psi}_{\eta}e^{i\theta}$$ on the action, where not using Majorana fields means the action does not vanish. The transformed action becomes,

$$
    \tilde{S} = \int dx dt \ \tilde{\bar{\psi}}_{\eta}(i\partial_{\eta} + \partial_{\eta}\theta_{\eta}) \tilde{\psi}_{\eta}.
$$

The partition functions $$\mathcal{Z}_{\eta} = \int \mathcal{D}\psi_{\eta} e^{iS_{\eta}}$$ for the original and transformed action can be calculated as the fields are quadratic in the action. The relation of these to each other defines the Jacobian of the transformation,

$$
    \mathcal{Z}_{\eta} = J_{\eta} \tilde{\mathcal{Z}}_{\eta}, \implies J_{\eta} = \frac{\det(g^{-1}_{\eta})}{\det(g^{-1}_{\eta} + \partial_{\eta}\theta_{\eta})},
    \label{eq:4:JacobianDef}
$$

where $$g^{-1}_{\eta}$$ is the inverse of the Green's function for the equation of motion,

$$
    i\partial_{\eta} g_{\eta} = \delta(x-x')\delta(t-t').
$$

Upon using the ubiquitous linear algebra identity, $$\ln(\det(A)) = \text{Tr}(\ln(A))$$ for a matrix $$A$$, the equation can be seen as a disguised exponential and therefore as a contribution to the action. Upon performing the trace over the Green's functions, the Jacobian becomes,

$$ \begin{align}
    \ln(J_{\eta}) = - \frac{i\eta}{4\pi} \ \text{Tr}(\partial_{\eta}\theta_{\eta}\partial_x\theta_{\eta}).
    \label{eq:4:JacobianSimplification}
\end{align} $$

The derivation of this result is presented in a Blog post soon. Defining new fields $$\theta = (\theta_L - \theta_R)/2$$ and $$\phi = (\theta_L + \theta_R)/2$$, the action which is determined fully by the Jacobian becomes,

$$ \begin{align}
    S_0 &= \frac{1}{4\pi} \int dx dt \ \partial_L \theta_L \partial_x\theta_L - \partial_R\theta_R\partial_x\theta_R \nonumber \\ 
    &= \frac{1}{2\pi} \int dx dt \ \partial_t\theta\partial_x\phi + \partial_t\phi\partial_x\theta - v_F(\partial_x\theta)^2 - v_F(\partial_x\phi)^2.\label{eq:4:ActionSpinlessLLBeforeIntegrating}
\end{align} $$

Integrating one of the first two terms by parts and then performing the functional integral over one of the fields gives two possibilities for the action, dependent on what field was integrated out. Any contribution from the quadratic functional integral that is integrated out will be cancelled out by the denominator in an average and therefore can be forgotten. The bosonised action is,

$$ 
\begin{align}
    S_0 &=  \frac{1}{2\pi v_F} \int dxdt \ (\partial_t \theta)^2 - v_F^2(\partial_x\theta)^2, \label{eq:4:SpinlessLLAction}\\
    &= \frac{1}{2\pi v_F} \int dxdt \ (\partial_t \phi)^2 - v_F^2(\partial_x\phi)^2.
\end{align} 
$$

This dual representation allows whatever action is most convenient to be used. The distinction here seems academic, but upon including interactions the two actions will have different forms. In trying to obtain a representation of the density in this new bosonised form, the anomaly once again rears its ugly head, as $$\rho_{\eta} = \bar{\psi}_{\eta}\psi_{\eta}$$ will be zero upon Bosonising. The antidote this time is to introduce a source field prior to bosonisation, which when differentiated gives the density. Carrying it through the derivation, the density becomes,

$$ 
\begin{align}
    \rho_{\eta} = \frac{\eta}{2\pi} \partial_x \theta_{\eta}, \quad \quad \implies \quad \rho = -\frac{1}{\pi} \partial_x \theta.\label{eq:4:DensityInLL}
\end{align} 
$$

This issue can also be resolved by point splitting the fields and being more careful in the limit that the fields are evaluated in the same point[^10]. From the continuity equation, the current can be found to be,

$$
    \partial_t \rho = - \partial_x j, \qquad j = \frac{1}{\pi}\partial_t \theta.
$$

If this bosonisation procedure was performed with operators, it can be found the the operator fields $$\theta$$ and $$\partial_x\phi$$ are conjugate variables and satisfy the canonical commutation relations with an extra factor of $$\pi$$.

*Often the definition of fields $$\theta$$ and $$\phi$$ are swapped depending on the authors - so always check the density and current definitions!*

### Operator Interpretation

Now we will repeat the derivation but from an operator perspective, essentially lifted from Giamarchi[^1]. There may be some repitition of points but each section is meant to serve as a possible introduction to bosonisation! We are trying to diagonalise and solve a generic interacting Hamiltonian in one dimension, which when the linearised dispersion is included will have the following form.

$$\begin{align}
    \mathcal{H} &= \sum_{\eta = \pm} \mathcal{H}_{0\eta} + \mathcal{H}_{int}, \quad \quad   \mathcal{H}_{int} = \frac{1}{2} \int \rho(x')V(x'-x)\rho(x) dx'dx
\end{align}
$$

The second section showed that an electron-hole fluctuation would be a good basis so we will now consider a superposition of them at various different momenta,

$$
\begin{equation}
    \rho^{\dagger}(q) = \sum_{k} c^{\dagger}_{k+q}c_k.
    \label{eq:density}
\end{equation}
$$

The benefit of the electron-hole representation is that it reduces the interaction term in the Hamiltonian from quartic in operators to quadratic in the operators, making it easily solvable. The kinetic energy term still however needs to be formulated in this new basis.

One final complication is that normal ordering of operators must be introduced to compensate for the infinite number of states in the Tomonaga-Luttinger model. In our case this is equivalent to subtracting off the average value of the operator within the vacuum. Therefore the normal ordered density becomes:

$$
\begin{align}
    : \rho^{\dagger}_{\eta}(q) : &= \sum_k c^{\dagger}_{\eta, k+q}c_{\eta,k}, \quad  \quad (q \ne 0) \\
    &=N_{\eta} = \sum_k c^{\dagger}_{\eta, k}c_{\eta,k} - \langle 0 \vert c^{\dagger}_{\eta, k}c_{\eta,k}\vert 0 \rangle, 
    \quad (q=0)
\end{align}
$$

which defines the number operator $$N_{\eta}$$ for one of the chiralities. Calculating the commutator and taking $$k$$ to be quantised, being mindful of the normal ordered nature, gives:

$$
\begin{equation}
    [\rho^{\dagger}_{\eta}(q), \rho^{\dagger}_{\eta'}(q')] = - \delta_{\eta,\eta'}\delta_{q,q'} \frac{\eta q L}{2\pi}
\end{equation}
$$

These are, up to normalisation, the boson commutator relations! The different chiralities will annihilate states with the `opposite' momentum in the following way:

$$
\begin{equation}
    \rho^{\dagger}_L( p > 0 ) \vert 0 \rangle  = 0, \quad \quad \rho^{\dagger}_R( p < 0 ) \vert 0 \rangle  = 0, 
\end{equation}
$$

This allows boson creation and annihilation operators, with the bosonic canonical commutation operators to be defined:

$$
\begin{align}
    b^{\dagger}_q = \Big(\frac{2\pi}{L\vert q\vert }\Big)^{1/2} \sum_{\eta} \Theta(\eta q)\rho^{\dagger}_{\eta}(q) \\
    b_q = \Big(\frac{2\pi}{L\vert q\vert}\Big)^{1/2} \sum_{\eta} \Theta(\eta q)\rho^{\dagger}_{\eta}(-q)
\end{align}
$$

where $$\Theta(\eta q)$$ is the step function. Commuting these new bosonic operators with the kinetic Hamiltonian part allows us to find a repesentation of it:

$$
\begin{equation}
    H_{kin} \approx \sum_{q\ne 0}v_F\vert q\vert b^{\dagger}_qb_q
\end{equation}
$$

This shows that the kinetic energy, normally expressed quadratically in fermion operators, can be expressed as a term that is quartic in fermion operators and therefore quadratic in the bosonic operators. This finally shows that through considering density fluctuations to be the low energy excitations, we can completely express all terms in the Hamiltonian as bosonisic fluctuations.

To show exactly how the interactions are expressed in terms of the particle-hole fluctuations, the single particle operator that destroy an electron of a specific chirality $$\psi_{\eta}(x)$$ must be first investigated. Following the same method as done previously from the Hamiltonian, it can be seen that the operator should have the following form:

$$
\begin{equation}
\psi_{\eta}(x) \approx \exp( \sum_q e^{iqx} \rho^{\dagger}_{\eta}(-q) \frac{2\pi \eta}{qL})
\label{eq:SingleFermionNoKlein}
\end{equation}
$$

However there is a slight issue with $$\psi_{\eta}$$ changing the total particle number and being expressed as an infinite sum of operators, $$\rho^{\dagger}$$, that conserve particle number. The introduction of a Klein factor, $$U_{\eta}$$, which multiplies the previous definition, resolves this problem. It will commute with the boson operators, and destroys or creates a fermion appropriately.

Adding the Klein factors allows a rigorous mapping between the fermion to the boson basis to be formulated (briefly explained in a following section), though a lot of the time this factor does not impact many of the properties of a 1D material.

Often it is most convenient to work with the fields $$\theta(x)$$ and $$\phi(x)$$, defined as :

$$
\begin{align}
    \phi(x) &= -(N_R + N_L)\frac{\pi x}{L} - \frac{i\pi}{L}\sum_{p \ne 0}\frac{1}{p}\exp(-ipx) (\rho^{\dagger}_{R}(p) + \rho^{\dagger}_L(p) \\
    \theta(x) &= (N_R - N_L)\frac{\pi x}{L} + \frac{i\pi}{L}\sum_{p \ne 0}\frac{1}{p}\exp(-ipx) (\rho^{\dagger}_{R}(p) - \rho^{\dagger}_L(p)
\end{align}
$$

These are used as $$\theta(x)$$ and $$\nabla\phi(x)$$ turn out to be conjugate operators and have a simple interpretation. $$\nabla\phi$$ is the (negative) sum of the densities, being the $$ q \sim 0$$ part of density fluctuations. The other field $$\nabla\theta$$ is the difference between the two chiralities - the current!
Summarising these results we have a Hamiltonian of the following form which describes the kinetic part of a 1D system:

$$
\begin{equation}
    H = \frac{1}{2\pi} \int dx v_F\Big( \pi\nabla\theta(x))^2 + (\nabla\phi(x))^2\Big)
\end{equation}
$$

and the single particle operator has the famous bosonisation form:

$$
\begin{equation}
\psi_{\eta}(x) \sim U_{\eta}e^{i\eta k_Fx}e^{-i(\eta\phi(x) - \theta(x))}
\end{equation}
$$

A point that is not clear when the derivation is presented this way, but is clearer in the functional derivation approach, is that a duality exists in these representations. This means that swapping the $$\phi$$ and $$\theta$$ around gives the exact same physics. Although this seems redundant at this point, these two representations absorb the interactions in a different way so changing between the two becomes an invaluable tool in calculations. 

#### Operator Identity

The reason why one dimensional fermion theories can be rewritten using bosonic degrees of freedom is that a one dimensional Fock space can be decomposed into the direct sum of Hilbert spaces. Each of these Hilbert spaces contain a fixed particle number and all have particle-hole excitations so are bosonic in nature. This is an operator identity and is therefore independent of all details of the Hamiltonian and system. This can be seen as a state with a set amount of electrons will not have the number of electrons changed by electron-hole fluctuations but these allow access to all energetic states. The direct sum of these Hilbert spaces produces the Fock space that we work within. 

The derivation of this[^9], requires knowledge of coherent states and their properties. These are used to produce a cancellation of a huge number of particle-hole contributions, resulting in the single particle operator having an exponential form. By considering the action of the single particle operator on the $$n$$-particle Hilbert space and relaxing conditions on normal ordering and regularisation, we end up with the famous bosonisation formula

$$
\begin{align}
    \psi = \chi e^{i\theta}
\end{align}
$$

which is the same substitution that was used in the functional method. Here, $$\chi$$ is a Klein factor and by following the method through, it can be seen that the action of the Klein factor lowers the number of fermions by one - essentially changing between the fixed particle number Hilbert spaces. As a side note, to get around the QFT anomaly when using operators we ensure normal ordering when evaluating commutation relations.

### Phenomenological Bosonisation

This method of bosonisation does not depend on the details of the system at all and uses very *ad hoc* assumptions like stating the bosonisation identity, but it gives useful insight into how the fields relate to variables even if it feels like its been reverse engineered! This layout follows Giamarchi[^1] again and first introduces a labelling field. This labelling field is a continuous function of the position and takes the value $$2\pi n$$ at the $$n$$-th particle, essentially labelling each particle. However in contrast to higher dimensions, this field is well defined as there is a unique way to number the particle (ie going from left to right!) which is not possible in higher dimensions. Rewriting the density operator in terms of this labelling field and using the Poisson summation formula, it can be shown that:

$$
\begin{align}
    \rho(x) = \frac{\nabla\phi_l(x)}{2\pi} \sum_p e^{ip\phi_l(x)} \quad \text{where} \ \ p \in \mathbb{N}
\end{align}
$$

By defining a field $$\phi$$ that is relative to the perfect crystalline solution (when each particle is the same distance apart). This gives our new form of the density operator:

$$
\begin{align}
    \rho(x) = \Big( \rho_0 - \frac{\nabla\phi(x)}{\pi} \Big) \sum_p e^{2ip(\pi\rho_0x-\rho(x))}
\end{align}
$$

If the average is taken over large distances (compared to interparticle spacing) then the oscillating terms in the sum will average to zero, leaving the $$p=0$$ term. Giving our smeared density of:

$$
\begin{align}
    \rho_{q \sim 0} \approx \rho_0 - \frac{\nabla\phi(x)}{\pi}
\end{align}
$$

Turning our concentration to a single particle creation operator, which can always be written in the bosonisation form:

$$
\begin{align}
    \psi^{\dagger}(x) = \sqrt{\rho(x)} e^{-i\theta(x)}
\end{align}
$$

Evaluating the commutator of the single particle creation and annihilation operators using the above formula gives conditions on our fields - which is that the fields $$\theta$$ and $$\nabla\phi/\pi$$ are canonically conjugate. The canonically conjugate nature of the fields means that they have a representation in terms of bosonic operators - so its a simple harmonic oscillator!

Substituting our $$\rho$$ into the $$\psi$$ equation gives a way to represent the excitations of the system in terms of variables that are defined in the continuum limit. From symmetry considerations, the Hamiltonian can be formed and the action found from this.
## Including Interactions


The strength of this technique is in how it simplifies interactions. It has just been shown that, surprisingly, a kinetic term that is quadratic in fermionic fields is also quadratic in bosonic fields. For terms that are quartic in the fermionic fields, it is obvious that this can be expressed by two bosonic fields. The interaction term in a generic fermionic model is 

$$
    S_{int} = \int dxdx'dtdt' \ \bar{\psi}(x,t)\psi(x,t)V(x,x';t,t')\bar{\psi}(x',t')\psi(x',t) \sim  \int dxdt \rho^2(x,t) . \label{eq:4:SintSpinless}
$$


The 'g-ology' formalism (rare to get a fun joke in physics!) of interactions in the Tomonaga-Luttinger model is obtained through setting the interactions to be instantaneous and only upon contact, $$V(x,x';t,t') \sim \delta(x-x')\delta(t-t')$$. This strongly screened Coulomb approximation manages to retain a lot of the underlying physics despite its apparent restriction. This interaction, however, is not modelled as entirely featureless with a different weighting being given to the terms that appear upon seperating the chiralities into the interacting action,

$$ \begin{align}
    S_{int} = \int dx &dt \  g_4 (\rho_L^2 + \rho_R^2) + g_2 \rho_2\rho_4 \nonumber \\
    &+ (g_1 \psi^{\dagger}_L\psi_R\psi^{\dagger}_R\psi_L + g_3e^{4ik_Fx} \psi^{\dagger}_L\psi_R\psi^{\dagger}_L\psi_R + \text{h.c.}), \label{eq:4:spinlessInteraction}
\end{align} $$

where the $$e^{2ik_Fx}$$ terms are averaged out. The $$g_3$$ term can be relevant if there is umklapp scattering from the presence of a lattice - this is the cause of the Peierls distortion. In the spinless case, where just one fermionic species is considered, $$g_1$$ is a rearrangement of $$g_2$$ and can therefore be absorbed into the definition of the $$g_2$$ terms. When performing the spinful analysis in the next section, this cannot be completely absorbed. 

Away from specific fillings of a lattice, there will be no relevant umklapp scattering so the interaction just contains the $$g_2$$ and $$g_4$$ term. Using the equivalent density for the bosonic fields the action becomes,

$$ \begin{align}
S_{int} = \int dx dt \ \frac{g_4}{4\pi^2}\big( (\partial_x\theta_L)^2 + (\partial_x\theta_R)^2 \big) - \frac{g_2}{4\pi}\partial_x\theta_L\partial_x\theta_R.
\end{align} $$

Performing the same substitution as before where $$\theta_L = \theta + \phi, \theta_R =  \phi-\theta$$ gives a final action of 

$$
    S =\frac{1}{2\pi} \int dx dt \  2\partial_x\phi\partial_t\theta - \Big(v_F +\frac{g_2}{2\pi}+\frac{g_4}{2\pi}\Big)(\partial_x\theta)^2 - \Big(v_F+ \frac{g_4}{2\pi}-\frac{g_2}{2\pi}\Big)(\partial_x\phi)^2.
$$

Commonly, the coefficients of the gradient terms are defined  using variables $$\nu$$ and $$K$$ where

$$ \begin{align}
    \nu K = v_F +\frac{g_2}{2\pi}+\frac{g_4}{2\pi},\quad& \quad  \frac{\nu}{K} = v_F+ \frac{g_4}{2\pi}-\frac{g_2}{2\pi} \nonumber \\
    \implies K = \sqrt{\frac{2\pi v_F+ g_4 - g_2}{2\pi v_F + g_4 + g_2}}, \quad &\quad \nu = v_F \sqrt{\Big(1 + \frac{g_4}{2\pi v_F}\Big)^2 - \Big(\frac{g_2}{2\pi v_F}\Big)^2}.\label{eq:4:nuKdefinitions}
\end{align} $$

The action can then be integrated out to give,

$$ \begin{align}
  S &= \frac{K}{2\pi\nu} \int dx dt \ \Big( (\partial_t\phi)^2 - \nu^2 (\partial_x\phi)^2 \Big) \label{eq:4:phiLLaction}\\
  S &= \frac{1}{2\pi\nu K} \int dx dt\ \Big( (\partial_t\theta)^2 -\nu^2 (\partial_x\theta)^2\Big). \label{eq:4:thetaLLAction}
\end{align} $$

Finally, we have obtained an explicit formula for the Luttinger parameter $$K$$ that was introduced conceptually at the start of the chapter. The above form means that for $$g_4$$ and $$g_2$$ being positive constants, as they should be for a fermionic model, then $$K\leq 1$$. This confirms what was previously show in the first figure, that fermionic models correspond to this region of $$K$$. This action can be expressed in terms of an inverse Green's function by integrating by parts,

$$
    S = \frac{1}{2\pi\nu K} \int dxdt \ \theta \Big( \partial_t^2 - \nu^2 \partial_x^2\Big) \theta = \frac{1}{2} \int dxdt \ \theta(x,t) G^{-1}(x,x',t,t')\theta(x't').\label{eq:4:LuttingerActionGFForm}
$$

The field dependencies have appeared again to make it clear that this expresses the inverse Green's function in position and real time. From this form, all the other Green's functions can be found through computing the Fourier transforms.

The overall effect of this renormalisation on the spectrum is that the dispersion becomes $$\varepsilon_q = \eta\nu q$$, where $$\nu$$ has replaced $$v_F$$. In this final form the reason for the dual actions can be seen as the interaction parameter $$K$$ is inverted in the two different representations. This means that if the parameter is large in one representation, we can use the dual to express our action in such a way that the parameter is small and a perturbative expansion can be found.

## Spinful Luttinger Liquids


Including the electron's spin into the non-interacting Tomonaga-Luttinger model simply doubles the degrees of freedom with 4 types of fermion, one for each chirality and spin.
Each of these can be bosonised by,

$$
    \psi_{\eta\sigma} = \chi_{\sigma} e^{i\theta_{\eta\sigma}},
$$

where $$\sigma = \{ \uparrow,\downarrow\}$$. Following the same procedure of calculating the Jacobian gives the kinetic part of the action as,

$$
    S_0 = \frac{1}{2\pi v_F}\sum_{\sigma}\int dx dt\ (\partial_t \theta_{\sigma})^2 - v_F^2 (\partial_x\theta_{\sigma})^2,
$$

with the new fields $$\theta_{\sigma} = \theta_{L\sigma} - \theta_{R\sigma}$$, $$\phi_{\sigma} = \theta_{L\sigma}+\theta_{R\sigma}$$. The density is then generalised as

$$
    \rho_{\eta\sigma} = -\frac{\eta}{2\pi}\partial_x\theta_{\eta\sigma}, \quad \quad \rho_{\sigma} = -\frac{1}{\pi}\partial_x\theta_{\sigma}.
$$

The full electron-electron interaction is a generalisation the previous case to where the density fluctuations of a particular spin species will influence other density fluctuations. Splitting the field of each spin into the left and right chiral components gives an interaction term that can be split up into the different possible pairings of chirality. The terms are,

$$ \begin{align}
    S_{int}=S_1 + S_2 + S_4 &\sim \int dxdt \ \sum_{\substack{\eta_1\eta_2\eta_3\eta_4 \\ \sigma_1\sigma_2}} \psi^{\dagger}_{\eta_1\sigma_1}\psi_{\eta_2\sigma_1}\psi^{\dagger}_{\eta_3\sigma_2}\psi_{\eta_4\sigma_2},  \\
    S_4 &= \int dxdt\sum_{\sigma, \eta} g_{4\perp } \rho_{\eta\sigma}\rho_{\eta\bar{\sigma}} + g_{4\vert\vert} \rho_{\eta\sigma}\rho_{\eta\sigma},\\
    S_2 &= \int dxdt\sum_{\sigma}g_{2\perp} \rho_{L\sigma}\rho_{R\bar{\sigma}} + g_{2\vert\vert} \rho_{L\sigma}\rho_{R\sigma},\\
    S_1 &= \int dxdt\sum_{\sigma} g_{1\vert\vert} \psi^{\dagger}_{L\sigma}\psi^{
    \dagger}_{R\sigma}\psi_{L\sigma}\psi_{R\sigma} + g_{1\perp} \psi^{\dagger}_{L\sigma}\psi^{\dagger}_{R\bar{\sigma}}\psi_{L\bar{\sigma}}\psi_{R\sigma} + \text{h.c},
\end{align} $$

where the introduction of $$\perp$$ and $$\vert\vert$$ is to denote whether the interaction is between different spins or the same spins respectively. The umklapp terms that should appear with $$g_3$$ are again ignored. Mirroring the spinless case, $$g_{1\vert\vert}$$ can be rearranged to give a contribution of the form $$g_{2\vert\vert}$$. However, $$g_{1\perp}$$ contains interactions between different spin species and cannot be formulated in terms of densities.

Ignoring the $$g_{1\perp}$$ term for the moment, the $$g_2$$ and $$g_4$$ spinful terms have terms that mix the $$\theta_{\uparrow}$$ and $$\theta_{\downarrow}$$ fields. A rotation is therefore made to diagonalise the Hamiltonian, which introduces charge and spin fields,

$$ \begin{align}
    \theta_{\rho} = \frac{1}{\sqrt{2}}(\theta_{\uparrow} + \theta_{\downarrow}), \quad &\quad \theta_{\sigma} = \frac{1}{\sqrt{2}}(\theta_{\uparrow} - \theta_{\downarrow}), \nonumber \\
        \phi_{\rho} = \frac{1}{\sqrt{2}}(\phi_{\uparrow} + \phi_{\downarrow}), \quad &\quad \phi_{\sigma} = \frac{1}{\sqrt{2}}(\phi_{\uparrow} - \phi_{\downarrow}) \label{eq:4:spinphithetarotation}
    .
\end{align} $$

With these definitions, and the patience to perform some algebra, both the $$g_{2}$$ and $$g_4$$ terms can be absorbed into a quadratic description. The $$g_1$$ term however results in a different kind of term upon bosonising, 

$$
    \bar{\psi}_{L\uparrow}\bar{\psi}_{R\downarrow}\psi_{L\downarrow}\psi_{R\uparrow} \sim e^{-i(\theta_{L\uparrow}+\theta_{R\downarrow} - \theta_{L\downarrow}-\theta_{R\uparrow})} = e^{-2i\sqrt{2}\theta_s} .
$$

Adding this to its Hermitian conjugate gives a final action,

$$ 
\begin{align}
    S &= \frac{1}{2\pi\nu_{\rho} K_{\rho}}\int dx dt (\partial_t\theta_{\rho})^2 + \nu_{\rho}^2 (\partial_x\theta_{\rho})^2\nonumber\\
    & \quad + \frac{1}{2\pi\nu_{\sigma} K_{\sigma}}\int dx dt (\partial_t\theta_{\sigma})^2 + \nu_{\sigma}^2 (\partial_x\theta_{\sigma})^2 + \int dxdt \ 2g_{1\perp} \cos(2\sqrt{2}\theta_{\sigma}). 
\end{align} 
$$

The $$\nu_{a}$$ and $$K_{a}$$ parameters, where $$a = \{ \rho, \sigma\}$$, are given by,

$$ \begin{align}
    K_{a} = \sqrt{\frac{2\pi v_F+ g_{4a} - g_{2a}}{2\pi v_F + g_{4a}+ g_{2a}}}, \quad &\quad \nu_{a} = v_F \sqrt{\Big(1 + \frac{g_{4a}}{2\pi v_F}\Big)^2 - \Big(\frac{g_{2a}}{2\pi v_F}\Big)^2}, \label{eq:4:nuKSpinfull} \\
   \text{for} \quad g_{2a} = g_{1\vert\vert} - g_{2\vert\vert} \pm g_{2\perp}, \quad &\quad g_{4a} = g_{4\vert\vert} \pm g_{4\perp}, \nonumber
\end{align} $$

where $$\rho$$ corresponds to the positive sign choice and $$\sigma$$ for the negative. Note that the action could be equivalently described with $$\phi_{\rho}$$ instead of $$\theta_{\rho}$$ which amounts to using the form of dual action with the new spinful Luttinger parameters.

Now the spin and charge fields are completely decoupled and unaffected by each other's dynamics. This is the spin-charge separation mentioned at the beginning of the chapter and presents an example of fractionalisation. The spin sector however now contains a curious cosine term. This will have no affect on the charge transport but will obviously result in different behaviour for the spins.

A final side note is that all of this analysis relied on bosonising the full Tomonaga-Luttinger model with its infinite spectrum but many systems have a finite bandwidth. To mimic this in the bosonic fields, a factor of $$(2\pi\alpha)^{-1/2}$$ where $$\alpha$$ is related to the bandwidth is introduced to the bosonisation formula as well as a restriction on the momentum integrals to being over the bandwidth.


## References

[^1]: Giamarchi's book which is amazing to keep returning to - *One-Dimensional Physics*
[^2]: Original Tomonaga paper - *Remarks on Bloch's Method of Sound Waves applied to Many-Fermion Problems* - <a href="https://academic.oup.com/ptp/article/5/4/544/1926191"> open access</a>
[^3]: Luttinger's Original paper - *An Exactly Soluble Model of a Many‐Fermion System* - <a href="https://pubs.aip.org/aip/jmp/article/4/9/1154/229917/An-Exactly-Soluble-Model-of-a-Many-Fermion-System"> open access</a>
[^4]: Haldane's grouping of the Luttinger Liquid model - *'Luttinger liquid theory' of one-dimensional quantum fluids* - <a href="https://iopscience.iop.org/article/10.1088/0022-3719/14/19/010"> Link to publisher</a>
[^5]: Schonhammer has a great historical overview of the development - *Luttinger Liquids: The Basis Concepts* - <a href="https://arxiv.org/pdf/cond-mat/0305035.pdf">arxiv paper</a>
[^6]: Lee and Chen, this one is self explanatory - *Functional bosonisation of the Tomonaga-Luttinger model* - <a href="https://iopscience.iop.org/article/10.1088/0305-4470/21/22/018/pdf">Here</a>
[^7]: Voit review, essential reading - *One-Dimensional Fermi liquids* - <a href="https://arxiv.org/abs/cond-mat/9510014">Here</a>
[^8]: Cazalilla - *Bosonizing one-dimensional cold atomic gases* - <a href="https://arxiv.org/abs/cond-mat/0307033">Here </a>
[^9]: Von Delft and Schoeller, also essential - *Bosonization for Beginners — Refermionization for Experts* - <a href="https://arxiv.org/abs/cond-mat/9805275"> Here </a>
[^10]: Shankar has a book that covers many topics in reasonable depth - *Quantum Field Theory and Condensed Matter*
[^11] Yurkevich and Lerner, goes into good depth at the functional proceedure - *Impurity in the Tomonaga-Luttinger model: a Functional Integral Approach*- <a href="https://arxiv.org/abs/cond-mat/0508223">Here</a>
