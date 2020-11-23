---
title: "Renormalisation Group"
permalink: "/RG/"
mathjax: "true"
toc: true
toc_label: "Contents"
toc_icon: "list"
toc_sticky: true
classes: single
excerpt: "These are notes on renormalsation "
author_profile: false
header:
  overlay_image: "../images/RGnotes.png"
  overlay_filter: "rgba(100,100,100,0.5)"

---

<a href="../assets/notes/Renormalisation_Group.pdf">Download PDF</a>


The renormalisation group is not machinery through which you can put in numbers and get out information. It is more a way of approaching a problem and therefore there is no systematic way to apply it to a general problem. There are even non-renormalisable theories for which these ideas can not even be applied! However, for equilibrium critical phenomenon (so phase transitions), there is a systematic way to formulate it. The main tool for finding the phase diagram  of a system now is the renormalisation group (RG) which through a joint development in statistical and particle physics became one of the great successes of 20th century physics.  So introducing the topic will come through exploring how phase transitions work.

## Phase transitions

### History And Some Scaling Ideas

Identifying where phase transitions occur, has always been crucial in understanding how materials work. From Ehrenfest's original classification using the discontinuities in the free energy to Landau's minimisation of free energy functionals, figuring out how such a wide range of transitions between phenomena can be unified required considerable theoretical effort.\\

The RG idea came about (in stats) from scaling theory, where in we attempt to simplify systems with a huge number of degrees of freedom that interact in a complex, possibly non-linear, fashion. The idea is to isolate the relevant variables for a particular length/time scale, and postulate scaling relationships between them for these various length scales. By continuity, we would connect up these regions and get a description at all scales - see the scaling theory of localisation for an example of this. But as a brief introduction of the way this sort of theory operates, we split a large sample into many blocks of size $L$. The crucial equations when considering the conductivity are


  $$  g(L) = \frac{G(L)}{2e^2/h} = \frac{\sigma_L L^{d-2}}{2e^2/h} \ \ when g(L) >> 1, \quad \quad g(L) \sim e^{-L} \ \  \textnormal{when }g(L) << 1
$$

where $g(L)$ is the dimensionless conductance, a parameter that is related to the conductance $G(L)$ and also how coupled a one block is to its neighbour (or equivalently disorder of the sample). The postulated scaling relationship is that the conductance of a block size $2L$ only depends on the block of size $L$ so $g(2L) = f(g(L))$ for some function. If $g(L)$ is larger than one, this means that the system is coupled to its neighbours and it conducts well and vice versa for when $g(L)$ is small. \\

When it is conducting well, we can use the normal equation for conductance in metals generalised to arbitrary dimension $d$ (this will probably be most familiar from the formula for that uses resisitivity of a sample to find its resistance $R = \rho L/A = \rho L/L^{d-1}$ with conductance being the inverse of this). When it conducts badly, it exponentially decays. Don't worry about how these are derived, the important thing we care about is the dependence on length which we express using whats known as a beta function $g \sim L^{\beta(g)}$.\\

Looking at the equations we see that when $d=1$ we will always have a negative exponent ($g \sim L^{\beta<0}$). So independently of what the value of conductance is for our original starting block, as we increase the length to be the size of our total sample the dimensionless conductance will get smaller and our total sample will conduct badly! \\

This is quite a deep result that we cannot have a good conductor in 1 dimension and it was extracted from simply finding $\beta$ and assuming that nothing funky happens when we connect up $g$ at its large and small values. There is a lot more than can be extracted from the 2 equations but this is the simplest result to see and gives a flavour of how through simplifying a complex system quite general statements can be found. \\

The appeal of RG techniques is that they allow us to extract the information about how quantities scale with each other (like scaling theory can) and where the boundaries of phases are (where scaling relationships become infinite in a continuous transition as is essentially the definition of a phase transition) as well as explaining the universality of different systems. We normally use it in physics to find the low energy behaviour or the long range behaviour as we care about what the total system is doing, not what the inner parts specifically doing. \\

