# Bounded-outdegree coloring

## Context

Distributed graph algorithms, LOCAL model.

Trees oriented so that all nodes have outdegree at most $d$.

($d = 1$ is the familiar case of rooted trees.)

## New result

For any constant $d \ge 2$, there is an $O(\log^* n)$-round algorithm that solves list coloring for lists of size $d(d+1)$.

In particular, for $d = 2$ we can solve list coloring for lists of size 6.

## Prior work

For any constant $d \ge 2$, there is an $O(\log^* n)$-round algorithm that solves list coloring for lists of size $d(d+1) + 1$; see [Fuchs, Kuhn 2026](https://arxiv.org/abs/2608.02386).

## Documents

- [AI-generated write-up](writeup.pdf)

## Discovered by

GPT-6 in Codex

## Communicated by

[Jukka Suomela](https://jukkasuomela.fi)

## Confidence

Vibe-formalized in Lean 4 in Palomar style.

## Thanks

Thanks to everyone involved in the bounded-outdegree coloring project.
