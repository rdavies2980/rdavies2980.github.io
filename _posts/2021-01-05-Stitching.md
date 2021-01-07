---
title: "Solving without translational invariance - Green's functions"
date: 2021-01-05
tags: [Maths Heavy, Techniques]
excerpt: "A method for stitching together a patchwork of Green's functions"
mathjax: "true"
---

While I was attempting to rederive some results from a classic 1D transport paper, I got stuck trying to solve for the Green's function of the system. The main problem wasn't a horrendous integral or lack of convergence, but that in the system I was considering there was *no translational invariance*. The whole usual method of Fourier transforming our Green's function into a diagonal basis, inverting it and transforming back could not be used. Our lack of translational invariance means that the Fourier transform no longer neatly decouples our problem into a diagonal basis.

To be clearer, the usual procedure is to start with our generic Green's function, $$G(x,x')$$, which if we have translational invariance will be a function of the difference of $$x$$ and $$x'$$ alone, $$G(x-x')$$. This reduction of the number of parameters needed means that the Fourier transform only requires one $$k$$ to get our answer, $$\tilde{G}(k)$$, into a form that we can easily invert. Without translational invariance our Green's function will depend on $$k$$ and $$k'$$ in general.

It isn't often that we lack translational invariance in physics due to the fact that it is what makes many calculations possible, however there is a neat way to solve the issue in certain cases (otherwise I wouldn't be writing this at all!). Content here has been lifted from my research into Maslov and Stone's 95 paper, full notes of which may appear at some point.

This short explanation will focus on solving the issue when we are focused on finding the Green's function to describe the system. Another entry will show a different way in which we can tackle another problem that directly deals with the operators themselves.

## Green's Function method

So simply quoting what the mathematical problem is without much context

$$
\begin{equation}
    \Bigg[-\partial_x \frac{v(x)}{K(x)} \partial_x + \frac{\omega^2}{v(x)K(x)} \Bigg] G_{\omega}(x,x') = \delta(x-x')
\end{equation}
$$

where the parameters $$v(x), K(x)$$ are constant when $$x<0, x>L$$ and have a different constant value when $$0 \le x \le L$$. We will call this inside region a wire throughout. Here we see that if we had translational invariance (parameters constant everywhere) we could Fourier transform to get a familiar looking Green's function of $$G(k,\omega) = 1/(ak^2 +b\omega^2)$$ for constants $$a,b$$. Through complex analysis this can be transformed back, but we cannot rely on that method now.

### Conditions on the Green's Function