The RG paradigm is often contrasted with mean field theory, which was found to be increasingly not in correspondence to experimental observations of the critical exponents (essentially the exponents of the scaling relationships which the main way of classifying how a transition occurs). The advantage of RG over mean field theory, is that more length scales are taken into account when we renormalise. Mean field theory neglects short scale fluctuations but the iterative nature of the renormalisation group allows fluctuations over many length scales to be included, which will be needed for strongly correlated systems near the critical point. However, mean field theory does allow investigation into the nature of phases away from the critical point which RG cannot give information about. \\

###Real Space RG - Block spins

 All renormalisation group studies have the idea of re-expressing the parameters that define a problem in terms of a simpler set of parameters but keeping the physical aspects that we are interested in the same. In critical phenomenon, it is the long range degrees of freedom that we are interested in so the process may be achieved by course grain-ing out the short distances involved in the problem. So to introduce the idea with more physical understanding, the real space renormalisation of spins on a square lattice will be looked at. \\

The process is called Block decimation, and was introduced by Kadanoff. The trick is to take a subsection of your system (like 9 blocks of a square) and represent these somehow with only one spin. A common choice is to decide by majority, if most of the spins are up, then the representative spin is up and vice versa. Finally by re-scaling the lengths we find that our system is described by the same equations only with different (renormalised) parameters. We have essentially simplified the more complex into a simpler one, but shunk it in the process so we need to stretch out the lattice so it resembles our original system. \\

Being explicit, if the partition function is the trace over various spin configurations $Z = \Tr_se^{-\mathcal{H}(s)}$ and a rule for assigning a new sign for 9 other spins $T(s'; s_1,s_2 \cdots s_9)$ then the reduced Hamiltonian is:

\begin{align}
    e^{-\mathcal{H}'(s')} &= \Tr_s \prod_{all \  blocks} T(s'; s_1,s_2 \cdots s_9)e^{-\mathcal{H}(s)}\\
    Z' = \Tr_{s'}e^{-\mathcal{H}'(s')}& = \Tr_se^{-\mathcal{H}(s)} = Z
\end{align}

This relies on the fact that for an Ising spin, in can be in one of two configurations (up or down - labelled by 0 or 1) so $Tr_{s'}T(s';s_i) = 1$ so summing over both spins gives (0 + 1) . Two points to note about this process is that it leaves the partition function and the long range correlations unaffected. This is the crucial feature of this process!  \\


After doing this process many times we are left with renormalisation group flows in a parameter space, and it is the study of these flows that is important. Being specific, lets say consider the 1D Ising Model, where we choose to let our rule be $T(s'; s_1, s_2, s_3) = \delta_{s',s_2}$ (so we choose the middle spin to represent a group a three spins) and our Hamiltonian is $\mathcal{H} = -K\sum_i s_is_{i+1}$ with $K$ containing a factor of $\beta$. Tracing out the end spins on 2 neighbouring blocks and using the relation $\exp(Ks_3s_4) = (\cosh K)(1 +  s_3s_4\tanh K)$ means we can express our new coupling constant:

\begin{equation}
    K' = \tanh^{-1}[\tanh(K)^3] \quad \implies x' = x^3 \textnormal{  where  } x = \tanh(K)
\end{equation}

As a note the dimensionful correlation length which describes the long distance physics must be the same, but considering that the underlying lattice spacing, $b$, has changed (by a factor of 3 in this case), we can show how the dimensionless correlation length transforms as:

