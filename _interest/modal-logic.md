---
title: "Modal Logic"
subtitle: "A few interesting facts and results in modal logic."
author_profile: true
read_time: true
permalink: /general-interest/modal-logic/
toc: true
toc_label: "Modal Logic"
header:
  image: /assets/images/italian-alps.jpg
  image_description: "A picture of the Italian alps early in the morning"
---

# Modal Logic

One of my favourite aspects of my undergraduate degree (in Maths and Philosophy) was formal logic. This came into use at every turn, from proofs in real analysis to standard form philosophical arguments. I can't begin to express just how much this one aspect of my degree has shaped the way I think and deal with the world, so I couldn't possibly recommend its study more.


## Introduction to Formal Logic

Formal logic is a really broad area, but fundamentally involves using signs and symbols to study inference. It is how we abstract our arguments, to analyse them in all their bare detail; formal logic gives us the tools to decide whether a given set of statements is consistent - that is, whether we can say they are all true or if one or more of them make one or more of the others false, thereby making them inconsistent with each other. The ways in which we do this can vary greatly, from considering every single case of each atomic unit being true or false - which may involve considering lots of combinations of true and false predicates - to using the "tableau" method. All of this, to me, is really special, because it gives us some incredible results about how we communicate and the types of ways we can call an argument false or identify the particular cases in which it can be true. 

Modal logic is a special case of this scenario, but to explain exactly how it differs from this (and indeed ends up extending formal logic into new realms), we need to look at some notation.


## Notation

In formal logic, we tend to write a predicate as a single roman letter. For instance, let $$P$$ denote the statement "$$x$$ was in the drawing room at midnight." Then, let $$Q(x, y)$$ denote the predicate "$$x$$ was with $$y$$" and $$R(x)$$ denote "$$x$$ committed the crime in question" - perhaps you can see where I'm going with this. With these definitions, I can give you a story like the following: 

> Colonel Mustard was in the drawing room with Mrs White at midnight.
  If Colonel Mustard was with Mrs White at midnight, he could not have committed the crime.
>

Now, if I give a couple of predicates we should be able to formalise this: first, $$\neg$$ is the negation symbol, so $$\neg A$$ means 'not $$A$$.' We evaluate this as you would expect - if $$A$$ is true, then $$\neg A$$ is false and _vice versa._ Then, $$\wedge$$ and $$\lor$$ mean _and_ and _or_ respectively, i.e. $$A\wedge B$$ means 'A and B' and $$A\lor B$$ means 'A or B'. We evaluate the former as true only when $$A$$ and $$B$$ are both true; it is false at all other times; the latter is true if either $$A$$ is true or $$B$$ is true (or they both are) - it is only false if both $$A$$ and $$B$$ are false. The last logical connective we're going to need is the conditional: $$\rightarrow$$, which (roughly) corresponds to "if ... then ...", so $$A\rightarrow B$$ means if $$A$$ holds, then $$B$$ holds. This, for reasons I'll go into in a separate post, is a tricky one but all you need to remember is that $$A \rightarrow B$$ is only false when $$A$$ is true and $$B$$ is false - i.e. we can't draw a false conclusion from true premises, any other combination of true and false for $$A$$ and $$B$$ will return true. There's another commonly used connective, $$\leftrightarrow$$, which represents 'if and only if' - $$A\leftrightarrow B$$ is only true if both $$A$$ and $$B$$ have the same truth value, i.e. when either both are true or both are false. These connectives are summarised in the following truth tables:

| $$A$$ | $$\neg A$$ |
| ----- | ---------- |
|  _T_  |    _F_     |
|  _F_  |    _T_     |

| $$A$$ | $$B$$ | $$A\wedge B$$ | $$A\lor B$$ | $$A \rightarrow B$$ | $$A \leftrightarrow B$$ |
| ----- | ----- | ------------- | ----------- | ------------------- | ----------------------- |
|  _T_  |  _T_  |      _T_      |     _T_     |         _T_         |           _T_           |
|  _T_  |  _F_  |      _F_      |     _T_     |         _F_         |           _F_           |
|  _F_  |  _T_  |      _F_      |     _T_     |         _T_         |           _F_           |
|  _F_  |  _F_  |      _F_      |     _F_     |         _T_         |           _T_           |

Now, we can return to the above example, which I'll write out again:
* Colonel Mustard was with Mrs White in the drawing room at midnight.
* If Colonel Mustard was with Mrs White at midnight, then he could not have committed the crime.

And the predicates are as follows:
* $$P(x)$$ - $$x$$ was in the drawing room at midnight,
* $$Q(x, y)$$ - $$x$$ was with $$y$$, and
* $$R(x)$$ - $$x$$ committed the crime in question.

So, we can now formalise our above argument: let $$m$$ represent Colonel Mustard and $$w$$ represent Mrs White. Then, we formalise the argument as:
* $$ P(m) \wedge Q(m, w),
* $$ Q(m, w) \rightarrow \neg R(m). $$

Using this, we can concluse that Colonel Mustard did not commit the crime (although we can say nothing of Mrs White...), and the standard way of representing this is as follows: 

$$
\{P(m) \wedge Q(m, w), Q(m, w) \rightarrow \neg R(m) \vdash \neg R(m) \}
$$

