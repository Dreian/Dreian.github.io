---
layout: post
title:  "Type-level graphs in Haskell"
date:   2021-02-01 09:00:00 +0000
categories: jekyll update
---

I have been recently looking at existing facilities for type-level structures in
Haskell, as well as the possibility for encoding data types at the type level.
There is a lot of potential for representing all sorts of properties using the
type system.
This also includes effect systems, which is done using graded monads
([`effect-monad`](https://github.com/dorchard/effect-monad) by Dominic Orchard
and Jan Bracker shows how to do this).

The kinds of type-level structures Haskell supports are booleans and natural
numbers, which come with support for type-level branching and arithmetic.
It goes even further: we can write *type-level finite lists* as well.
Finite lists also allow us to represent
[finite sets](https://github.com/dorchard/type-level-sets),
which in turn allow us to represent
[data-flow transfer functions](https://github.com/dorchard/dataflow-effects-as-grades).

The thing all these structures have in common is the fact that they are *finite*
and they have *no loops*.
The first of these is hardly surprising: an infinite type-level structure like
a stream (i.e. infinite list) might be useful some setting, but an infinite type
signature is useless; a definable infinite list will necessarily have a finite
representation using some fixed-point operator ($Y$, $\mu$...), so any useful
infinite list has a finite representation as long as we can write type-level
ASTs.
The second is there to guarantee that every operation based on structural
recursion terminates.

*Graphs* are the most natural `loopy' structure to consider in this case.
It might not seem obvious why anybody would care – what kind of property would a
graph possibly represent?
Practically speaking, there are good reasons to verify type-level
*happens-before* relations: for concurrent programs, for representing tasks
with prerequisites and so on.
From a mathematical standpoint, this is just a natural next step after showing
how to represent finite sets and finite function domains: a directed graph is
nothing more than a representation of a set $A$ and a binary relation
$R \subseteq A \times A$ (a bipartite graph can also be used to represent a
relation $R' \subseteq A \times B$).

In this post, I show how we arrive at an implementation of type-level
graphs, as well as the challenges of providing this embedding.

# Type-level facilities

# Sets, records and trees

# Representing graphs

{% highlight haskell %}
type family UnionRelation (a :: [[k]]) (b :: [[k]]) :: [[k]] where
  UnionRelation '[] ys = ys
  UnionRelation xs '[] = xs
  UnionRelation (a ': xs) (a ': ys) = a ': UnionRelation xs ys
  UnionRelation ('[a, x2] ': xs) ('[a, y2] ': ys) =
    If ((Cmp x2 y2) == LT) ('[a, x2] ': UnionRelation xs ('[a, y2] ': ys))
                           ('[a, y2] ': UnionRelation ('[a, x2] ': xs) ys)
  UnionRelation ('[x1, x2] ': xs) ('[y1, y2] ': ys) =
    If ((Cmp x1 y1) == LT) ('[x1, x2] ': UnionRelation xs ('[y1, y2] ': ys))
                           ('[y1, y2] ': UnionRelation ('[x1, x2] ': xs) ys)
{% endhighlight %}

# From partial to primitive recursion

# Usability


