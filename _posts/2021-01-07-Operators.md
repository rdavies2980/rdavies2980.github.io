---
title: "Solving without translational invariance - Operators"
date: 2021-01-06
tags: [Maths Heavy, Techniques]
excerpt: "Dealing with localised terms in the Hamiltonian with more glue"
mathjax: "true"
---

In the previous blog post, a way to stitch together Green's functions to get an overall non-homogeneous result was explored. The thing that broke translational invariance in that case was a change in the parameters of the system between two different constant values. This is obviously not the only way in which we can break this symmetry.

The way that will be looked into here is due to terms in the Hamiltonian of our system being local. The overall technique remains the same, solving either side and then gluing the pieces together. This time, however, instead of performing this to the Green's function we will glue operators. There are many parallels between the two techniques though!

In fact the technique that will be explored shares a lot of similarities with the simpler quantum mechanics problem of a particle with a potential barrier. Through application of the conditions of continuity of the wavefunction and its derivatives we can relate the coefficients of the wavefunction. The generalisation of this to a full field theory perspective is interesting as again it now requires us to deal with a situation without full translational symmetry - meaning the usual approach must be altered slightly. 

This example is taken from the notes on refermionisation in my Egger-Grabert 1998 paper, although Chamon, Freed, and Wen's 1996 paper is a lot more clear.


## The Hamiltonian

So we introduce our Hamiltonian with no context

$$\begin{equation}
    H = -\int dx \psi^{\dagger}\partial_x \psi + V(c + c^{\dagger})(\psi(0) + \psi^{\dagger}(0))
\end{equation}$$

The kinetic term has that particular form as it is a sum over modes with a linear dispersion (thats been Fourier transformed back). There is an infinitely thin barrier at the origin that separates two regions in which the system is non-interacting. Interestingly because this comes from a refermionisation there is a Majorana mode from $$c + c^{\dagger}$$ (which can be seen to be equal it Hermitian conjugate and therefore is its own antiparticle) meant to ensure that the combination in the Hamiltonian behaves in a fermionic manner. This is because $$\psi$$ is actually the exponential of a bosonic field and can therefore cannot possess fermionic statistics.

So after all these caveats about what the system is, we now just have a scattering problem which can be solved in a variety of ways. Here we will find the equations of motion for the system, where the majorana mode has been renamed $$f$$

$$\begin{equation}
    -i\partial_t \phi = [H, \phi] = i\partial_x \phi + Vf\delta(x), \quad \quad -i\partial_t \phi^{\dagger} = [H, \phi] = i\partial_x \phi^{\dagger} + Vf\delta(x),
\end{equation}$$

and the time dependence of the Majorana mode must also be found and solved for,

$$\begin{equation}
    -i\partial_t f = [H,f] = V(\psi(0) + \psi^{\dagger}(0))
\end{equation}$$

### Solving and joining the individual pieces

Away from $$x=0$$ the field can be found and solved for as it must satisfy the equation $$(i\partial_t + i\partial_x)\psi = 0$$, with the form of $$\psi$$ being able to be found by taking the Fourier transform. This must can be different either side of $$x=0$$ so in general our solution will be,

$$\begin{equation}
    \psi(x,t) = \frac{1}{L}\sum_k e^{ik(\nu t -x)} \left\{
                \begin{array}{ll}
                  a_k, \quad \quad (x<0)\\
                  b_k, \quad \quad (x>0)\\
                \end{array} = \frac{1}{L}\sum_k e^{ik(\nu t -x)} \ ( \Theta(-x)a_{k} + \Theta(x)b_k)
              \right.
\end{equation}$$

To find the boundary condition to join these two solutions together we must solve for $$f$$ which involves defining $$\psi(0)$$. To ensure commutation relations are satisfied (as $$\psi$$ is bosonic and $$f$$ makes the combination $$f\psi$$ fermionic) we define $$\psi(0) = (\psi(0^+) + \psi(0^-))/2$$. Therefore solving for $$f$$ with this definition we can find that,

$$\begin{equation}
    f_{\omega} = \frac{V}{\omega}(\psi_{\omega}(0) + \psi_{\omega}^{\dagger}(0)) =  \frac{V}{2\omega}(a_k + b_k + a^{\dagger}_k + b^{\dagger}_k)
\end{equation}$$

Now we plug back into the equations of motion, splitting it up into $$\psi_L(x,t) = \frac{1}{L} \sum_{k} e^{ik(\nu t- x)} a_k$$ and $$\psi_R$$ respectively, joined together by a theta function. This gives,

$$\begin{align}
    (i\partial_t + i\partial_x)(\psi_L\Theta(-x) + \psi_R\Theta(x)) &= 2Vf\delta(x)\\
    \Theta(-x)(i\partial_t + i\partial_x)\psi_L + \Theta(x)(i\partial_t + i\partial_x)\psi_R + i\psi_L\partial_x\Theta(-x) + i\psi_R\partial_x\Theta(x) &=  2Vf\delta(x) \\
    i(\psi_R - \psi_L)\delta(x) = 2Vf(x)\delta(x)
\end{align}$$

therefore we can equate the two coefficients of the delta function and take the Fourier transform to obtain,

$$\begin{equation}
    i(b_k - a_k) = -\frac{\hbar \nu \lambda_B}{2\omega}(a_k + b_k + a^{\dagger}_k + b^{\dagger}_k)
\end{equation}$$

and the procedure can be repeated on the equation of motion for the conjugate $$\psi^{\dagger}$$. This gives two equations from which we can eliminate $$b^{\dagger}_k$$ to obtain a relations between the scattering components,

$$\begin{equation}
    2b_k = ( 1 + \frac{i\hbar \nu k- \lambda_B}{i\hbar \nu k + \lambda_B})a_k + ( 1 - \frac{i\hbar \nu k- \lambda_B}{i\hbar \nu k + \lambda_B})a^{\dagger}_k
\end{equation}$$
