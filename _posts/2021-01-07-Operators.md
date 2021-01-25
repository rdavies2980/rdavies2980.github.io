---
title: "Solving without translational invariance - Operators"
date: 2021-01-07
categories: [Maths Heavy, Techniques]
tags: [Boundary Conditions, Operators]
excerpt: "Dealing with localised terms in the Hamiltonian by stitching operators"
mathjax: "true"
---

In the previous blog post, a way to stitch together Green's functions to get an overall non-homogeneous result was explored. The thing that broke translational invariance in that case was a change in the parameters of the system between two different constant values. This is obviously not the only way in which we can break this symmetry.

The way that will be looked into here is due to terms in the Hamiltonian of our system being local. The overall technique remains the same, solving either side and then gluing the pieces together. This time, however, instead of performing this to the Green's function we will glue operators. There are many parallels between the two techniques though!

In fact the technique that will be explored shares a lot of similarities with the simpler quantum mechanics problem of a particle with a potential barrier. Through application of the conditions of continuity of the wavefunction and its derivatives we can relate the coefficients of the wavefunction. The generalisation of this to a full field theory perspective is interesting as again it now requires us to deal with a situation without full translational symmetry - meaning the usual approach must be altered slightly.

This example is taken from the notes on refermionisation in my Egger-Grabert 1998 paper, although Chamon, Freed, and Wen's 1996 paper is a lot more clear.


## The Hamiltonian

So we introduce our Hamiltonian with no context

$$\begin{equation}
    H = \int dx \psi^{\dagger}\partial_x \psi + V(c + c^{\dagger})(\psi(0) + \psi^{\dagger}(0))
\end{equation}$$

The kinetic term has that particular form as it is a sum over modes with a linear dispersion (thats been Fourier transformed back). There is an infinitely thin barrier at the origin that separates two regions in which the system is non-interacting. Interestingly because this comes from a refermionisation there is a Majorana mode from $$c + c^{\dagger}$$ (which can be seen to be equal it Hermitian conjugate and therefore is its own antiparticle) meant to ensure that the combination in the Hamiltonian behaves in a fermionic manner. This is because $$\psi$$ is actually the exponential of a bosonic field and can therefore cannot possess fermionic statistics.

So after all these caveats about what the system is, we now just have a scattering problem which can be solved in a variety of ways. Here we will find the equations of motion for the system, where the majorana mode has been renamed $$f$$

$$\begin{equation}
    -i\partial_t \phi = [H, \phi] = i\partial_x \phi + Vf\delta(x), \quad \quad -i\partial_t \phi^{\dagger} = [H, \phi] = i\partial_x \phi^{\dagger} - Vf\delta(x),
\end{equation}$$

and the time dependence of the Majorana mode must also be found and solved for,

$$\begin{equation}
    -i\partial_t f = [H,f] = V(\psi(0) - \psi^{\dagger}(0))
\end{equation}$$

### Solving the individual pieces

Away from $$x=0$$ the field can be found and solved for as it must satisfy the equation $$(i\partial_t + i\partial_x)\psi = 0$$, with the form of $$\psi$$ being able to be found by taking the Fourier transform into frequency space.

$$ \sum_{\omega} e^{i\omega t} (\omega + i\partial_x)A_{\omega}(x) = 0$$

As this is true for all $$\omega$$ we can see that $$-\omega A_{\omega}(x) = i\partial_xA_{\omega}(x)$$. This can be solved to get $$A_{\omega}(x) = a_{\omega}e^{i\omega x}$$.

This must can be different either side of $$x=0$$ so in general our solution will be,


