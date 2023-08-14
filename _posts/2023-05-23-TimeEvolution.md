---
title: "Why is everything time ordered?"
date: 2023-04-23
categories: [Maths Heavy, Demonstrations]
tags: [Operators]
excerpt: "Understanding why time-ordering is needed in the maths of Quantum Field Theory"
mathjax: "true"
---

In Quantum Field Theory, there is this odd little symbol that crops up everywhere - that of the time ordering (super)operator $$\mathcal{T}$$. This is an instruction as to what order to act our time-dependent operators on the underlying state, making sure that the earliest time acts first. When starting to study QFT, it can be confusing to understand why this is used in the definition of Green's functions and why past a certain point in the course it suddenly appears. Many books rely on a physical intepretation of the ordering explaining how it accounts for particles and anti-particles. 

Here I'll consider it as arising as bit of mathematical trickery to make expressions easier to write and a way to put times on equal footing. From this perspective, time ordering is an unavoidable feature of trying to find the time-evolution operator for a time-dependent Hamiltonian. This explains why the ordering crops up halfway through most introductory courses as time-independent Hamiltonians, which normally make up the first few examples in a course, can be solved for without time ordering but by just finding eigenstates. Note that trying to incorporate interactions and using the the interaction picture will produce a time-dependent Hamiltonian; it's more than just an external field that varies in time. 

To find the expression for the time evolution of a time-dependent Hamiltonian, Schrodinger's equation must be solved [^1]. Using the evolution operators results in,

$$
\begin{equation}
    i\frac{dU(t,t_r)}{dt} = H(t)U(t,t_r),\end{equation}
$$

$$
    \begin{equation}
     \quad \rightarrow U(t,t_r) = U(t_r,t_r) - i\int_{t_r}^t dt_1 H(t_1)U(t_1,t_r).
\end{equation}
$$

When no time evolution occurs, the state must not change which implies that $$U(t,t) = 1$$. The problem can be solved by inserting $$U(t,t_r)$$ into the right hand side iteratively,

$$
\begin{equation}
    U(t,t_r) = 1 -i \int_{t_r}^t dt_1 H(t_1) \Big( 1 - i\int_{t_r}^{t_1} dt_2 H(t_2)U(t_2,t_r)\Big).
\end{equation}
$$

This is an infinite sum so we can express it as such,

$$
\begin{equation}
    U(t,t_r) = \sum_{n=0}^{\infty} (-i)^n \int_{t_r}^t dt_1 \int_{t_r}^{t_1} \cdots \int_{t_r}^{t_{n-1}}dt_{n} \ H(t_1) \cdots H(t_n).
\end{equation}
$$

There are $$n$$ integrals at the $$n$$-th order of summation. It is crucial to remember in this derivation that the Hamiltonian is a fully fledged operator whose order cannot be swapped carelessly. The set of $$t_n$$ is also ordered so that

$$
\begin{equation}t \ge t_1 \ge t_2 \cdots \ge t_n \ge t_r\end{equation}.
$$

 This is due to the iterative nature of the procedure requiring intermediate times and those intermediate times appearing as the integration limits. This dependence however is difficult to implement and we can re-express this chain of conditional integrals with all the integrals having the same limits. This idea, although it seems like a pointless shift of emphasis, is useful as having $$n$$ time intergrals over the same limits to do of a complicated function is often nicer than having a simple function over complicated interdepedent integration limits - remember previous calculus courses youve taken! It also allows all the fields to be treated on the same footing, with time being a label in QFT, so they truely are the same object rather than a weird sub-field. To see how to obtain the same limits on the integral consider the term at second order,

$$
\begin{equation}
  O^{(2)}(t,t_r) = -\int_{t_r}^t dt_1 \int_{t_r}^{t_1} dt_2 H(t_1)H(t_2), \quad \quad \text{ where } \ \ t_1 \ge t_2.
\end{equation}
$$

Let's introduce a notation for ordering our operators called the time ordering operator $$\mathcal{T}$$. It is a tool that ensures that operators at earlier times act first and are therefore on the right side of the equation. This can be explicitly formulated by using Heaviside functions $$\Theta(x)$$,

$$
\begin{equation}
  \mathcal{T}\{A(t_1)B(t_2)\} = \theta(t_1 -t_2) A(t_1)B(t_2) \pm \theta(t_2-t_1)B(t_2)A(t_1),
\end{equation}
$$

where the $$\pm$$ refers to the sign produced by the commutation relations of bosons or fermions. The second order term is re-written using this operator,

$$
\begin{equation}
  \mathcal{T} \{ \int_{t_r}^t dt_1 \int_{t_r}^{t} dt_2 H(t_1)H(t_2) \} = 2 O^{(2)}(t,t_r)
\end{equation}
$$

which allows the limits on the integral to be the same as the Heaviside function enforces these limits now. 

The factor of two must be introduced as the time ordering operator does not specify which time will be smaller. There are two ways of ordering $$t_1$$ and $$t_2$$, so if we want to obtain just one of the ways then the division by two must occur. This logic continues to the $$m$$-th order, where there are $$m!$$ ways of ordering $$m$$ times. Each term in the sum can be then be formulate in terms of a time-ordered expression. This leads to the final result,

$$
\begin{equation}
    U(t,t_r) = \mathcal{T}\{ \sum_{n=0}^{\infty} \frac{1}{n!}\int_{t_r}^t dt_1 \cdots dt_n \ H(t_1)\cdots H(t_n) \} = \mathcal{T}\exp( -i \int_{t_r}^t d\tau H(\tau) ).
\end{equation}
$$

The time-ordering that pervades quantum field theory arises due to the time evolution operator being expressed in this way. If we want to evolve any state/operator for the most general Hamiltonian (which is really the most basic thing that we can do!) then we must use the time-ordering operator, or instead have to impose by hand the heirachy of times. 

This short derivation should hopefully answer why time-ordering occurs in a roundabout way, by pointing out that one of the most fundamental builiding blocks (the time-evolution operator) involves a strange ordering of times. This is constrasted to other people who simply introduce the time-ordered Green's function (also known as a Feymann propagator) and to give physical reasons as to why this object makes sense. However that method is useful because to go from what is shown here to the time-ordered Green's function is rather tricky and lays the groundwork for non-equilibrium quantum field theory. I've written a whole section on getting to this point if you are feeling brave as it introduces the idea of time contours and shows why for equilibrium field theory all the subtlety can be ignored. 

<p style="text-align: center"><a class="btn btn--QFT btn--large" style="text-align: center" href="/QFT/">QFT Introduction</a></p>

[^1]: This has all been taken from one of the appendices in my thesis! Can find a full copy here. 