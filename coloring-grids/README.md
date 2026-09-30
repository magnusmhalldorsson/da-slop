# Coloring grids

## Context

Distributed graph algorithms; LOCAL model, quantum-LOCAL model and non-signaling model.

Task: $c$ coloring, for a constant $c \ge 4$.

Graph family: $d$-dimensional grids.

## Highlight results

Ignoring possible $O(\log^* n)$ factors, we have the following bounds:

- $\Omega(d)$ locality needed
- $2^{O(d)}$ locality sufficient.

## Prior work

There is an algorithm with locality $2^{O(d^2)}$; see [Brandt, Hirvonen, Korhonen, Lempiäinen, Östergård, Purcell, Rybicki, Suomela, Uznański, PODC 2017](https://arxiv.org/abs/1702.05456).

## Discovered by

GPT-6 in Codex

## Documents

- [AI-generated write-up](writeup.pdf)

## Communicated by

[Jukka Suomela](https://jukkasuomela.fi)

## Confidence

The upper bound makes sense to me, I understand the idea, it is a minor modification of the algorithm from [prior work](https://arxiv.org/abs/1702.05456); the key change is that the cluster centers are selected more efficiently with an iterative algorithm instead of a single-shot algorithm.

The lower bound is based on the following graph-theoretic result: for any $c$, there are graphs that look locally like a $d$-dimensional grid, yet their chromatic number is more than $c$. This result has been formalized in Lean 4 in Palomar style.
