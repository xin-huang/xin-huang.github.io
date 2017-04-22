---
layout: post
title: Population Growth Models
date: 2017-04-22
use_math: true
---

In population genetics, we use mathematical models to describe how a population grows as time goes on. We can divide these models into two categories--deterministic and stochastic--based on whether we consider random factors or not. If we neglect random factors and assume the population has infinite number of individuals, then we build up determinsitic models. If we cannot ignore random factors because the population has finite number of individuals, which is a more realistic scenario, we have to think about stochastic models.

## Deterministic models

## Discrete time model

In this model, we assume the generation time is discrete. This means the old generation die out after they give birth to the new generation, like silkworms.
    
![img](http://www.cdfd.org.in/SILKSAT/img/lifecycle.jpg){: .center-image }

Let $N_t$ be the number of individual in the population at time $t$, and $w$ be the average number of progeny per individual (also the measure of the fitness of an individual), then the number of individual in the population at time $t+1$ is: 

\begin{align\*}
    N_{t+1}=wN_t.
\end{align\*}

Therefore, if $N_0$ is the number of individual in the population at time 0, then \begin{equation}N_t=N_0w^t.\end{equation}

If there are $k$ types of individuals in the population, and each type has different fitness (they have different number of progeny), then we can replace $w$ with $\bar{w}$, which is the average fitness of individuals in the population. Let $n_k$ be the number of the $k$-th type individual, and $w_k$ be its fitness, then the total number of individual in the population $N=\sum_k n_k$, and the average fitness is: 

\begin{align\*}
    \bar{w}=\frac{\sum_k w_kn_k}{N},
\end{align\*}

and 

\begin{align\*}
    N_{t+1}=\bar{w}N_t.
\end{align\*}

If $\bar{w}$ is not constant, let $\bar{w}_t$ be the average fitness at time $t$, we have 

\begin{align\*}
    N_t&=\bar{w}\_{t-1} N\_{t-1} \\\\ &=\bar{w}\_{t-1} \bar{w}\_{t-2} N\_{t-2} \\\\ &=N\_0 \prod\_{i=0}^{t-1} \bar{w}\_i.
\end{align\*}
        
## Continuous time model

In this model, we assume the generation time is continuous. For example, individuals with different ages in human populations can reproduce new individuals or die. Let $b$ and $d$ be the birth and death rates of the population in a small time $\Delta t$, respectively. Then in $\Delta t$, the change of the population number is: 

\begin{align\*}
    \Delta N_t=(b-d)N_t\Delta t.
\end{align\*}

As $\Delta t\rightarrow 0$, we have 

\begin{align\*}
    \frac{dN}{dt}=mN,
\end{align\*} 
    
where $m=b-d$, which is the **Malthusian parameter** measuring fitness of individuals in the continuous time model.

Therefore, \begin{equation}N_t=N_0e^{mt}.\end{equation}

Like in the discrete time model, if different types of individuals have different fitnesses, we can measure the average fitness of the population as: 

\begin{align\*}
    \bar{m}=\frac{\sum_k m_kn_k}{N},
\end{align\*} 

and 

\begin{align\*}
    \frac{dN}{dt}=\bar{m}N.
\end{align\*}

If $\bar{m}$ is not constant, we can break the time into $k$ intervals, and $\bar{m}_k$ is constant in the $k$-th interval. We then have 

\begin{align\*}
    N_t&=N_0e^{\bar{m}_1\Delta t_1}e^{\bar{m}_2\Delta t_2}\cdots e^{\bar{m}_k\Delta t_k} \\\\ &=N_0e^{\sum_k\bar{m}_k\Delta t_k} \\\\ &=N_0e^{\bar{\bar{m}}t},
\end{align\*}

where $\bar{\bar{m}}=\sum_k\bar{m}_k\Delta t_k/t$.

Eq. 2 tells us that a population will grow **exponentially** if no constraints exist. This is not true in reality. For example, the environment can only provide limited food for the population. As the population grows larger, each individual will obtain less food. Therefore, the population cannot grow up infinitily.

## Relation between $w$ and $m$

As we have seen, $w$ and $m$ measure fitness of individuals in the discrete and continuous time models, respectively. Fitness is an important parameter when we discuss natural selection. To connect these two terms, we can let $w=e^m$ or $m=\ln w$, then the two formulae $N_t=N_0w^t$ and $N_t=N_0e^{mt}$ are equivalent.

Morever, we can let $w=1+s$. If $s$ is very small, such as 0.01, then $w\approx 1$. Because $m=\ln w=\ln(1+s)\approx s$, when $w\approx 1$. We will find $s$ is the **selection coefficient** when we discuss natural selection.

## Stochastic models

## References