---
title: "We can't know how big the real numbers are"
math: true
draft: false
date: 2026-05-24
tags: ["math", "logic"]
summary: "Using a classic model theory theorem to show that some things are
above our understanding"
---

At some point when one is learning mathematics one reaches one of the most 
important theorems

{{<callout>}}
### Theorem (Cantor)
There is no bijection between the set of natural numbers and the set of real
numbers.
{{</callout>}}

Thus, when learning model theory and one reaches the following statement:

{{<callout>}}
### Theorem 
There exists a _model_ of set theory (Zermelo-Fraenkel specifically) in which 
the real numbers (of that model) are in bijection with the natural numbers.
{{</callout>}}

The first instinct is to think that something has gone terribly wrong...

The second instinct is that the word _model_ there has to be doing some heavy
lifting for this to make sense.

## Model Theory

Model Theory is a branch of logic that studies how we can realize "concretely"
different "universes" for a theory or set of axioms.

{{<callout>}}
### Example
In the theory of groups we need, a "universe" set $G$, a "binary
function symbol" for the multiplication $\mu:G \times G \to G$, a "constant
symbol" $1 \in G$, a "unary function symbol" for the inversion $\iota:G \to
G$, and the group axioms:
1. Associativity $$\forall x, \forall y, \forall z, \mu(\mu(x,y),z)=\mu(x,\mu(y,z))$$
2. Neutral element $$\forall x,\mu(x,1) = x = \mu(1,x)$$
3. Inverses $$\forall x, \mu(x,\iota(x)) = 1 = \mu(\iota(x),x)$$

In this theory, a "model" is simply... a group, namely $G$. What we have done in
this process is abstracted a group to a set of symbols $(G,\mu,1,\iota)$ and
some essential axioms. 
{{</callout>}}

Model theory cares about how different 'models' of a single set of axioms and
symbols behave. 

Each theory is made up by what is known as a "signature" or "language": a
collection of symbols in which to write the axioms.

{{<callout>}}
In the example we gave before there are three symbols:
multiplication, the constant and inversion symbols.

We also snuck in another symbol: the equality. This one's special only because 
we sometimes restrict our interpretations of this symbol to... the equality
(duh). But we could have also defined other symbols for other _relations_ not 
only functions or equality.
{{</callout>}}

Given a language, we can define a (first order) theory given by logical
formulas determined by those symbols alongside _logical symbols_ such as
$$\vee, \wedge, \neg, \to, \forall, \exists$$ and the parenthesis and commas as
auxiliary symbols (to make it easy to read).

First order theories are characterized by only using variables as parameters
for the existential ($\exists$) and universal ($\forall$) symbols, higher order
theories allow other types of symbols bounded by these.

An _interpretation_ of the language is simply a way to assign the symbols as
corresponding functions, constants, relations etc.

A package of a bunch of formulas in a language is what we call a _theory_.

Finally, an interpretation of a language, in which all formulas of a theory
hold -- that is, all the statements 'formalized' by the formulas _as symbols_
translate to actual properties in that interpretation -- is what we call a
_model_ of that theory.


{{<callout>}}
### Example
In our example before, we constructed the language of groups and its theory where
any model of such theory is actually a group.

We could create the language of rings, of vector spaces, of order relations, etc.
{{</callout>}}

## Substructures

Given a model, we can sometimes find _substructures_: a piece of the
model that is also a model.

{{<callout>}}
### Example
Given a group $G$ any subgroup $H \subseteq G$ will also be a model of the
theory of groups, meaning that taking $H$ as an interpretation of the language
we get _another_ model of a group that happens to be inside $G$.

It's important to distinguish that $H$ does not need to satisfy _all_
the same formulas as $G$, only the ones we fixed in the theory (the ones that
identify them as groups). There might be other formulas that are true in $G$ 
but not in $H$ and vice versa. For a more concrete example, let $G = Z/2$ be the 
integers modulo $2$, and its trivial subgroup $H=\{0\}$, then $G$ and $H$ are
not isomorphic as groups, _so there must be a formula (in the language of 
groups)_ that is true in $G$ and not in $H$ and vice versa, right? (Cool
exercise to understand what is happening).
{{</callout>}}

## Elementary Substructures

Sometimes a model has substructures that are _elementary_ meaning that the 
model and the substructure satisfy _all the same formulas_ (not just those in
the theory).

