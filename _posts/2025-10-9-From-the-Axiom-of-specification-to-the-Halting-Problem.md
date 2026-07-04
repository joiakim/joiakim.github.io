### FROM THE AXIOM OF SPECIFICATION TO THE HALTING PROBLEM

This short blog explores a simple idea in set theory and shows how the same idea reappears in the theory of computation.

### Part I: The Axiom of Specification

In set theory, the **Axiom of Specification** states that *any definable subclass of a set is itself a set*. Formally:

$$\forall z:\exists x: \forall y:(y\in x\iff (y \in z  \wedge P(y)))$$

where $$P(y)$$ is a property (a well-formed formula).

This axiom also goes by other names, such as the Axiom of Restricted Comprehension. Notice that in this definition, $$y$$ is *restricted*: it must both satisfy our property $$P$$ **and** already belong to some existing set $$z$$. If we strip away that restriction, dropping the requirement $$y \in z$$, we're left with:

$$\exists x: \forall y:(y\in x\iff  P(y))$$

This is called the **Axiom of Unrestricted Comprehension**. It says that for any property $$P$$, there exists a set $$x$$ consisting of exactly the elements that satisfy $$P$$, with no need for those elements to come from anywhere in particular.

This is where things break. Logician Bertrand Russell discovered the following inconsistency:

> Let $$R = \{y : P(y)\}$$, where $$P(y)$$ is the property $$y \notin y$$, that is, $$R$$ is the set of all sets that are not members of themselves. Is $$R \in R$$?
>
> If $$R \in R$$, then by the defining property of $$R$$, $$R \notin R$$ — a contradiction.
> If $$R \notin R$$, then $$R$$ satisfies the defining property, so $$R \in R$$ — also a contradiction.

Either way, we get a contradiction. The problem traces back to unrestricted comprehension: it let us conjure $R$ into existence from nothing but a property, with no set $$z$$ to draw its elements from. Restricted comprehension blocks this move, since $$R$$ would first have to be carved out of some *already-existing* set $$z$$. This is why modern set theory adopts restricted, not unrestricted, comprehension as an axiom.

### Part II: The Halting Problem

The **Halting Problem** asks: does there exist a program $$H$$ that, given any program $$P$$ and any input $$I$$, can always correctly decide whether $$P$$ halts or runs forever on $$I$$?

Suppose, for contradiction, that such a decider $$H$$ exists. Using $$H$$, we can build a new program, call it $$M^*$$, that takes a single input and does the following: it asks $$H$$ whether that input, run on itself, would halt.

<br>

<p align="center"><img src="/assets/h3.png" width="450"></p>

<p align="center"><i>Figure: M* takes itself as input. If M* would halt on itself, it loops forever instead; if M* would loop forever on itself, it halts instead.</i></p>

<br>

Instead of asking "would program $$P$$ halt on input $$I$$?", we ask:

 "Would $$M^* $$ halt when given $$M^* $$ as input?" 

By construction:

- If  $$M^* $$  halts on input $$M^* $$, then $$M^* $$ was built to do the opposite, so $$M^* $$ loops forever on input $$M^* $$.
- If $$M^* $$ loops forever on input $$M^* $$, then $$M^* $$ was built to do the opposite, so $$M^* $$ halts on input $$M^* $$.

Either answer contradicts itself. So $$M^*$$ cannot consistently exist but we built it directly from $$H$$. The only assumption we made was that $$H$$ exists. That assumption must be the one that's false. Thus no program $H$ can exist that decides, for every program and every input, whether that program halts on that input. Suppose we are interested in the halting property, $$P_{H}$$. Then we can reconstruct our argument as, if $$P_{H} \in P_{H}$$, then $$M^* $$ should halt yet it loops forever so $$P_{H} \notin P_{H}$$. If $$P_{H} \notin P_{H}$$, then $$M^* $$ should loop forever, yet it halts so $$P_{H} \in P_{H}$$.

**Conclusion: In both cases self-referencing breaks the property of universality.**



| Set Theory | Computability Theory |
|---|---|
| Property $$P(y)$$: " $$y \notin y $$ " | Decider $$H$$: "would this program halt on this input?" |
| Set $$R = \{y : P(y)\}$$, built from $$P$$ | Program $$M^*$$, built from $$H$$ |
| Ask: is $$R \in R$$? | Ask: does $$M^* $$ halt on input $$M^* $$? |
| $$\Rightarrow$$ unrestricted comprehension is inconsistent | $$\Rightarrow$$ no universal halting-decider $$H$$ can exist |

