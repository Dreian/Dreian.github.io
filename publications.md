---
layout: page
title: Publications
permalink: /publications/
---

*   [A Graded Monad for Deadlock-free Concurrency (Functional Pearl)](
https://dl.acm.org/doi/10.1145/3406088.3409024)
(Andrej Ivašković and Alan Mycroft).
Haskell 2020

    This paper is the second in a series exploring how program analysis can be
    represented using graded monads.
    Concurrency is a natural setting for exploring concepts in programming
    language semantics and for performing analyses, and it is notoriously
    difficult for humans to reason about.
    _Deadlock_ is a common problem in concurrent programs that use explicit
    locking primitives.
    A common way to write code that avoids deadlock is to impose a partial order
    between locks.
    In this paper, we show how to enforce this discipline at the type level in
    Haskell.

*   [Data-flow Analyses as Effects and Graded Monads](
https://drops.dagstuhl.de/opus/volltexte/2020/12337/)
(Andrej Ivašković, Alan Mycroft and Dominic Orchard).
FSCD 2020

    This paper is part of a series of papers exploring how static analysis can
    be phrased in terms of graded monads.
    We looked at classical data-flow analysis (meaning _monotone data flow
    analysis frameworks_ as defined by [Kam and Ullman](
    https://link.springer.com/article/10.1007/BF00290339)).
    Typically, effect systems are used to analyse functional languages, but
    data-flow analysis is phrased in the context of imperative programs.
    We looked at a variant of the graded `State` monad and showed how a grading
    algebra based on _transfer functions_ can be used to represent liveness
    analysis and related data-flow program analyses.
    Dominic Orchard [implemented](
    https://github.com/dorchard/dataflow-effects-as-grades) the ideas from this
    paper in Haskell (and hence showed a way how type-level functions can be
    represented).

*   [Multiple Random Walks on Paths and Grids](
https://drops.dagstuhl.de/opus/volltexte/2017/6989/)
(Andrej Ivašković, Adrian Kosowski, Dominik Pajak, Thomas Sauerwald).
STACS 2017

    This paper is the result of my internship with Thomas Sauerwald in the
    summer of 2016.
    Random walks and Markov chains are undeniably useful across many areas of
    mathematics: network theory, optimisation, stochastic processes and so on.
    Intuitively, a random walk tracks how an entity explores a state space
    (usually we consider finite graphs).
    If a random walk starts at a node _u_, we can associate every state _v_ with
    _hitting time_ (expected time a random walk started at _u_ first reaches
    _v_).
    and we can talk about the _cover time_ of a state space (expected time a
    random walk started at _u_ visits all states).
    We can generalise these ideas to _multiple random walks_, where multiple
    walkers synchronously move at each timestep: for example, hitting time in
    this case refers to the expected time until one of the walkers reaches a
    vertex.
    We looked at what _speedup_ can be achieved when we switch from the single
    to multiple random walk setting, in the context of paths and grids.