\begin{equation}
    \xi(x') = b^{-1}\xi(x)
\end{equation}

Now lets looks at what this means!



###Understanding RG flows

Our $x$ variable can only vary between 0 and 1 so, we will iterate down to 0 unless we are at exactly 1 as cubing a number smaller than one results in a smaller number. Being at $x=0$ corresponds to zero $K$ which is proportional to $\beta=1/T$ so therefore the $x=0$ point corresponds to zero temperature. Therefore if our original system has a temperature that is non zero, it will iterate to infinite temperature. This is saying that the long wavelength degrees of freedom for our original Hamiltonian (as each iteration correponds to doing one block decimating procedure, essentially zooming out) are described by a the Ising Hamiltonian with infinite temperature which is a paramagnet!\\

\begin{figure}
    \centering
    \input{Rg1d}
    \caption{Showing how the RG equations flow in the 1D Ising case, with the arrows showing what direction the parameters are changing with each iteration of decimation.}
    \label{fig:my_label}
\end{figure}

The behaviour at these two end points is already worked out (by solving the Hamiltonian) but makes sense that at infinite temperatures there will be a lot of energy to excite the spins and each spin will not care about its neighbours position and will all be up or down randomly (paramagnet) and at zero temperature whereas at zero temperature it will try to minimise the energy so is ferromagnetic. However in higher dimensions there may be more interesting things happening. Fixed points indicate a region where the system does not care what length scale it is viewed at, therefore the correlation length will be either zero or infinite as it cannot change with an iteration. An unstable fixed point separating flows to different regimes indicates a phase transition.\\

Understanding renormalisation group flows relies on knowledge of dynamics and its phase space ideas. In this case however it is a flow in parameter space. Interpretation of the parameters must also be understood, normally there is a temperature dependence so a small value of the parameter means a large temperature for example. \\

So what does it mean for a parameter to flow to a value? So this process will start at a particular value of parameter corresponding to the actual system we are considering. Multiple iterations of the renormalisation group will change this parameter and the scale at which the system is being considered (ie the short wavelength behaviour will have been integrated out). Therefore if the parameter flows to a certain value, that means the long wavelength behaviour of the system will be characterised by a system with those particular parameters.  \\

Another thing to note that occurs in higher dimensions is the appearance of other couplings when renormalisation is undertaken. For example summing over a corner spin in 2D, will introduce a next nearest neighbour coupling between the corners of two blocks. In general, all neighbour couplings will now appear and the 1D example is a massive oversimplification. But it turns out that the fixed point of the transformation, which now lives in the space of all possible couplings, control the critical behaviour. \\

The RG flow will not have any singularities, with the singularities arising from iterating the RG flow for more and more iterations, like a ball taking infinite time to roll to the top of hill in classical mechanics.


## General Theory

This section follows Cardy's \textit{Scaling and Renormalisation in Statistical Physics} Book \cite{cardy1996scaling}.\\

Thinking of the couplings in the Hamiltonian as forming a vector $ \{K \}$, and the renormalisation group transformation as acting in the space of all possible couplings: $\{K'\} = \mathcal{R} \{K\}$, with $\mathcal{R}$ being dependent on the length rescaling parameter. This allows very general ideas to be expressed. The size of this space might be reduced through symmetries or at least become block diagonal. \\

Assuming there is a fixed point at $$K^*\$$, it is differentiable there. Around the fixed point, we can linearise the change in the couplings:

 \begin{equation}
     K_{a}' - K_a \sim \sum_b T_{ab}(K_b -K_{b}^*), \quad \quad T_{ab} = \pdv{ K_a'}{K_b} \Big|_{K=K^*}
 \end{equation}

The matrix $T$ can then be examined as having left eigenvectors such that $\sum_a \phi^i_aT_{ab} = \lambda^i \phi^i_b$, and scaling variables that are linear combinations of the deviations from the fixed point $u_i \equiv \sum_a \phi^i_a (K_a - K_a^*)$. \\

The reason to define these scaling variables is that they transform multiplicatively near the fixed point ($u'_i = \lambda^i u_i$). So if we define the renormalisation group eigenvalues as $\lambda^i = b^{y_i}$, then the sign of the exponent will tell us if the deviations are growing or shrinking in size. If $y_i > 0$, then the scaling variable is called relevant and the mapping forces it away from the fixed point. Correspondingly if it is less than zero then the scaling variable is called irrelevant. If it is equal to zero then $u_i$ is called marginal, which means more information is needed.\\

So if there was $n$ relevant eigenvalues and $n'$ dimensions in this parameter space, there will be $n'-n$ dimensional hypersurface of points that are attracted to the critical point and continuity means this extends out a finite amount. On this surface, the long distance behaviour is controlled by the fixed point. The universality of the various classes therefore correspond to different fixed points.\\

###Extracting Information

However, we need to find out what the fixed point says about the system. To be concrete, the Ising model will be used. The critical point occurs as zero field and there are only two parameters we can vary. This means that there are two subspaces (even and odd under the symmetry $s \rightarrow -s$) with a fixed point in each. The even scaling variable is the thermal one $u_t$, and the odd is the magnetic scaling variable, $u_h$. \\

Although there can be infinite irrelevant variables, it will only take finite number of mappings until the theory is in the vicinity of a fixed point. The values of the scaling fields will therefore depend analytically on deviations of the original theory from the fixed point, as the mapping is analytic. As they must vanish for $u=t=0$ and by symmetry, they have the form:

$$u_t = t/t_0 +O(t^2,h^2), \quad \quad u_h = h/h_0 + O(th)$$

where $h_0, t_0$ are non-universal constants, but this means that close to the critical point we take take them to be proportional. The renormalisation group preserves the partition function. Consider the reduced free energy per site $f(\{K\}) \equiv N^{-1} \ln(z)$, and this will get a constant term added with each iteration:

$$Nf\{K\} = Ng\{K\} - N'f\{K'\}$$

with $N' = b^{-d}N$ being the new total number of blocks. Unlike the correlation length, the free energy transforms inhomogeneously. The $g\{K\}$ term comes from summing over the short wavelength degrees of freedom, so should still be analytic in the $K$'s at the critical point. So dropping that term because the singular part of the function is what will cause the transition, and writing the function in terms of the scaling variables:

$$f_s(u_t,u_h) = b^{-d}f_s(b^{y_t}u_t,b^{y_h}u_h) = b^{-nd}f_s(b^{ny_t}u_t,b^{ny_h}u_h)$$

Note that it is from this relation that Widom stated and correctly postulated the scaling relationship for free energy. Hence why things derived from this are called scaling relations. Kadanoff's contribution was to explain what the scale factor was related to - the block decimation length. This will moves us away from where the approximation is valid, so we will halt the iteration at point $u_{t0}$. Solving the equation for $n$ gives:

$$f_s(t,h) = \abs{t/t_0}^{d/y_t} \Phi \Big( \frac{h/h_0}{\abs{t/t_0}^{y_h/y_t}} \Big)$$

where $\Phi$ is the scaling function. The only dependence on the particular system is through the scale factors $t_0$ and $h_0$. From this form of the free energy, we can differentiate and find the various critical exponents in terms of $y_t$ and $y_h$, with a scaling relation between the critical exponents being possible to find. These relations will hold for any universality class with one relevant thermal eigenvalue and a symmetry breaking field. \\

The rescaling factor $b$ enters these calculations so the question as whether there is dependence on the results to our choice is a valid question. For uncontrolled approximations, the approximate values of the exponents show weak dependence on $b$. Therefore considering infinitesimal transformations where $b = 1 + \delta l $. The renormalisation group equation are then differential equations and are called beta functions. In block spins however, the requirement to have it look like the lattice on all scales mean this cannot be done - one of the reasons this renormalisation is uncontrolled!

### Irrelevant Eigenvalues

For an irrelevant scaling variable $u_3$, we can still assume analytic dependence on $t$ and $h$, but cannot assume that the constant is equal to zero so close to the critical point we can say that $u_3 \approx u_0$ which will be a non-universal constant. Repeating the calculation, in the previous section the form of the scaling can be found. Expanding out in a Taylor series in $u_0\abs{t}^{\abs{y_3}/y_t}$ means we can see that this gives rise to corrections to scaling terms.

This is what causes the requirement for high quality data in this area, having to be super close to the critical point to extract the critical exponents. However, this assumes that the Taylor expansion exists, and this may not always be true. In this case it is called a dangerously irrelevant variable.

### Correlations

This is as much as we can extract from the free energy, the next thing we should turn our attention to is how correlations scale. This relies on the previous fact that the renormalisation group transformation preserves the long wavelength degrees of freedom. It was in including these correlations that allowed Kadanoff to go further than Widom and extract even more exponents. So defining the correlation between two points, with a source field added to the Hamiltonian:

\begin{equation}
        G(r_1-r_2) = \eval{\pdv{\ln(Z\{h\})}{h(r_1)}{h(r_2)}}_{h(r)=0}
\end{equation}

 If the Hamiltonian (closed to the fixed point Hamiltonian) only has short ranged interactions, we can ignore that the field is slowly varying and assumes it would transform as a weak field $h=h(r_1)$. Therefore the renormalised Hamiltonian:

\begin{equation} \mathcal{H} - \sum_r h(r)s(r) \rightarrow \mathcal{H'} - \sum_{r'} h'(r')s'(r'), \quad h'(r') = b^{y_h}h(r) \end{equation}

