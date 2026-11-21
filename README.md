# First Mertens crossings in Yokoi’s family

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24410813.svg)](https://doi.org/10.5281/zenodo.24410813)

This result is now maintained in [quadratic-mertens-first-crossings](https://github.com/leecrossley/quadratic-mertens-first-crossings/tree/main/results/yokoi-mertens-crossing-bounds). This repository is archived and keeps its releases and DOI.

Daniel R. Johnston’s Problem 8 asks for an upper bound on the first sign change of the prime-ideal Mertens error in a family of number fields. Here the family is $\mathbb Q(\sqrt d)$ with $d=m^2+4$ squarefree and $m$ positive and odd. Write $S_d$ for the first real crossing, with $S_d=+\infty$ if the error stays nonnegative. [2024 problem, pp. 4–5](https://arxiv.org/pdf/2407.03530#page=4)

**No finite constant bounds every field.** For every fixed real $B\ge2$, a positive lower proportion of the family have a finite first crossing strictly between $B$ and $B^2$. This includes arbitrarily late first crossings and holds unconditionally.

**A growing upper bound works for almost every field.** If $f(d)\to\infty$, however slowly, the proportion with $S_d<f(d)$ tends to one as the discriminant cutoff increases. The proof also gives a necessary worst-case growth rate for any proposed bound.

**Follow-up, 21 November 2026.** Under GRH for $\zeta(s)L(s,\chi_d)$, a separate proof gives $S_d<2^{2^{d^{30000}}}$ for every real quadratic fundamental discriminant, covering the fields left outside this density-one conclusion. [Proof, zero-location input and verification](https://github.com/leecrossley/yokoi-mertens-explicit-upper-bound/releases/tag/v1.0.0)

**Through discriminant 10,000, every field crosses before 526.** There are 45 fields. The largest first crossing occurs for $9413=97^2+4$, between 525.474356978253 and 525.474356978254. The second largest occurs for $d=1685$, between 36.195773681475 and 36.195773681476. The census checks entire real intervals between prime-ideal norms. [All 45 enclosures](evidence/census.tsv)

Counting from $x=2$ puts 37 of the 45 boundaries before the first ideal norm. In 11 fields the error is already negative at 2. The table also gives the infimum starting at the first ideal norm, with all ideals of that norm included. This leaves $d=9413$ first and puts $d=6245$ second, between 52.592121251681 and 52.592121251682. [Both sets of enclosures](evidence/census.tsv)

The proof connects the prime-window calculation to the distribution of quadratic $L$-values across fields. It uses results of Dahl and Kala, Granville and Soundararajan, and Diamond and Pintz. The earlier calculation for the two fields named in the question also gave a 7% bound for one small interval. [Full proof and prior work](PROOF.md) · [Earlier release](https://github.com/leecrossley/quadratic-mertens-first-crossings/releases/tag/v1.0.0)

## Reproduce the finite checks

Use Python 3.10 or later. The first calculation uses the standard library, the class number formula and a bound on the tail of a periodic Dirichlet series. The independent calculation uses Arb interval arithmetic, direct Dirichlet $L$-values and polynomial factorization. Both must reproduce every line of the census. The infinite-family results have analytic proofs in the note.

~~~sh
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements.txt
./verify-release.sh
~~~

The release includes the checksum manifest and the outputs used for comparison. [Recorded checks](evidence/check.txt) · [Manifest](SHA256SUMS)
