### <u>AXIOM OF SPECIFICATION</u>

This short blog explores a simple idea in set theory with an extension into Theoretical Computer science. In Set Theory, one of the foundational principles regarded as true (formally called an Axiom) is the axiom of specification, which simply states that "Any definable subclass of a set is a set". Mathematically, defined as:

> $$\forall z:\exists x: \forall y:(y\in x\iff (y \in z  \wedge P(y)))$$ where P(y) is a property/well-formed formula 

Also, this axiom goes by other names and definitions like the Axiom of restricted comprehension. Notice in our definition "y" is restricted as y contains elements that satisfy our condition and are in z. Taking away, our restriction we are left with :

> $$\exists x: \forall y:(y\in x\iff  P(y))$$ where P(y) is a property/well-formed formula 

Which is termed as the Axiom of unrestricted specification. Thus we have that "y" consists of all and only the elements that satisfy our Property. Interestingly, we ran into an inconsistency discovered by Logician Bertrand Russell. Here is the inconsistency: 
 >Let R={y:P(y)} where P(y) is the property that y $$\notin$$ y (or R is the set of all sets  that are not members of themselves). If R is not a member of itself, then by definition R is a member of itself; yet, if it is a member of itself, then it is not a member of itself, since it is the set of all sets that are not members of themselves.

Clearly restricting from all sets to some sets (i.e. $$y\in$$ z) resolves our logical inconsistency. From the paradox, we can ascertain that "A set of all sets  cannot contain themselves". we can extend this idea to functions. Now suppose we have a recursive function containing self-recursive functions. 
