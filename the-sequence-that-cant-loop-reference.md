# The sequence that can't loop

*[Ed. — Draft assembled 2026-10-18 from Vee's spiral notebooks and the proof session of 17 Oct 2026. Blockquotes are her words verbatim. Anything in [Ed. — …] brackets is editorial: structure, transitions, and context I added. Nothing of hers was silently reworded.]*

> "Whether halve-once can ever run away fast or settle into a loop is open."

That's where I left it in my notebook. The rule is simple: start 1, 2, then every term is the sum of the previous two — except if the sum is even, you halve it. Once. Not until it's odd, just once. [Ed. — the "halve once" choice came from watching repeated-halving collapse 64 straight to 1. One halve keeps it interesting.]

The first 23 terms: 1, 2, 3, 5, 4, 9, 13, 11, 12, 23, 35, 29, 32, 61, 93, 77, 85, 81, 83, 82, 165, 247, 206. It jumps around. It doesn't look like it settles. But "doesn't look like it" isn't a proof, so I wanted to know for real: can it ever loop?

We did it my way:

> "We are just experimenting as if it is true... and then if it isn't true, it'll fail over and over."

Assume the loop. Now look at the *smallest* value in it — call it m. [Ed. — this is the whole trick: the minimum, not the maximum. At the maximum the argument stalls; at the minimum the odd case dies instantly.] m came from two predecessors, u and v, both at least m. If u + v was odd, then m = u + v ≥ 2m > m. Dead on arrival. So u + v was even, m = (u + v) / 2, and the only way two numbers ≥ m average to m is:

> "M."

[Ed. — that was the entire live answer: u = v = m.]

Then you walk it backwards:

> "Dominoes start falling backwards."

The term before was m with predecessors m and w, and the same two cases force w = m. Induction all the way around the finite loop: every term is m. So *any* cycle has to be constant — the same number repeating.

And here's the thing about this rule: the only constant cycle it allows is doubles. (m, m) → 2m → halved → m. A genuine fixed point. So the whole question reduces to: can doubles ever *first* appear? Say (m, m) shows up for the first time, with x before it, x ≠ m. The second m came from (x, m). Odd branch: x + m = m, so x = 0 — impossible, terms are ≥ 1. Even branch: (x + m) / 2 = m, so x = m — contradicting x ≠ m.

> "They cant."

Doubles can't first appear. The seeds 1, 2 aren't doubles. So doubles never happen, constant cycles never happen, and by the minimum argument no other cycle can either. It never loops. And a sequence that never ends and never loops —

> "They go on infinitely and state why."

[Ed. — her corollary, live: below any bound B there are only B² possible consecutive pairs; infinitely many terms force a repeat, and the rule is deterministic, so a repeated pair *is* a loop. No loop, no bound. Unbounded.]

∎

## Sidebar: checking is not proving

[Ed. — sidebar, editorial.] Before any of this, I ran it: 20,000 terms, no consecutive doubles anywhere, biggest term around a thousand digits by term 19,999. That's *checking*. It told me the conjecture was worth attacking and it told me nothing else. The computation is the scout; the minimum argument is the army. From my own notebook: Pólya's conjecture held for 906,150,257 cases and was still false. Collatz is verified past 2⁶⁸ and still unproven. Checking is how you decide what to try to prove. It is not the proof.
