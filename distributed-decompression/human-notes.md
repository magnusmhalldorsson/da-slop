# Distributed decompression

(Notes by Jukka Suomela)

Yes the ideas make sense to me, and most importantly they generalize so that they can be used to simplify other stuff that we did in our DISC paper.

Here is a very simple data encoding scheme using just 1 bit per node:

- Mark cluster centers with 1 surrounded by all-0.
- Then find Voronoi cells.
- Then find using some deterministic algorithm a maximal matching M in each cell.
- Then encode data so that each edge of M is marked either 1–1 or 0–0, and this gives you conveniently 1 bit of storage per edge of M, and the size of M is within factor ≈ Delta of the size of the cell.

That's it, isolated 1 is always a cluster center, and encoding and decoding is trivial. And then you can just make your cells larger and this way fit more data per cell. (And you can encode also data related to many different problems here in the same cells.)

Now for compression we do something slightly different as we aren't using 1 bit per node. But the basic idea is very similar. If we have e.g. labels 0,1,2,3 (2 bits) available, we use 0 surrounded by all-1 to indicate cluster centers; these are the only places with an isolated 0. Then for each edge of M we can use any label combination except 1–0 / 0–1, so it is 14 combinations per edge of M (out of 16 possible). And for unmatched nodes we have 3 combinations (out of 4 possible). So this gives you plenty of data storage yet a trivial way to detect cluster centers. 

Then you could use the LLL sledgehammer to encode orientations like we did, but apparently this encoding gives enough storage that Hall suffices.

The catch is that we have information-theoretically so much slack that even if we "waste" this specific patter 0-surrounded-by-all-1 for just marking cluster centers, there is still tons of room for information storage per cell.