So as we know the scale between $r_1-r_2$ has just been zoomed out so that $r'_1 - r'_2 = (r_1-r_2)/b $

\begin{equation}G((r_1 - r_2)/b) = \pdv[2]{\ln(Z'(h'))}{h'(r_1')}{h'(r_2')} = \pdv[2]{\ln(Z(h))}{h'(r_1')}{h'(r_2')} =  b^{-2y_h} \langle ( s_1^{(1)} + s_2^{(1)} + \cdots)( s_1^{(2)} + \cdots) \rangle_{\mathcal{H}}\end{equation}

so where $s_2^{(1)}$ is the second spin in the first block. The expansion can be written as making an infinitesimal local change to the field within a block corresponds to changing all the fields acting on the spins in this block by $b^{-y_h}$ - the renormalisation eigenvalue for that magnetic scaling variable. As there are $b^d$ spins in each block we can expand as a sum of $b^{2d}$ two point correlation. These will be numerically the same if the distance between the two correlated spins is much larger than $b$. Hence:

$$ G((r_1 - r_2)/b)_{\mathcal{H'}} = b^{2(d-y_h)}G(r_1 - r_2)_{\mathcal{H}} $$

so subbing in the relevant variable for $\mathcal{H}$. and get out how the correlation function scales close to the critical point and extract more critical exponents. These can then be related to the thermodynamic exponents, a hyperscaling relations between the other critical exponents not covered by the scaling relation are related. Dangerous irrelevant variables can mess up these relations.

### Scaling Operators and Dimensions

The correlation function scaling ideas can be generalised to arbitrary correlations. As the scaling fields are linear in the deviations of the couplings, and each variable couples to a unique interaction term in the Hamiltonian so the interactions can be expressed as the fundamental degrees of freedom. For example in the Ising model the interaction terms can be expressed as a linear combination of products of arbitrary spins on different sites. However, our derivation above used the assumption that the interactions are short ranged, the objects we are trying to express must be local. \\

These objects are called operators, due to the relation between QFT and statistical mechanics relation.  Defining from the operators $\{S\}$ of the interactions, what we will call scaling operators, $\phi_i$ that couple to the appropriate scaling fields:

\begin{equation}\sum_i u_i \phi_i = \sum_a (K_a - K_a^*)S_a \end{equation}

Then the argument of the Ising correlation can be generalised to show that as $\abs{r_1 - r_2} \rightarrow \infty$, $\langle \phi_i(r_1)\phi_i(r_2) \rangle \propto \abs{r_1 - r_2}^{-2x_i}$ where $x_i = d-y_i$. \\

This quantity $x_i$ is called the scaling dimension of operator $\phi_i$. What this does is relate the renormalisation group eigenvalue of a scaling variable ($y_i$) to the behaviour of the two point correlation function. To understand the behaviour of this quantity, consider the continuum of the Hamiltonian and the restriction that the partition function be invariant. The scaling of the length and the scaling variable requires that the field scale as $\phi_i(r) \rightarrow b^{x_i}\phi_i(r)$ \\

To be concrete, the local energy density, $E(r)$, and its corresponding two point correlation function of the Ising model behaves how we expect - $\expval{E(r_1)E(r_2)} \sim \abs{r_1 - r_2}^{d - y_t}$. But the operators $E(r)$ are not the scaling operators but the linear combinations of them. It is the scaling operators that have pure power behaviour of their correlations. The energy operator will be a combination of all the scaling operators that transform in the same way under the symmetries of the Hamiltonian, so at finite separation, it should technically be:

\begin{equation}
    \expval{E(r_1)E(r_2)} = \sum_{i,j} \frac{A_{ij}}{\abs{r_1 - r_2}^{x_i + x_j}}
\end{equation}

where the most relevant contribution will be the one with the smallest scaling dimension and the operator this corresponds to has the earlier form.

There is also the irrelevant operators to take into account, and these will lead to corrections of the form $\sum_{\text{irrel}}y_k$ to the exponent. To generalise to an $N$ point correlation function, the same arguments can be followed to get:

\begin{equation}\langle \phi_1(r_1)\phi_2(r_2)\cdots \phi_N(r_N) \rangle = R^{-x_1 - \cdots x_N} \langle \phi_1(r_1/R) \cdots \phi_N(r_N/R) \rangle \end{equation}


### Cross Over Behaviour - 2 Examples

Consider the space of Hamiltonians that describe short range ferromagnetic systems, with a vector spin $\textbf{s}(r) = (s_x(r),s_y(r),s_z(r))$. Depedent on the symmetries, this can be descibed by either the Ising, XY or Heisenburg Models. We can represent this in the following Hamiltonian.

\begin{equation}
    \mathcal{H} = \sum_{r,r'} J(r-r')\textbf{s}(r) \cdot \textbf{s}(r') - D \sum_r s_z(r)^2
\end{equation}

\begin{wrapfigure}{r}{0.3\linewidth}
    \centering
    \includegraphics[height=5cm]{RGnotes.png}
    \label{fig:my_label}
\end{wrapfigure}


So when $D=0$, this behaviour is described by the Heisenburg fixed point. If $D$ is positive and large then we will have an Ising system and an XY if $D$ is large and negative. Therefore projecting our flows down to the $(T,D)$ plane will give three fixed points as shown in the Image, with this being the easiest way to connect up the relevant and irrelevant flows as we expect Ising or XY even for arbitrarily small $D$.\\


The point at $D=0$ and $T=T_c$ is a bicritical point, at the junction of two lines of critical points. We need to consider what happens when we try to cross this line in different ways, denoted by $A$ and $B$ in the diagram. In flow $A$, this doesnt come close to the Ising point, therefore its critical exponents will be controlled by the Heisenburg fixed point. But if we get close to the Ising points, like in path $B$, then the trajectory will spend a long time in the vicinity of the Ising fixed point.\\

So consider the transformation law for the singular part of the reduced free energy in the vicinity of Heisenburg:

\begin{equation}
    f_s(t,D) = b^{-nd}f_s(tb^{ny_{tH}},Db^{ny_{DH}})
\end{equation}

Choosing it so that one of the arguments is equal to one, we get a form of the scaling as:

\begin{equation}
    f_s(t,D) = \abs{t}^{2-\alpha_H}\Psi(D\abs{t}^{-y_{DH}/y_{tH}})
\end{equation}

where the new exponent is called the cross over exponent $\phi = y_{DH}/y_{tH}$, given entirely as the eigenvalues of the Heisenburg unstable fixed point. So when $D$ is small there is no change to the specific heat exponent of the Heisenberg fixed point. However when $D\abs{t}^{-\phi} \approx 1$ and we reach the cross over temperature. So when $t$ is small, we should observe Ising like exponents from these arguments (we set $D$ to be positive a while back) but this is not predicted by perturbation theory. So we add this by hand as a boundary condition on the scaling function. So looking at these consequences, for the specific heat:

\begin{align}
     C \sim \abs{t}^{-\alpha_H} \Psi(D\abs{t}^{-\phi}) &= D^{-\alpha_H/\phi)} (D\abs{t}^{-\phi})^{\alpha_H/\phi}\Psi(D\abs{t}^{-\phi})\\
     & \equiv D^{-\alpha_H/\phi} \tilde{\Psi}(tD^{-1/\phi})
\end{align}

Which defines a new scaling function $\tilde{\Psi}$, with the only dependence on the temperature being in this scaling function. Applying the fact that we know that the specific heat will have an Ising like singularity: $C \sim A(D)(t-t_c(D))^{-\alpha_I}$ therefore this must arise from the new scaling function having a singularity.

\begin{equation}
    \tilde{\Psi}(tD^{-1/\phi}) \sim a(tD^{-1/\phi} - b)^{-\alpha_I} \quad \implies C \sim aD^{\alpha_i - \alpha_H}(t - bD^{-1/\phi})^{-\alpha_I}
\end{equation}

This tells us how the amplitude of the Ising peak (given by $A(D)$) varies and how the critical temperature is shifted with increasing $D$ (when the bracket equals zero). These both are dependent on $\phi$, which is surprising as the amplitude of the singular behaviour and shape of the phase boundary are two quantities that can be measured separately - this is a prediction that RG makes that can be tested.

### Finite size scaling

Theres another type of cross over that can happen that depends on the geometry of the system, not the interactions. Consider a system whose critical behaviour is described by an isotropic fixed point, with length $L$. This means as the microscopic spacing gets rescaled the density gets rescaled$N = L/a \rightarrow b^{-1}N$ rescaling the length would not change the system but only our measurement scale). Therefore we can think our free energy as dependent on $N^{-1}$, with the thermodynamic limit corresponding to this going to zero. Our new free energy will become:

\begin{equation}
    f_s(\{K\}, N^{-1}) = b^{-d} f_s(\{K'\}, bN^{-1})
\end{equation}

This means we can think of $N^{-1}$ as a relevant scaling variable with eigenvalue $y=1$, although we have assumed that a non zero value of this does not affect the renormalisation group equation for the interactions which is reasonable if the interactions are short range. Considering the susceptibility, and setting the thermal variable to be equal to 1, we get the scaling form:

\begin{equation}
    \chi(t,N^{-1}) \sim \abs{t}^{-\gamma}\phi(N^{-1}\abs{t}^{-\nu}) \sim N^{\gamma/\nu}\tilde{\psi}(tN^{1/\nu})
\end{equation}

Knowing that $\abs{t}^{-\nu}$ is the correlation length, we can write the argument of the scaling function as $\xi/N$. This means that when $N \gg \xi$, the scaling function becomes irrelevant. But there will be a cross over temperature as $t$ is decreased $t_X \sim N^{-1/\nu}$ where the finite size effects become pronounced. As an example there are no thermodynamic singularities in a finite system, with the extent of this rounding off being given by crossover theory. So considering the second scaling form given, and realising that $\tilde{\psi}$ will be analytic and expected to have a peak.\\

This form tells us that the shift in the effective critical point (maximum of $\chi$) should scale like $N^{-1/\nu}$ and the height of the peak is predicted to behave as $N^{\gamma/\nu}$. The direction of the shift of the peak depends on the boundary conditions, with periodic conditions suppressing fluctuations as only certain wave vectors are allowed, resulting in a higher critical temperature. Therefore the scaling function $\tilde{\psi}$ depends on not only the shape of the geometry but the boundary conditions as well. \\

There is some subtlety with a non-zero effective dimensionality (ie a $L \times L \times \infty$ slab), which can all be resolved with cross over behaviour. Though experimentally it is hard to untangle finite size effects from boundary effects.


## Renormalisation Using Functional Methods
The technique which will be most useful in QFT is momentum space renormalisation group where the action is perturbed and the behaviour under successive renormalisation is followed. This allows us to understand how parameters will change as the lengths of the system is scaled. \\

The first step is to split up the field into fast and slow modes. This course graining is artificial and we introduce a chosen frequency, denoted $\Lambda'$, above which the modes are fast and below which they are slow. This procedure of course graining can be implemented by taking the Fourier transform of $\theta$ and then defining a 'random' point to separate the frequencies at.

\begin{align}
    \theta = \frac{1}{\beta L} \sum_{\omega} e^{iqr}\theta(q) &= \frac{1}{\beta L }\sum_{\omega < \Lambda'} e^{iqr}\theta(q) + \frac{1}{\beta L}\sum_{\Lambda' < \omega < \Lambda}e^{iqr}\theta(q) \\
    &= \theta^s + \theta^f
\end{align}

Here $\theta^s$ are defined as the 'slow' modes and $\theta^f$ are the 'fast' modes. $\Lambda$ is an ultraviolet cutoff beyond which contributions to the field are ignored. Another way of parameterising the frequency is by a scaling parameter $b$ such that $\Lambda' = \Lambda/b$. Preferably, $b=1 + \delta l$, that infinitesimally small parts of the system are averaged over and details will not be glossed over. \\

The next step is to integrate over all the fast modes to find a new effective action. The form of this new action is compared to the original and it must be the same up to scaling of the terms. If extra terms are generated then the procedure cannot be iterated and we cannot effectively use the renormalisation group. \\

The action is defined in the exponent of the partition function, so splitting up the action into parts containing the modes separately and a term that is a combination of the both:

\begin{align}
    Z[\theta] = \int \mathcal{D}\theta e^{-S[\theta]} =&  \int \mathcal{D}\theta^s e^{-S_s[\theta^s]} \int \mathcal{D}\theta^f e^{-S_f[\theta^f] - S_m[\theta^f,\theta^s]} \\
    =& \int \mathcal{D}\theta^s e^{-S'[\theta^s]}
\end{align}

The new action $S'[\theta]$ is given by the original slow modes of the action, multiplied by functional integral over the fast modes of the term that contained both modes and the fast modes. Multiplying by the partition function of only the fast modes (ie $Z_f = \int \mathcal{D}\theta^fe^{-S_f[\theta^f]}$) divided by itself, means a proper average can be formed with respect to the fast modes.

\begin{align}
    e^{-S'[\theta^s]} = e^{-s_s[\theta^s]}  \frac{\int \mathcal{D}\theta_fe^{-S_m[\theta^f,\theta^s]}e^{-S_f[\theta^f]}}{\int \mathcal{D}\theta^f e^{-S_f[\theta^f]}}\int \mathcal{D}\theta^f e^{-S_f[\theta^f]} =
    e^{-s_s[\theta^s]}  \langle e^{-S_m[\theta^f,\theta^s]} \rangle_{S_f} Z_f[\theta^f]
\end{align}

The partition function of the fast variables will be independent of the slow variables, therefore does not contribute and will be cancelled in any calculations of the correlation functions. \\

Here is where the perturbative nature of RG can be seen. Suppose there is a coupling in the action of the mixed term $S[\theta^f,\theta^s] = \lambda S[\theta^f,\theta^s]$, which we can take to be small. An expansion about this parameter can be done and we will only consider first order corrections. If the term is small enough the average can be put on the secondary term and then re-exponentiated in the following way:\\

\begin{equation}
      \langle e^{-\lambda S_m[\theta^f,\theta^s]} \rangle_{S_f} \approx 1 - \lambda\expval{S_m[\theta^f,\theta^s]}_{S_f} \approx e^{-\lambda\expval{S_m[\theta^f,\theta^s]}_{S_f}}
\end{equation}

Using this approximation the average can often be calculated, and an expression for the renormalised action can be found.\\

The final step is to rescale the frequencies in the effective action so that the cutoff momenta is the same regardless of scale $\omega' = s\omega$. This will rescale the fields by $\theta'(\omega') = \zeta^{-1}\theta^s(\omega'/s)$, and $\zeta$ is chosen appropriately. This allows us to map the action onto itself while increasing the scale. \\

Considering the `mixed' term to be a perturbation to an original quadratic action and remembering that the scale that is being integrated over is energy, then it can be seen that following the coupling of the perturbative term across many iterations of the renormalisation group will determine how strong the perturbation will be at lower and lower energy. This is an invaluable tool to see how a system reacts to perturbations.
