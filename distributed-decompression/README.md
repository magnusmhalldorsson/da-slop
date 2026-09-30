# Distributed decompression

## Context

Fix a $d$. We have a $d$-regular graph $G = (V,E)$, each node stores $b$ bits, and we can design an $O(1)$-round algorithm $A$ that uses these bits to recover a subset of edges $X \subseteq E$. What is the smallest $b$ such that there exists an $A$ that can be used to recover any given subset $X$?

## New result

$b = \lfloor d/2 \rfloor + 1$ bits suffice. For $d = 3$ we can have $b = 2$.

## Prior work

$b = \lceil d/2 \rceil + 1$ bits suffice. For $d = 3$ we can trivially have $b = 3$, but whether $b = 2$ suffices was left open by that work. See [Balliu, Brandt, Kuhn, Nowicki, Olivetti, Rotenberg, Suomela, DISC 2025](https://arxiv.org/abs/2405.04519).

## Documents

- [AI-generated write-up](writeup.pdf)
- [Human-written notes](human-notes.md)

## Discovered by

The main breakthrough was by GPT-5.6 in Codex; after the initial idea there was some human guidance towards a simpler algorithm.

## Communicated by

[Jukka Suomela](https://jukkasuomela.fi)

## Confidence

The high-level idea makes sense to me, and the ideas will find direct use much more broadly in the context of distributed computation with advice.

The result was also vibe-formalized in Lean 4 in Palomar style.

## Thanks

Thanks especially to Dennis Olivetti for discussions.
