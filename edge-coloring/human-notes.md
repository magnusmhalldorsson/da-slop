# Color reduction for edge coloring

(Notes by Jukka Suomela)

## Notation

$d$ = degree, $r \ge 2$ is a free parameter.

Our set of old colors is $C = [2^r d]$, we use $c$ to refer to old colors, and $c(e)$ specifically for the old color of edge $e$.

Our set of new colors is $K = [512rd]$, we use $k$ to refer to new colors, and $k(e)$ specifically for the new color of edge $e$.

## Setup

For each old color $c$, pick independently a uniformly random $4r$-element subset $N(c) \subseteq K$.

We say that these sets $N(c)$ are ***"expanding"*** if the following holds: if you pick any $A \le d$ old colors $c_1, \dotsc, c_A$, the union of $N(c_1), \dotsc, N(c_A)$ has at least $3rA$ elements. (Trivially it has at most $4rA$ elements.)

## A simple lemma on binomial coefficients

***Observation 1:*** For integers $1 \le b \le a$ we have ${a \choose b} \le (3a/b)^b$.

*Proof:* From $1 + x \le e^x$ we get $1 + b/a \le e^{b/a}$ and therefore

$$(1 + b/a)^a \le e^b.$$

Do the binomial expansion of $(1 + b/a)^a$, all terms are nonnegative, so we can just pick one term for this estimate:

$$(1 + b/a)^a \ge {a \choose b} (b/a)^b.$$

So to recap,

$${a \choose b} (b/a)^b \le e^b$$

and the claim follows from $e < 3$.

## Random subsets are expanding

***Claim 1:*** With probability at least $1/2$, randomly-chosen sets $N(c)$ are expanding.

*Proof:* Fix $1 \le A \le d$. Suppose there is some bad collection $X \subseteq C$ of size $|X| = A$ such that the union of $N(c)$ over $c \in X$ fits inside some subset $Y \subseteq K$ of size $|Y| = 3rA$.

Suppose we pick the $4r$-element subset $N(c)$ with a process where we keep selecting uniformly random elements of $K$ until we have $4r$ distinct elements. Then for $N(c)$ to be fully contained inside $Y$, it certainly has to be the case that our first $4r$ trials fall inside $Y$. So for a fixed $Y$, the probability that a randomly-chosen $N(c)$ indeed fits inside $Y$ is at most $$\left(\frac{3rA}{512rd}\right)^{4r} = \left(\frac{3A}{512d}\right)^{4r}.$$

For a fixed $X$, the probability that all $A$ of the sets $N(c)$ fit inside $Y$ is hence at most $$\left(\frac{3A}{512d}\right)^{4rA}.$$

There are $2^r d \choose A$ possible choices of $X$, and $512rd \choose 3rA$ possible choices of $Y$. So the probability that for some $X$ and $Y$ bad things happen is, by union bound, at most

$${2^r d \choose A} {512rd \choose 3rA} \left(\frac{3A}{512d}\right)^{4rA}.$$

Then apply Observation 1 to get the following upper bound:

$$\left(\frac{3\cdot2^r d}{A}\right)^A \left(\frac{3 \cdot 512rd}{3rA}\right)^{3rA} \left(\frac{3A}{512d}\right)^{4rA}$$
$$= \left(\frac{3\cdot2^r d}{A}\right)^A \left(\frac{512d}{A}\right)^{3rA} \left(\frac{3A}{512d}\right)^{4rA}$$
$$= \left( \left(\frac{3\cdot2^r d}{A}\right) \left(\frac{512d}{A}\right)^{3r} \left(\frac{3A}{512d}\right)^{4r} \right)^A$$
$$= \left( \left(\frac{3\cdot2^r d}{A}\right) \left(\frac{A}{512d}\right)^r \cdot 3^{4r} \right)^A$$
$$= \left( \frac{3d}{A} \cdot 2^r \cdot \left(\frac{A}{512d}\right)^r \cdot 81^r \right)^A$$
$$= \left( \frac{3d}{A} \left(\frac{81A}{256d}\right)^r \right)^A$$
$$= \left( 3 \cdot \left(\frac{81}{256}\right)^r \cdot \frac{d}{A} \cdot \left(\frac{A}{d}\right)^r \right)^A$$
$$= \left( 3 \cdot \left(\frac{81}{256}\right)^r \cdot \left(\frac{A}{d}\right)^{r-1} \right)^A$$
$$\le \left( 3 \cdot \left(\frac{81}{256}\right)^r \right)^A$$
$$< \left( 3 \cdot \left(\frac{1}{3}\right)^r \right)^A
\le \left(\frac{1}{3}\right)^A.$$

