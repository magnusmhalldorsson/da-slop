# Distributed decompression

## Context

We have a $d$-regular graph $G = (V,E)$, each node stores $b$ bits, and we can design an $O(1)$-round algorithm that uses these bits to recover a subset of edges $X \subseteq E$.

## New result

$b = \lfloor d/2 \rfloor + 1$ bits suffice. For $d = 3$ we can have $b = 2$.

## Prior work

$b = \lceil d+1 \rceil + 1$ bits suffice. For $d = 3$ we can trivially have $b = 3$, but whether $b = 2$ suffices is open. See [Balliu, Brandt, Kuhn, Nowicki, Olivetti, Rotenberg, Suomela, DISC 2025](https://arxiv.org/abs/2405.04519).

## Documents

- [AI-generated write-up](writeup.pdf)
- [Human-written notes](human-notes.md)

## Discovered by

The main breakthrough was by GPT-5.6 in Codex; after the initial idea there was some human guidance towards a simpler algorithms.

## Communicated by

[Jukka Suomela](https://jukkasuomela.fi)

## Confidence

The high-level idea makes sense to me, and the ideas will find direct use much more broadly in the context of distributed computation with advice.

The result was also vibe-formalized in Lean 4 in Palomar style.

## Thanks

Thanks especially to Dennis Olivetti for discussions.
