# Distributed edge coloring

## Context

Distributed graph algorithms, LOCAL model.

## Highlight results

Edge coloring with $O(\Delta)$ colors in graphs of maximum degree $\Delta$: possible in $O(\log^* n)$ rounds.

Edge coloring with $O(\Delta)$ colors in 2-colored graphs of maximum degree $\Delta$: possible in $O(\log^* \Delta)$ rounds.

The key idea is a ***color reduction technique*** that reduces $2^r \Delta$ colors to $O(r \Delta)$ colors in one round in 2-colored graphs. This leads to many new results on possible tradeoffs between the number of colors and the number of communication rounds, and it has also implications in list coloring.

## Prior work

The strongest result from prior work is $\log^{O(1)} \Delta + \log^* n$ rounds ([Balliu, Brandt, Kuhn, Olivetti, PODC 2022](https://arxiv.org/abs/2206.00976)).

## Documents

- [AI-generated write-up](writeup.pdf)
- [Human-written notes](human-notes.md)

## Discovered by

GPT-6 in Codex

## Communicated by

[Jukka Suomela](https://jukkasuomela.fi)

## Confidence

The algorithm idea is simple and elegant and makes a lot of sense to me. It uses only elementary mathematical ingredients and could be easily presented in a lecture to students.

The result has also been vibe-formalized in Lean 4 in Palomar style.

## Thanks

Thanks especially to Alkida Balliu, Sebastian Brandt, Fabian Kuhn, Yannic Maus, and Dennis Olivetti for discussions.

## Assigned to

[Yannic Maus](https://academia.yannicmaus.de)