Now this was for a fixed size $A$, and then summing over all sizes of $A$ the probability of bad things happening is bounded by $(1/3)^1 + (1/3)^2 + \dotso + (1/3)^d < 1/2$.

## Algorithm

So from now on we will assume that we have indeed chosen expanding sets $N(c)$. The complete algorithm is now:

- **Black node:** We see the old colors $c(e)$ of incident edges $e$. For each incident edge $e$, pick an $(r+1)$-element subset $S(e) \subseteq N(c(e))$, such that the sets $S(e)$ are pairwise non-intersecting.

- **White node:** We see the sets $S(e)$. For each incident edge, pick a color $k(e) \in S(e)$ such that the colors are different.

## Black nodes succeed

***Claim 2:*** Black nodes have a valid choice.

*Proof:* Consider this auxiliary bipartite graph $H$:

- $(r+1)d$ blue nodes, $r+1$ copies $(e,1), (e,2), \dotsc, (e,r+1)$ for each incident edge $e$.
- $512rd$ orange nodes, one for each new color in $K$.
- You add an edge from $(e,i)$ to $k$ if $k$ is in $N(c(e))$.

Now if you select any subset of $B$ blue nodes, you will select blue nodes corresponding to some $A \ge B/(r+1)$ distinct edges $e$. So you are selecting at least $A$ distinct subsets $N(c)$, and they are "expanding", so they cover at least $3rA \ge 3rB/(r+1) \ge B$ orange nodes. So to recap, the neighborhoods of any $B$ blue nodes cover at least $B$ orange nodes. So by Hall's theorem, there is a matching $M$ in $H$ that matches all blue nodes with distinct orange nodes. So this way we are able to select for each incident edge $e$ a set $S(e)$ of $r+1$ new colors from $N(c(e))$, so that the sets $S(e)$ are pairwise non-intersecting.

## White nodes succeed

***Claim 3:*** White nodes have a valid choice.

*Proof:* Consider this auxiliary bipartite graph $H'$:

- $d$ blue nodes, one for each incident edge $e$.
- $512rd$ orange nodes, one for each new color in $K$.
- You add a "strong" edge from $e$ to $k$ if $k \in S(e)$.
- You add a "weak" edge from $e$ to $k$ if $k \in N(c(e)) \setminus S(e)$.

Note that each blue node has $r+1$ strong neighbors and $3r-1$ weak neighbors.

Since $N(c)$ are expanding, if you select any subset $A$ of blue nodes, their "strong + weak" neighborhoods cover at least $3rA$ orange nodes. The "weak" neighborhood can cover at most $(3r-1)A$ orange nodes. So the "strong" neighborhoods must cover at least $A$ orange nodes. To recap, the "strong" neighborhoods of any $A$ blue nodes cover at least $A$ orange nodes. So by Hall's theorem, there is a matching among the "strong" edges of $H'$ that matches all blue nodes with distinct orange nodes. So this way we are able to select for each incident edge $e$ a distinct new color $k(e)$.

## FIXME: Improvements

One can apparently improve on this somewhat by changing the magic values as follows:

- $4r \to 2r+1$
- $3r \to r+1$
- $r+1 \to r+1$
- $512 \to 48$

Then things are hopefully less arbitrary and better-motivated. Both Hall arguments are "tight":

- You start with sets of size $2r+1$.
- Since you have expansion $r+1$, you can choose subsets of size $r+1$ in the first Hall argument.
- And then you have only $r$ weak edges, so expansion minus weak is still giving $1$ in the second Hall argument.