{{<callout>}}
### Example
Keeping in line with our group flavored examples, if we take the integers $G=\Z$
as our model of group, then the subgroup given by the even numbers $H = 2\Z$ is 
also a group that is _isomorphic_ to the whole group, meaning that they _must_
satisfy the same formulas (also cool exercise).
{{</callout>}}

Not always a model admits substructures, much less elementary substructures.

If one thinks for a bit, for a model to admit an elementary substructure it
should behave much like infinity: a part is 'equivalent' to the whole in some
way. But it is not evidently true that an infinite model admits elementary
substructures.

{{<callout>}}
## Löwenheim-Skolem theorem
Given _infinite_ model $M$ then for any infinite 
cardinality $\kappa$:
* if $\kappa \leq |M|$, there are elementary submodels $N \subseteq M$ such 
that $|N|=\kappa$.

* if $\kappa \geq |M|$, there are models $N'$ with $|N'|=\kappa$ such that 
$M$ is an elementary substructure of $N'$. 

This is incredible! If we have an infinite model, then there must be models
(equivalent even!) on _any infinite_ cardinality. (Cool exercise to show that 
the infinity part is required).

If you need the details Wikipedia's proof is ok. The TL;DR is
* for the first part, use the axiom of choice to "fill" a subset $A \subseteq
M$ with the required elements of $M$ so that every formula is either true
(adding elements of M) or false.
* for the second part we can create a new language using $M$ "as symbols" and 
any number (uncountable) of new symbols _different_ from those of $M$. Using
compactness it's easy to show that this new theory also has a model (using the
first part one can find a model of the required cardinality).
{{</callout>}}


{{<callout>}}
## Example
Returning to our integer group example $G=\Z$ this means that there are groups
$N'$ that are 'the same' as the integers but with _any_ infinite cardinality!
A group like $N'$ won't be isomorphic to $\Z$ (because they would need
to be in bijection, meaning they would have to have the same cardinality), _but_
from the perspective of group theory they are _indistinguishable_, they satisfy
_exactly_ the same properties (of group theory!).
{{</callout>}}

{{<callout>}}
## Peano arithmetic and 'weird naturals'
There are even more extreme examples. Usually when we work with the 
arithmetic of natural numbers we essentially use the Peano axioms. A _very_ 
small set of (first order) formulas that seem to condense our understanding 
of the natural numbers: we start at 1 (or 0 for some), we know how to add 1 
and we know it satisfies the principle of induction.

What the Löwenheim-Skolem theorem tells us is that _there are other_ versions of
the natural numbers (with other cardinalities) that also satisfy the same Peano
axioms!
This is like a supercharged version of Gödel's incompleteness theorem: we can't 
possibly characterize the natural numbers, there will _always_ be other weird
uncountable versions of them!
{{</callout>}}


## Skolem's Paradox

The example I'd like to finish here today is the one related to the one I
mentioned at the beginning. The theory of sets can be formulated in a first
order language; there are actually multiple ways to do it but the most accepted
one is the Zermelo-Fraenkel (or ZF for short).

As a direct corollary from the Löwenheim-Skolem theorem is the following:
we have a model of ZF -- the one we 'use' to make math every day; that
model is infinite (we have the set of natural numbers inside). Therefore, there
must be a model of ZF that is countable (the smallest possible infinity).
Furthermore, the real numbers $\R$ can be defined in the model we usually use,
meaning that it can be defined in that model as well, mutatis mutandis. 

{{<callout>}} 
In this model $\R$ _must_ be countable, since the entire model is
countable... but Cantor's theorem is also true in this model so... 

what is happening?
{{</callout>}}

This apparent contradiction is known as Skolem's Paradox.

Cantor's theorem interpreted literally only says: "a bijection from $\N$ to
$\R$ does not exist"; if one understands a function as a _set_, the statement
can be reinterpreted as: "a specific set (with some required properties) does
not exist _in this model_". From this what one can gather is that it's possible
that _there is a bijection_ from the real numbers (in that model) to the
natural numbers, _it's just that the bijection is not a set inside that model_!
In other words, the concept of cardinality _in that model_ works the same as
_in our usual model_, Cantor's theorem does not apply to sets "across models"!

## How large are the real numbers?

One thing that we can take from Skolem's paradox is that _we actually don't
know how large are the real numbers_. We don't really know in which model of ZF
we 'live'; we know that in any model we can't find a bijection from the real
numbers to the natural numbers, but that we can't find it doesn't mean it
doesn't exist _somewhere else_.
