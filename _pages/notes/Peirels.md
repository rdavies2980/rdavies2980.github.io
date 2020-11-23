---
title: Peierls Instability
mathjax: true
permalink: "/Peierls/"
toc: true
toc_label: "Contents"
toc_icon: "list"
toc_sticky: true
classes: single
excerpt: "Investigating an instability that is unavoidable in 1D physics"
author_profile: false
header:
  overlay_image: "../images/Peierls/PeierlsHeader.png"
  overlay_filter: "rgba(23,147,200,0.9)"
  actions:
  - label: "Download PDF Version"
    url: "../assets/notes/Peierls_Ideas.pdf"

read_time: true
---

The Peierls instability (Kohn anomaly) is an unavoidable consequence of doing physics in 1D. Originally discovered when considering the energy of a half filled electronic band and finding that the energy is lowered by a periodic distortion of the underlying lattice - which can be shown using second order perturbation theory in quantum mechanics (in fact Peierls was writing an introductory solid state book when finding this out). This particular situation is called the Peierls transition but it is much more general than this specific half filled case.


This phenomenon sprung into relevance during the search for higher temperature superconductors in the 70's. Essentially materials that have 1D behaviour due to highly anisotropic electron bands form linear chains of molecules, were expected to result in a large electron-phonon coupling and hence a high $$T_c$$. Upon cooling, however, these materials became insulators rather than superconductors - this was realised to be a manifestation of this Peierls transition. Famously, the SSH model was designed for one of these materials (polyacetylene) and it is the Peierls transition that enforces the alternating double and single band structure in the ground state.

These notes will go through the response functions for generic 1D systems, showing why 1D is special and requires extra care. Then putting this into the context of electrons on a lattice, we will find the physical meaning of this diverging of susceptibility and try to understand what new phase arises because of it.


## Response Function of a 1DEG #

### Responding To External Field At Zero Temperature

To understand the reason why the phenomenon occurs, we need to examine the response of a 1D Electron Gas. This is done within the confines of linear response theory by asking how a time independent potential, $$\phi(r)$$, affects an electron gas. This will cause the charge density to rearrange to a more optimal position, and we express this as an induced charge $$\rho_{ind}(r)$$.  These two quantity are related by the Lindhard response function (for static perturbations),

$$
    \rho_{ind}(k) = \chi(k)\phi(k), \quad \quad \chi(k) = \int \frac{d^dq}{(2\pi)^d} \frac{f_q - f_{q+k}}{\epsilon_q - \epsilon_{q+k}}
$$

where $$f_q = f(\epsilon_q)$$ is the Fermi function. To dive a little into the derivation of this, there are multiple ways in which this can be found. It was originally derived when trying to calculate behaviour of an interacting Fermi gas, introducing a self consistent field to avoid divergence issues (as we are essentially dealing with electron-electron interactions). For those who know QFT well, it is the polarisation operator for an isotropic system and uses the random phase approximation. It is essentially given by $$\sim \sum_q G_qG_{p+k}$$. See the resources for a detailed description of how to find this particular form of the function [^1].


The derivation for the people who know how Kubo works in general is quite easy as it is simply the usual commutator