$$\begin{equation}
    \psi(x,t) = \frac{1}{L}\sum_{\omega} e^{i\omega(t -x)} \left\{
                \begin{array}{ll}
                  a_{\omega}, \quad (x<0)\\
                  b_{\omega}, \quad (x>0)\\
                \end{array} = \frac{1}{L}\sum_k e^{i\omega(t -x)} \ ( \Theta(-x)a_{\omega} + \Theta(x)b_{\omega})
              \right.
\end{equation}$$

### Joining the parts together

To find the boundary condition to join these two solutions together we must solve for $$f$$ which involves defining $$\psi(0)$$. This must contain parts from our operators either side of our discontinuity and to ensure that our definition of $$\psi(0)$$ commutes with its Hermitian conjugate to give a delta function (not 4 times the delta function or whatever). We define $$\psi(0) = (\psi(0^+) + \psi(0^-))/2$$, as $$\{a_{\omega},b^{\dagger}_{\omega}\}=1$$ in addition to the more obvious commutation relations - hence the $$1/2$$. Therefore solving for $$f$$ with this definition we can find that,

$$\begin{equation}
    f_{\omega} = \frac{V}{2\omega}(\psi_{\omega}(0) - \psi_{\omega}^{\dagger}(0)) =  \frac{V}{2\omega}(a_{\omega} + b_{\omega} - a^{\dagger}_{-\omega} - b^{\dagger}_{-\omega})
\end{equation}$$

The $$-\omega$$ arises from making sure that the exponentials in our definition of the Fourier series are the same for the operator and its conjugate. Now we plug back into the equations of motion, splitting the full solution up into $$\psi_L(x,t) = \frac{1}{L} \sum_{\omega} e^{i\omega(t- x)} a_{\omega}$$ and $$\psi_R$$ respectively, joined together by a theta function. This gives,

$$\begin{equation}
    (i\partial_t + i\partial_x)(\psi_L\Theta(-x) + \psi_R\Theta(x)) = -Vf\delta(x)
\end{equation}$$

Expanding out and differentiating the step functions gives

$$\begin{equation}
    \Theta(-x)(i\partial_t + i\partial_x)\psi_L + \Theta(x)(i\partial_t + i\partial_x)\psi_R + i\psi_L\partial_x\Theta(-x) + i\psi_R\partial_x\Theta(x) =  -Vf\delta(x)
\end{equation}$$

From the defining differential equation for $$\psi$$, we can see that the first two terms will be zero to give.


$$\begin{equation}
    i(\psi_R - \psi_L)\delta(x) = -2Vf(x)\delta(x)
\end{equation}$$

therefore we can equate the two coefficients of the delta function. For the mathematicians, everything is secretly under an integral so this process actually makes sense. Finally we take the Fourier transform of our result to get a relation between $$a_{\omega}, b_{\omega}, a^{\dagger}_{\omega}, b^{\dagger}_{\omega}$$,

$$\begin{equation}
    i(b_{\omega} - a_{\omega}) = -\frac{V^2}{2\omega}(a_{\omega} + b_{\omega} - a^{\dagger}_{-\omega} - b^{\dagger}_{-\omega})
\end{equation}$$

and the procedure can be repeated on the equation of motion for the conjugate $$\psi^{\dagger}$$.

$$\begin{equation}
    i(b^{\dagger}_{-\omega} - a^{-\dagger}_{\omega}) = \frac{V^2}{2\omega}(a_{\omega} + b_{\omega} - a^{\dagger}_{-\omega} - b^{-\dagger}_{\omega})
\end{equation}$$

This gives two equations from which we can add to find an expression for $$b^{\dagger}_{\omega}$$. Substituting in and performing the trick of adding and subtracting 1 in the from of $$i\omega +V^2/i\omega +V^2$$ to obtain a relations between the scattering components,

$$\begin{equation}
    2b_{\omega} = ( 1 + \frac{i\omega- V^2}{i\omega + V^2})a_{\omega} + ( 1 - \frac{i\omega - V^2}{i\omega+ V^2})a^{-\dagger}_k
\end{equation}$$

### Small sprinkle of analysis

So what we have done here is relate the operators either side of a barrier - the typical quantum mechanical problem in the field theoretic way. Solving this problem in QM (see this stack exchange - well up to a minus sign[^1]) is a little easier and follows the previous blog post by requiring a discontinuity in the derivative. This problem just requires a little more care to derive.

Just to close this out, I'll mention some ways in which this relationship is useful and what it can tell us.

As $$b_{\omega}$$ creates a particle moving to the left from the right hand side, we can see that the difference between the coefficients of the operators on the left hand side of the discontinuity is the phase shift caused by scattering. A particle incident on the barrier will be reflected with a shift of its coefficient. We can summarise the shift as

$$
e^{i\alpha_{\omega}} = e^{-i\alpha_{\omega}} = \frac{i\omega - V^2}{i\omega + V^2}
$$

This can be picked out from the form of our relation and this phase shift is the same as in the quantum mechanical problem. As another point of what we can do with this relation is that expectation values of $$\langle b^{\dagger}b \rangle$$ can be evaluated in terms of the other operators (and vice versa) which allows us to solve some problems.

So the one that appears in the Egger-Grabert notes (which this point is lifted from) has boundary conditions of our problem expressed in terms of $$\langle b^{\dagger}b \rangle, \langle a^{\dagger}a \rangle$$. This relation is what allows us to relate the two to actually solve the effect of the boundaries on our system.


[^1]: <a href="https://physics.stackexchange.com/questions/441616/scattering-by-a-delta-function-well-in-1d">https://physics.stackexchange.com/questions/441616/scattering-by-a-delta-function-well-in-1d</a>
