# tiny-chess

A chess engine in at most 4,096 bytes of Python (`main.py`), built for
make.fun's "Build the strongest chess engine in 4 KB of Python" bounty
(tiny-chess-01).

It plays every game of the house gauntlet through the env at
`MAKEFUN_ENV_URL`: iterative-deepening alpha-beta search with a
transposition table, quiescence search over captures and check evasions,
MVV-LVA / killer / history move ordering, check extensions, repetition
detection inside the search, and a material + piece-square evaluation.
The search runs to a fixed node budget (never a clock), so the same
position always gets the same move and trials replay exactly.

Run it with Python 3.13, standard library only:

    MAKEFUN_ENV_URL=<env origin> python3 -P -s main.py

MIT licensed (see LICENSE).
