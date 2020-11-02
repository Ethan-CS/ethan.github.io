---
title: Research
subtitle: An overview of what I'm working on
#readtime: true
permalink: /research/
---


_Return to [home](https://ethankelly.github.io/index)_


# Research

## About my PhD

**_TITLE: Game theoretic and probabilistic methods applied to spatial network models of contagion_**

Above is the research title that I was accepted to the University of Glasgow to investigate. Effectively, I'm interested in problems on graphs such as the Firefighter Problem and how using game theory and stochastic methods means they can be used to generate useful and descriptive models of contagion. To explain this, let's look at the Firefighter Problem.

### The Firefighter Problem

First introduced by Hartnell in 1995<sup>[1](#myfootnote1)</sup>, the Firefighter Problem (which we will refer to simply as _<span style="font-variant:small-caps;">Firefighter</span>_ from now on) is a simple model for an outbreak of fire. Consider a regular graph, which is just a collection of vertices (or nodes) connected to each other by edges (links) and what makes it regular is that every vertex has the same number of neighbours, such as in the following example.

(Image coming soon)

On this regular graph, a fire breaks out at some vertex. At that time, before the fire can spread our firefighter can choose a certain number of vertices (originally one) to 'defend,' which means they are protected from catching fire indefinitely. Then, the fire spreads to all unprotected neighbouring vertices. The firefighter gets another chance to protect some vertex/vertices and the fire spreads to any unprotected and unburnt vertices. This continues until either the entire graph is burnt or the firefighter has contained the fire.

How can we use this? Well, if we think of each vertex as an individual and the fire as a disease, then this could be used to understand how diseases spread on particular graphs. Then, the firefighter's strategy might be seen as the efforts of a public health body trying to slow the disease. In this scenario, another problem may be more applicable, the Firebreak Problem or simply _<span style="font-variant:small-caps;">Firebreak</span>_.

### The Firebreak Problem

_Firebreak_ is a similar idea to _Firefighter_, with one crucial difference: the defence strategy must be performed all in one go, before the fire breaks. This may be useful in a situation where we have a fixed budget to spend, which we deploy in one go by removing given vertices (introducing firebreaks) in the hopes of containing the outbreak as well as we can. The following animation shows the outbreak of a fire on a graph that we have removed some vertices randomly with probability 1/2, in order to represent more accurately a forest fire (see my notes on Percolation).

![](assets/outbreak.gif)

_Simple animation of unregulated firebreak on a randomly percolated graph._

Now, if we are allowed a budget that would cover the removal of up to two vertices ('trees') on the graph (in the 'forest'), we may choose to remove them in the way displayed in the next animation. Here, we see that we have managed to much better contain the fire using our firebreak.

![](assets/firebreak.gif)

_Simple animation of an outbreak of fire when a defence of 2 vertices has been implemented._





<a name="myfootnote1">1</a>: B. L. Hartnell, _Firefighter! an application of domination,_ in 25th Manitoba Conference on Combinotorial Mathematics and Computing, University of Manitoba in Winnipeg, Canada, 1995.



_Return to [home](https://ethankelly.github.io/index)_