Now we will look at what the properties the Green's function has, by investigating the defining equation. Because it contains no derivatives of delta functions, we see that the Green's function must be *continuous* everywhere as if it contains any discontinuities then taking the second spatial derivative of this will produce derivatives of the delta function. Therefore at all possible problem points ($$x=0,x=x',x=L$$) the Green's function will be continuous. To see the effect of derivatives we integrate in a thin strip of size $$2\delta$$ around a certain point $$y= \{ 0,x',L\}$$,

$$\begin{equation}
     \int_{y-\delta}^{y+\delta} dx \Bigg[ -\partial_x \frac{v}{K} \partial_x + \frac{\omega^2}{vK} \Bigg] G_{\omega'}(x,x') = \int_{y-\delta}^{y+\delta}  \delta(x-x')
\end{equation}$$

We can see that the RHS of the equation will be zero unless $$y=x'$$ and then it will equal 1 even as we let $$\delta \rightarrow0$$. Turning our attention to the LHS, we see that the factor $$(\omega^2/vK) G$$ will give zero as we let $$\delta \rightarrow0$$ due to the continuity of everything in the integrand. The terms with the spatial derivatives however will give a result of

$$\begin{equation}
    \Big[ \frac{v(x)}{K(x)}\partial_x G(x,x') \Big]^{y+0}_{y-0} = \left\{
                \begin{array}{ll}
                  0 \quad \text{if } y=0,L\\
                  1 \quad \text{if } y=x'\\
                \end{array}
              \right.
\end{equation}$$

These are all our conditions, so we should now look at what the solutions at various parts are.

### Finding our pieces

We can solve the problem away from the $$x=x'$$ point, this can be seen to give an exponential dependence (with terms that diverge being set to zero).

$$\begin{equation}
    G_0^L = Ae^{\omega x/v}, \quad G_W^L = Be^{\omega x/v} + Ce^{-\omega x/v}, \quad G_1^L = De^{-\omega x/v}
\end{equation}$$

where $$G_0$$ is the region to the left of the wire, $$G_W$$ is in the wire and $$G_1$$ is to the right of the wire. The $$L$$ notation is to denote that these are left of the point $$x'$$. To the right of this point we will have similar solutions with different coefficients which will be notated with primes. To simplify the more complicated problem, we will only consider that $$0<x'<L$$ which will reduce the complication of stitching the solutions together. So we need to glue together $$G_0^L, G_W^L, G_W^R, G_1^R$$ in accordance with the boundary conditions.

To summarise a bit, these boundary conditions mean that (as we have fixed $$x'$$ to be within the wire) that we need to make the $$G_0^L, G_W^L$$ boundary such that the function is continuous and to the same for $$G_W^R, G_1^R$$. Then the gluing together of $$G^L$$ and $$G^R$$ parts is done by matching the Green's function with a unit step in the derivative.

### Gluing together

Up to now, I have repeatedly talked about gluing solutions together - but what is mathematically meant by this? Essentially we will use two step functions, $$\Theta(x)$$, to ensure that the solutions are non-zero and zero respectively in the correct sections. So for the continuous boundary we will have,

$$
G^L(x<x') = A G^L_0(x)\Theta(-x) + B G^L_W(x)\Theta(x)
$$

where we can see that action of the step functions kicking in at $$x=0$$. Derivatives of this can now be taken, but any worrisome delta function terms that arise from differentiating the step function are killed off by one of the step functions having a negative sign and the continuity requirement meaning that $$A G^L_0(0) = BG^L_W(0)$$. For the gluing over the continuous boundaries ($$x=0,L$$), we set the two parts of the functions and their derivatives to be equal at the boundary - much like in the standard QM problem except with the prefactor of the derivatives being different on either side. This allows us to relate the coefficients $$A$$ and $$B$$ to obtain an expression for $$G^L$$ (with the final constant being set by larger considerations of the system, normalisation and whatnot).

The boundary with the derivative step can be solved for in the same way - writing out using theta functions and then relating the coefficients. This time however, the delta function in the derivative will not  So generically we solve for a solution where the coefficients can depend on where $$x'$$ is set. This means $$G^L(x,x') = a(x')y_1(x)$$ and $$G^R(x,x') = b(x')y_2(x)$$ where $$y(x)$$ contains the exponential $$x$$ dependence of the Green's function. Relating the two for $$x=x'$$, using the conditions on our Green's function.

$$\begin{align}
    &G^L(x=x',x') = G^R(x=x',x') = a(x') y_1(x=x') = b(x') y_2(x=x'), \\
    & b y'_2 - a y'_1 = K(x=x')/v(x=x')
\end{align}$$

This notation is very ugly but it's important to be clear on the dependence of various things. This can be solved for $$a,b$$ (by just rearranging the above two equations) to give,

$$\begin{equation}
  b = \frac{K}{v}\frac{y_1}{y_1y'_2 - y_2y'_1} \Big\vert_{x=x'}, \ \quad a = \frac{K}{v}\frac{y_2}{y_1y'_2 - y_2y'_1} \Big\vert_{x=x'}
\end{equation}$$

which we can then use to get our full expression for the Green's function which can be checked to satisfy our original differential equation.

$$\begin{equation}
    G(x,x') = \frac{K}{v} \frac{1}{y_1 y'_2 - y_2y'_1}\Big\vert_{x=x'} \Big(\Theta(x'-x) y_1(x)y_2(x') + \Theta(x-x')y_2(x)y_1(x')\Big)
\end{equation}$$

where the prefactor that is evaluated at $$x=x'$$ is actually the inverse of the Wronskian of the two solutions evaluated at this point. I prefer to write it more explicitly. The generalisation to the $$y$$ representation of the exponential dependence does make this particular question a little harder to follow (because of the multiple different exponential parts hidden within) but was used to show the more general technique.

The prefactor of the above equation actually turns out to be constant so we can evaluate its value anywhere! To show this we consider the derivative of the prefactor,

$$
\frac{d}{dx}\Big(\frac{v}{K}(y_1 y'_2 - y_2y'_1)\Big) = \frac{d}{dx}\Big(\frac{v}{K} \Big)(y_1 y'_2 - y_2y'_1) + \frac{v}{K}(\underbrace{y'_1y'_2 - y'_2y'_1}_{0} + y_1y''_2 - y_2y''_1)$$

and then consider our defining equation for what $$y_1$$ and $$y_2$$ must satisfy (ie the Green's function differential equation away from the delta function spike)

$$
\begin{equation}
    \frac{\omega^2}{v(x)K(x)}y = \partial_x \frac{v(x)}{K(x)} \partial_xy  = \frac{d}{dx}\Big(\frac{v}{K} \Big)y' + \frac{v(x)}{K(x)}y''
\end{equation}
$$

Therefore the spatial derivative of the prefactor can be seen to be

$$
\text{Derivative of prefactor} = y_1\frac{\omega^2}{vK}y_2 - y_2\frac{\omega^2}{vK}y_1 = 0
$$

so the prefactor itself must be a constant as we vary space - so we have some translational invariance after all!

This technique is quite general and can be shown to be equivalent to the eigenvalue method. This technique is standard in mathematical treatments of solving differential equations, but often in physics our laser focus on eigenvalues means that this method of constructing Green's functions is overlooked!

So we have managed to stitch it all together and find our translationally variant Green's function!

There's good info on this same process at the following link:

<a href="http://www.damtp.cam.ac.uk/user/dbs26/1BMethods/GreensODE.pdf">http://www.damtp.cam.ac.uk/user/dbs26/1BMethods/GreensODE.pdf</a>