$$
    \chi(r,t; r',t') = \frac{-i}{\hbar} \Theta(t-t') \langle [ \rho(r,t), \rho(r',t') ] \rangle_0
$$

This can also be derived through considering the action associated with a generic electron-phonon action and then integrating out the fermionic degrees of freedom and expanding to second order, giving the Green's function version of the expression. This is a problem in Chapter 6 of Altland and Simons[^2].

Ignoring the derivation and believing that the susceptibility is given by this function, we will look into the behaviour of this function. We can see that any vector $$k$$ that links two points of the same energy will cause singularities - this is known as nesting. However, for it to have the full effect, one of the momenta must be occupied and the other unoccupied (This is to avoid integrating over a 0/0 and to integrate over a 1/0 instead which will give the largest contribution). This condition is sometimes stated as $$\epsilon(k) = -\epsilon(K+Q)$$ The integral over $$q$$ introduces as factor of $$q^{d-1}$$ which makes this less of problem in high dimensions and smooths out any discontinuities and regulates it to derivatives of the susceptibility.

In 1D however, the topology of the Fermi surface means that we have perfect nesting. Every single point on the Fermi surface is related by one vector (because there is only two points!). Therefore we should expect some sort of divergence at this point. So manipulating the integral to be in a nicer form:

$$\begin{align}
    \chi(k) &= \int \frac{d^dq}{(2\pi)^d} \frac{f_q}{\epsilon_q - \epsilon_{q+k}} - \frac{f_q}{\epsilon_{q-k} - \epsilon_{q}} \\
    &= \int_{q\le q_F} \frac{d^dq}{(2\pi)^d} \frac{1}{k^2 + 2k\cdot q} - \frac{1}{k^2 - 2k\cdot q} \\
    &= \int_{q \le q_F} \frac{d^dq}{(2\pi)^d} \frac{q^2}{q^4 - 4(q \cdot k)^2}
\end{align}$$

where we have relabeled one of the integrals and taken the zero temperature limit. This integral can now be calculated in various dimensions, the easiest one being in 1D and we don't have to worry about the dot product. This is then the classic tanh substitution integral resulting in arctanh. So using the logarithmic version of arctanh, our 1D result is,  

$$
    \chi_{1D}(k) = \frac{1}{4\pi q} \ln( \frac{q + 2k_F}{q - 2k_F} )
$$

and this has a singularity that diverges logarithmically at $$q=2k_F$$. The other dimensionalities still have issues at points of nesting but these are smoothed out and occur in the derivatives of the response function. Graphically, the response function shows the importance of the $$2k_F$$ point in one dimension.

<figure class="align-center">
<img src="../images/Peierls/Lindhart.png" style="width: 70%" class="align-center">
<figcaption>A diagram showing how a normalised response function (to allow comparison with different dimensionalities) varies with the wavevector of an external field applied to the system for various dimensions.</figcaption>
</figure>



### Response At Non-Zero Temperature

All these calculations so far have been at zero temperature, but we now know what wavevector will have the strongest response. So choosing $$k=2k_F$$, and therefore $$\epsilon(q) = -\epsilon(q + 2k_F)$$, and using the full Fermi-Dirac distribution we find that the Lindhart response function now becomes,

$$
    \chi(k = 2k_F,T) = \int d\epsilon N(\epsilon) \frac{\tanh(\beta\epsilon/2)}{2\epsilon}
$$

This integral, does have an asymptotic form that uses the Euler-Mascheroni constant but thats all confusing. I'll just quote the answer,

$$
    \chi(k = 2k_F,T) = n(\epsilon_F) \ln(\frac{1.14\Lambda}{k_BT})
$$

where $$\Lambda$$ is some high energy cutoff. The log is expected as for low temperature (large $$\beta$$), then $$\tanh(\beta) \sim 1$$ and there is an obvious logarithmic looking term. This also assumes that the density of states is a constant which isn't too bad for low temperature stuff that will be close to the Fermi surface. As a quick note, the susceptibility is sometimes defined with a negative sign in front.

### Mean Field Transition Temperature

So having seen that there is a singularity in the response function in 1D, we should look into when this diverging susceptibility will cause issues. To study this, we use some g-ology. This assumes that the external potential $$\phi_{ext}$$ will induce a density fluctuation which will in turn induce a  potential $$\phi_{ind}$$ with the following form, $$\phi_{ind}(k) = -g\rho_{ind}(k)$$. Therefore using the definition of the response function being from the total field,

$$ \begin{align}
    \rho_{ind}(k) &= \chi(k,T)\phi(k) = \chi (
    \phi_{ext}+ \phi_{ind}) \\
    &= \frac{\chi
    \phi_{ext}}{1 + g \chi}
    \end{align}
$$

This will give a singularity when the denominator is zero, for $$g<0$$. Therefore considering the temperature at which this happens, we can express the mean field temperature when a transition will occur.

$$
    1 + g n(\epsilon_F) \ln(
    \frac{1.14\epsilon_0}{k_BT_{MF}}) = 0 \implies k_BT_{MF} = 1.14\epsilon_0 \exp(\frac{-1}{gn(\epsilon_F)} )
$$

This concludes the very general overview of 1D response functions, showing that there is a transition from the normal metallic state to something new. To investigate more thoroughly what is happening, we will now be more specific and consider a specific system and define things.

## An Actual System

### Frölich Hamiltonian

To start with, we consider a 1D electron gas coupled to the underlying chain of ions through electron-phonon coupling, suppressing the spin index for the moment. We will start quite general and actually derive the appropriate Hamiltonian. Using second quantised operators to describe the electrons and phonons, the interaction between them uses the rigid ion approximation. This assumes that the ionic potential at any point is just the distance from the ion. The interaction therefore is the overlap between electron states $$k,k'$$ when it has been shifted by the potential produced by the underlying lattice. As we want to include phonons which are vibrations of the lattice we must go past the original Bloch calculation and considering a potential that can vary as,

$$
    \mathcal{H}_{el-ph} = \sum_{k,k',l} \langle k |V(r-l-u) |k' \rangle a^{\dagger}_k a_{k'} = \sum_{k',k,l} \exp(i(k'-k)(l+u))V_{k-k'} a^{\dagger}_k a_{k'}
$$

where $$l$$is the equilibrium lattice position and $$u$$ is the distortion and a lot of constants have been absorbed into $$V_{k'-k}$$. For small displacements, we can express the exponential as

$$
    e^{i(k-k')u} \approx 1 + i(k'-k)u = 1 + iN^{-1/2}(k'-k) \sum_q e^{iql}u_q,
$$

which gives two terms: one that just has the electrons interacting with the equilibrium lattice and the other than includes displacement effects. The interaction with the equilibrium lattice is what changes the free electrons into Bloch states (see nearly free electron approximation in condensed matter for the calculation when we only include this term), which opens up gaps near the Brillouin zone boundaries. This is the reason why the Peierls distortion was originally discovered for half filled bands as it is near the edge of the 'new' Brillouin zone!

We are, however, not interested in this term as we will consider energies not near the edge. Therefore our term becomes,

$$  \begin{align}
    \mathcal{H}_{el-ph} &\approx iN^{-1/2} \sum_{k,k',l,q} \exp(i(k'-k+q)l)(k'-k)u_qV_{k'-k}a^{\dagger}_k a_{k'}\\
    & = iN^{1/2} \sum_{k,k'} (k'-k)u_{k'-k}V_{k'-k}a^{\dagger}_k a_{k'}
    \end{align}
$$

Finally we can express the Fourier transform of the displacement operator with creation and annihilation operators and obtain the Frölich Hamiltonian

$$
    \mathcal{H}_{el-ph} = \sum_{k,q} g_q(b^{\dagger}_{-q} + b_q) a^{\dagger}_{k+q} a_{k}, \quad \quad g_q = i \sqrt{\frac{\hbar}{2M\omega_q}}|q|V_q
$$

### Equations Of Motion - Phonons

So now we have obtained the Hamiltonian and can look at how the normal mode coordinates change by finding the equations of motion in the usual second quantised way - through commutators with the Hamiltonian. Again to be clear this is for small amplitude displacements, and the equation of motion for our phonons will be,

$$
    \ddot{Q_q} = -\frac{1}{\hbar^2}[[Q_q, \mathcal{H}],\mathcal{H}] = -\omega^2_q Q_q - g\sqrt{\frac{2\omega_q}{M\hbar}}\rho_q \quad \quad \rho_q = \sum_k a^{\dagger}_{k+q} a_{k}.
$$

as here we are considering the full Hamiltonian which includes the phonons. We know that these phonons obey the usual phonon things and oscillate with $$\omega_q$$ so that can be put into the equation of motion and is the first term in the equation above. The second term describes the effects of the $$\mathcal{H}_{el-ph}$$ to the motion of the phonons. The term we are interested is the effective force from the lattice dynamics, which couples to the electron system. The potential associated with the ion is the prefactor in front of the $$\rho$$ multiplied by $$MQ_p$$ (as we want the potential not the force). Therefore using linear response, we can express the density fluctuation from the ionic potential $$\rho = \chi gQ_p\sqrt{2M\omega_g/\hbar}$$. Therefore we can substitute this into the equation,

$$
    Q_p = - \Big( \omega^2_q + \frac{2g^2\omega_q}{M\hbar}\chi(q,T) \Big) Q_p, \quad \quad \omega^2_{ren,q} = \omega^2_q + \frac{2g^2\omega_q}{M\hbar}\chi(q,T)
$$

Now having explored the form of the response function earlier, we know it will be most susceptible when $$q=2k_F$$ and we have an explicit form for this. Knowing that as $$\omega^2_{ren} \rightarrow 0$$, a phase transition will occur as a mode can be occupied with no energy cost associated to occupying it, a mean field transition temperature can be found. This will occur for,

$$
    \omega^2_{2k_F} = \frac{2g^2\omega_{2k_F}n(\epsilon_F)}{\hbar}\ln(\frac{1.14\epsilon_0}{k_BT_0}) \quad \quad  k_BT_0 = 1.14\epsilon_0 e^{-\hbar\omega_{2k_F}/g^2n(\epsilon_F)} = 1.14\epsilon_0 e^{-1/\lambda}
$$

where $$\lambda$$ is the dimensionless phonon-electron coupling constant. To see how this approaches zero, we can do a Taylor expansion around $$T_0$$, but the graph of the dispersion of the phonons is a lot clearer on how the frequency is renormalised.

<figure class="align-center">
<img src="../images/Peierls/renorm.png" style="width: 50%" class="align-center">
<figcaption>Showing the lowering of energy of the lattice modulation mode at twice the fermi wavevector as we approach the transition temperature[^3]. </figcaption>
</figure>



## Life After Transition

So what happens below this phase transition? The phonon state will become macroscopically occupied and condense, this means that there will be a frozen in lattice distortion of $$2k_F$$. This macroscopic occupation means that the expectation value of $$\langle b^{\dagger}_{2k_F} \rangle$$ will be nonzero, so removing or adding a particle to the mode will not affect the behaviour. So defining the parameter as

$$
    |\Delta|e^{i\phi} = g( \langle b^{\dagger}_{-2k_F}\rangle  + \langle b_{2k_F}\rangle)
$$

we can then reformulate the problem in terms of this order parameter. Due to there only being one mode occupied (up to fluctuations) the average displacement can be calculated. The interesting result is that there is a periodic modulation of the displacement as we move along the chain.

$$
    \langle u(x) \rangle = A\sum_q (b_q + b_{-q})e^{iqx} = A' \cos(2k_Fx + \phi)
$$

This is the reason why the state below this transition is often called a charge density wave, and why the Peierls transition results in a doubling of the periodicity due the the half filling of the band, which makes $$k_F = a$$.

Now to turn our attention to the electronic part, we can describe the problem using this order parameter

$$
    \mathcal{H}_{el} = \sum_k \epsilon_k a^{\dagger}_k a_k + |\Delta|e^{i\phi} a^{\dagger}_{k+2k_F}a_k + |\Delta|e^{-i\phi} a^{\dagger}_{k-2k_F}a_k
$$

Now to simplify matters, we will only consider states near the Fermi level. States near $$k_F$$ are denoted $$c_{R,q}$$ and ones near $$-k_F$$ are labelled $$c_{L}$$, and the spectrum is linearised so $$\epsilon(q) = \nu_F q$$ for $$q=k-k_F$$ for right movers and $$\epsilon(q) = -\nu_Fq$$. Considering the sums that involve deltas separately, we can change the index to make it clearer

$$
    \sum_k |\Delta|e^{i\phi} a^{\dagger}_{k+2k_F}a_k = \sum_k |\Delta|e^{i\phi} a^{\dagger}_{k+k_F}a_{k-k_F} = \sum_k |\Delta|e^{i\phi} a^{\dagger}_{R,k}a_{L,k}
$$

This assumption is only justified if,  

$$ | \epsilon_k - \epsilon_F| << \epsilon_F $$

and so the only relevant $$k$$ that we take into account are near $$k_F$$. This is how we introduce the final step and replace the sum over $$k$$ with a sum over $$q$$ this will introduce an overall constant $$\mu$$ to the energy and take into account that we are now considering fluctuations about a filled system up to $$k_F$$. Therefore we can now express the Hamiltonian as,

$$
    \mathcal{H}_{el} = \sum_q \nu_F q (a^{\dagger}_{R,q}a_{R,q} - a^{\dagger}_{L,q}a_{L,q}) + \Delta a^{\dagger}_{R,q}a_{L,q} + \Delta^* a^{\dagger}_{L,q}a_{R,q} - \mu
$$

This Hamiltonian is now ripe for diagonalisation. The new spectrum can be found from the eigenvalue problem,

$$
    \begin{bmatrix}
     \epsilon_q  & \Delta \\
     \Delta^* & -\epsilon_q \\
    \end{bmatrix}
    \begin{bmatrix}
    u_q \\
    v_q
    \end{bmatrix}
    =    \begin{bmatrix}
     E_q & 0 \\
     0 & -E_q \\
    \end{bmatrix}
    \begin{bmatrix}
    u_q \\
    v_q
    \end{bmatrix}    
$$

which gives the new dispersion of,

$$
    E_q = \epsilon_F \pm\sqrt{\epsilon_q^2 + |\Delta|^2}
$$

Finding the density of states expression allows us to find out what sign should go where. To calculate this, we assume that the total number of states stays the same and that the normal density of states is approximately a constant.

$$
    N_{CDW} dE = N_e d\epsilon, \quad \quad \frac{N_{CDW}}{N_e} = \begin{cases}
       0, \qquad \qquad \quad \quad |E| < |\Delta| \ \ \ \ \\
        E/\sqrt{E^2 - \Delta^2}, \quad |E| > |\Delta|
    \end{cases}
$$

This allows us to see that the density of states diverges as $$\pm E \rightarrow \Delta$$. A diverging density of states means that the dispersion must be flat, and if $$E$$ is defined around the Fermi energy this means that the dispersion must look like,

<figure class="align-center">
<img src="../images/Peierls/Dispersion.png" style="width: 70%" class="align-center">
<figcaption>Showing how the electronic dispersion splits and how the density of states can go to zero. </figcaption>
</figure>


Now we are at a point were we can explicitly calculate the electronic energy by summing over all the states, $$\sum_k E_k$$, and then changing this into an integral and performing the integral

$$ \begin{align}
    E_{el} &= \int d\epsilon\sqrt{\epsilon^2 + \Delta^2} = \Big[ \frac{1}{2}\epsilon\sqrt{\epsilon + \Delta^2} + \frac{1}{2}arcsinh(\epsilon/\Delta) \Big]^{\epsilon_F}_0 \\
    &= \epsilon_F\sqrt{\epsilon^2_F + \Delta^2} + \Delta^2 \ln(\frac{\epsilon+ \sqrt{\epsilon^2_F - \Delta^2}}{\Delta})
    \end{align}
$$

This however needs to be contrasted with the energy from the increase in elastic energy of the lattice. This can be found from

$$
    E_{latt} = \frac{N}{2}M\omega^2_{2k_f}\langle u(x) \rangle^2 = \frac{\Delta^2 n(\epsilon_F)}{\lambda}
$$

Here we see that it is the $$-\Delta^2\ln(\Delta/\epsilon_F)$$ term that grows faster than the lattice energy's $$\Delta^2$$, so the charge density wave has a lower energy than the normal metallic state. The value of the gap can be found through finding the total energy (ie electron + lattice) and then minimising it with respect to $$\Delta$$.

Finally, the feature that gives this state its name - the charge density wave. To find this we understand that the ground state is now the ground state of the transformed operators filled up to the Fermi level. This was skipped over as finding the operators means carrying out the Bogoluibov transformation explicitly so I will just state them.

$$ \begin{align}
    |\phi_0 \rangle &= \prod_{|k|<k_F} \gamma^{\dagger}_{1,k}\gamma^{\dagger}_{2,k}|0 \rangle\\
    &= \prod_{|k|<k_F} (U_k e^{i\phi/2}a^{\dagger}_{R,k} - V_k e^{-i\phi/2}a^{\dagger}_{L,k})(V_k e^{i\phi/2}a^{\dagger}_{R,k} + U_k e^{-i\phi/2}a^{\dagger}_{L,k}
    \end{align} $$

So when we calculate the electronic density

$$
\rho(x) = \langle\phi_0|\psi^{\dagger}(x)\psi(x)|\phi_0\rangle
$$,

we can find out how the charge varies in space for the ground state. Here $$\psi(x) = \sum_k a_{R,k}e^{ik_Fx} + a_{L,k}e^{-ik_Fx}$$, and actually substituting in will give the charge density of,

$$
    \rho(x) = \rho_0 \Big( 1 + \frac{\Delta}{\nu_Fk_F\lambda}\cos(2k_Fx + \phi)  \Big)
$$

Therefore we have managed to show the two most distinctive features of the charge density wave phase - periodic modulation of charge and the lattice. This should be compared to the normal metallic state where the electron density is a constant and the lattice is all equally spaced. To sum it up in a picture[^3],

<figure class="align-center">
<img src="../images/Peierls/Comparison.png" style="width: 70%" class="align-center">
<figcaption>Comparing the electric spacial variation, the lattice spacing and the electronic dispersion in the normal phase vs the charge density wave state.</figcaption>
</figure>



## Competing Instabilities - This Town Isn't Big Enough For The Two Of Us

As a final note about this analysis shown above, we have shown that the susceptibility of a 1D electron gas diverges at a certain wavevector and formulated how it diverges at a non-zero temperature. We then found a temperature at which this diverging susceptibility causes problems with the induced density of electrons is infinitely changed by an external field. Having done this, an actual system was considered and shown to be described by the Fròlich Hamiltonian and the equations of motion for the lattice found. This showed that the energy cost of occupying a certain phonon mode becomes zero and so this mode will become macroscopically occupied and a temperature at which this occurs was found.

The effects of having this mode macroscopically occupied were then considered next and this was shown to lead to the periodic variation in space of the lattice sites and a periodically varying in space electronic density. However all of this assumes that there is only one of these modes (ie phonons oscillating at $$q=2k_F$$) that has a zero energy cost. But in reality there are others and these instabilities compete with one another. This goes back to the introduction where it was say that they expected superconductivity in certain materials but they become an insulator instead - it is due to the instability associated with superconductivity and the Peierls one competing.

To illustrate this, let's consider a 1D metal, with two Fermi points at $$\pm k_F$$. After linearising the spectrum around these two points, the system will be chiral with the possibility of holes and electrons having being a right or left mover. Including spin degrees of freedom, this leads to 4 different types of pair that can form,

<figure class="align-center">
<img src="../images/Peierls/table.png" style="width: 70%" class="align-center">
</figure>




The states associated with pair formation of the Cooper channel are the usual singlet or triplet superconducting states that develop from interactions with no momentum. The states that form from interactions with $$2k_F$$ are charge and spin density waves. To determine the most relevant type of pairing, an RG analysis is often performed. Parquet diagrams was another technique to take into account competing instabilities.

The reason for stressing the similarity between the superconducting state and the state from the Peierls instability is that a very similar analysis works for both states, if you have seen the equations that describe superconductivity you will notice that they are very similar to ones derived here. Introducing a complex order parameter allows us to capture most of the physics. Both states also break a symmetry, gauge symmetry in the superconducting case and translational symmetry in the density wave case.

Going through this was done to demonstrate how to use condensed matter techniques to calculate behaviour of states. Normally the derivation of the superconducting transition is shown, but the Peierls instability gives another arena in which to deploy the same techniques and represents a phase that can be found in materials.



## Resources

A lot of this work comes from Gruner's density waves in solids[^4]. There are however a lot of useful resources. A great easy one that is a good introduction is the following link,

<a href="http://galileo.phys.virginia.edu/classes/752.mf1i.spring03/PeierlsTrans.htm">http://galileo.phys.virginia.edu/classes/752.mf1i.spring03/PeierlsTrans.htm</a>

which treats the problem in a more 3rd year undergraduate level. A serious intro to Lindhart stuff that looks at the diagrams produced but is quite pedagodical [^5]

[^1]: Lindhart Function of a d-dimensional Fermi Gas, Bogdan Mihaila, <a href="https://arxiv.org/abs/1111.5337">arXiv:1111.5337</a>

[^2]: Condensed Matter Field Theory, Altland & Simons

[^3]: Electronic crystals: an experimental overview, P. Monceau, <a href="https://arxiv.org/abs/1307.0929v1">arXiv:1307.0929</a>



[^4]: Density Waves in Solds, Grüner

[^5]: The Lindhard Function and the Teaching of Solid State Physics, Smith, 1983 Phys. Scr. 28 287
