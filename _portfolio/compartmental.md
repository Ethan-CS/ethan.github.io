---
title: "Compartmental Models"
excerpt: "Some information on Compartmental Models of epidemic spread."
read_time: true
author_profile: true
toc: true
toc_label: "Contents"
permalink: /research/compartmental/
header:
  image: /assets/images/forest.jpg
  image_description: "A picture of large trees by the edge of a body of water"
  teaser: /assets/images/forest-t.jpg
---

# Compartmental Models of Disease Spread

Compartmental models generally are mathematical ways of simulating how compartments of a population interact. This involves coming up with a system of equations that describe the behaviour of each compartment and then seeing how each compartment interacts with the other. These compartments can describe many states an individual (typically a person or an animal) can be in - for instance, we could use predator/prey compartments to simulate a hunting situation or susceptible/infected compartments to model disease spread. This latter use is the context I am focusing on in my research, so it's the one I'll be discussing here.

We can use epidemiological compartmental models to determine or estimate lots of different pieces of information - for one, we could come up with a reproductive number using the model for a given epidemic or determine the effectiveness of various interventions, from vaccines with a given effectiveness to social distancing measures with a particular success rate. Introducing information we already know about, say how effective mask-wearing and hand hygiene is in reducing the spread of an airborne disease can allow us to understand what we could consider as a disease being "under control," thereby informing public health policy and so on.

_**Warning: there's going to be some maths below, read at your own peril...**_


## SIR Model

The compartmental model that seems the most "standard" is the SIR model - susceptible, infected and recovered. In general, when you read the name of a particular compartmental model, the acronym has the letters in the order that the compartments come; for SIR, susceptible comes first, then infected, then recovered. In this model, an indivdual can be susceptible to a disease, infected by it or recovered from it. Anyone can transition between these states, and the maths comes in to describe the dynamics of changing between states. These dynamics can either be described by ordinary differential equations (ODEs) which yield a deterministic model or by a stochastic framework (i.e. involving probabilities), which is a random model. The trade-off here is that a stochastic model is much more complex and harder to analyse than deterministic models (although these can still be incredibly difficult), but stochastic models are far more realistic, meaning they yield an expected reality that should be much closer to the actual reality. I'll keep coming back to this example in the discussion below.


## Vital dynamics

_This section explains the work done in [[1]](#1)._

In epidemiology, we generally have to decide whether to consider "vital dynamics," also known as "demography," or not: these dynamics describe the birth and death rates that happen regardless of any disease spread, i.e. the ordinary birth rate and baseline death rate. If an epidemic is short-lived, we usually don't gain much by considering vital dynamics and instead considerably increase the complexity of the calculations involved, but in the case of a disease which persists over a longer period of time, it is very important and informative to consider vital dynamics.


### Without vital dynamics

If we choose not to consider vital dynamics (in the case of a short-lived epidemic/pandemic), we can get some nice differential equations. To do this, we need to make some initial definitions. Let's take the SIR model we have been considering as an example so far. Consider the transition between $$S$$ and $$I$$. Let $$N$$ be the size of the population, $$\beta$$ be the average number of contacts each person has per unit time multiplied by the probability of transmission from an infected to a susceptible individual and hence $$SI/{N^2}$$ is the proportion of contact between infectious and susceptible individuals that result in transmission. Then, the rate of transmission can be written as

$$
\frac{d(S/N)}{dt} = -\frac{\beta SI}{N^2}.
$$

You may be familiar with the [Law of Mass Action](https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Supplemental_Modules_(Physical_and_Theoretical_Chemistry)/Equilibria/Chemical_Equilibria/Mass_Action_Law), a law of nature describing equilibrium in chemistry; the above equation isn't far off this law!

Now, we consider the transition from $$I$$ to $$R$$ - we assume that the rate here is proportional to the number of infectious people, which we denote by $$\gamma I$$. In fact, this is the same as saying the probability of someone recovering in a time interval $$dt$$ is just $$\gamma dt$$, and if we take the average length of the infectious period to be $$D$$ then $$\gamma = 1/D$$. This is the same as assuming that the length of the infectious period of a disease is a [random variable](https://www.britannica.com/science/statistics/Random-variables-and-probability-distributions) which has an [exponential distribution](https://mathworld.wolfram.com/ExponentialDistribution.html). Of course, if an infected individual never recovers, we say that $$\gamma = 0$$ and the SIR model becomes the much simpler SI model, the solution of this being that eventually everyone becomes infected.

Now, with those preliminaries out of the way, we can write down the following differential equations that describe the SIR model [[1]](#1):

$$
\begin{align*}
\frac{dS}{dt} & = -\frac{\beta IS}{N},       ~~~  S(0) & = S_0 \geq 0, \\
\frac{dI}{dt} & = \frac{\beta IS}{N} - \gamma I,  I(0) & = I_0 \geq 0,\\
\frac{dR}{dt} & = \gamma I                        R(0) & = R_0 \geq 0.
\end{align*}
$$

Note that here, $$S(t), I(t)$$ and $$R(t)$$ are the numbers in the respective compartments so that $$S(t) + I(t) + R(t) = N.$$ From the discussions above, we see that the dynamics of the infectious compartment are dependent on $$R_0=\beta / \gamma$$, which we term the _basic reproduction rate._ During the COVID-19 pandemic, we have heard near-constant discussion of the so-called "$$R$$" number: this $$R_0$$ describes the baseline rate at which, left unimpeded, we could expect a disease to reproduce, and $$R$$ in a given scenario is the rate at which an infection is actually transmitting.


### With vital dynamics (endemic model)

If we'd like to model a disease which does require consideration of the births and deaths in a population using the above SIR model, we can make a few adjustments to account for these vital dynamics. The resulting model is known as the classic endemic model and is given by:

$$
\begin{align*}
\frac{dS}{dt} & = \mu N - \mu S -\frac{\beta IS}{N},         S(0) & = S_0 \geq 0, \\
\frac{dI}{dt} & = \frac{\beta IS}{N} - \gamma I - \mu I,     I(0) & = I_0 \geq 0,\\
\frac{dR}{dt} & = \gamma I - \mu I                           R(0) & = R_0 \geq 0.
\end{align*}
$$

This is pretty much the same as our SIR model above, but now we can account for the birthrate adding newborns into the susceptible compartment at a rate of $$\mu N$$ and the deathrate removing individuals from all classes at rates $$\mu S$$, $$\mu I$$ and $$\mu R$$ for susceptible, infected and recovered respectively. In these models, we generally have that births balance the deaths, so $$N$$, the size of the population, is still a constant. In this classic endemic model, the basic reproduction rate is given by $$R_0 = \beta / (\gamma + \mu)$$.





## References
<a id="1">[1]</a> 
Hethcote, H. (2000) 
_The mathematics of infectious diseases._
SIAM Review, 42 (4), pp. 599-653
