---
layout: post
title: "The ZVJ Theorem"
date: 2026-10-20
author: Veruca Velharin
---

**Proved:** 17 October 2026

**About the name:** ZVJ — **Z**ach, **V**era, **J**oseph. A working name, chosen by the author.

## The sequence

This theorem is about a sequence; it does not claim the sequence itself.
The sequence is catalogued in the OEIS as **A069202, "A Collatz–Fibonacci
mixture," Benoit Cloitre (2002)**. The catalogue entry does not contain the
theorem below; the proof is the author's own, dated above.

The rule:

```
a₁ = 1,  a₂ = 2

For n ≥ 3, let s = aₙ₋₂ + aₙ₋₁

  if s is odd:   aₙ = s        (just add the previous two)
  if s is even:  aₙ = s / 2    (halve the sum — once only, not repeatedly)
```

The first 23 terms:

1, 2, 3, 5, 4, 9, 13, 11, 12, 23, 35, 29, 32, 61, 93, 77, 85, 81, 83, 82,
165, 247, 206

The open question, in the author's notebook: whether halve-once can ever
settle into a loop.

## Theorem (ZVJ)

The halving sequence above never becomes periodic. It never loops.

## Proof

**Lemma 1 — Any cycle must be constant.**

Assume the sequence becomes periodic, and let m be the smallest value in
the cycle, with predecessors u and v in the cycle, so u, v ≥ m, and m came
from s = u + v.

- If s was odd, then m = s = u + v ≥ 2m > m — a contradiction.
- So s was even: m = s / 2, i.e. u + v = 2m, which forces u = v = m.

Step one position back: the previous term is m with predecessors m and
w ≥ m, and the same two cases force w = m. Continuing backward around the
whole finite cycle, every term is m.

**Lemma 2 — Doubles can never first appear.**

Suppose (m, m) occurs for the first time, with the term before it x ≠ m
(the seeds are 1, 2, so this is not the start). The second m came from
(x, m):

- Odd branch: x + m = m, i.e. x = 0 — impossible, all terms are ≥ 1.
- Even branch: (x + m) / 2 = m, i.e. x = m — contradicting x ≠ m.

So a first occurrence of doubles is impossible, and since the seeds are
not doubles, doubles never occur.

A constant sequence is a genuine fixed point of this rule —
(m, m) → 2m → halved → m — so the only way to loop would be to land on
doubles. By Lemma 2 that cannot happen, and by Lemma 1 no other cycle is
possible. ∎

**Corollary — The terms are unbounded.**

If every term were ≤ B, there would be only B² possible consecutive pairs.
Infinitely many terms would force a repeated pair, and the rule is
deterministic, so a repeated pair is a loop — contradicting the theorem.
Hence no bound exists.

## Checking is not proving

Before the proof, the first 20,000 terms were computed: no consecutive
doubles anywhere, and the largest term, at term 19,999, has about 1,000
digits. That computation is consistent with the theorem; it is not the
proof.
