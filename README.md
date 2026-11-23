# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/iqbalbeladaz/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/iqbalbeladaz/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python (`main.py`), built for
make.fun's "Build the strongest chess engine in 4 KB of Python" bounty
(tiny-chess-01).

It plays every game of the house gauntlet through the env at
`MAKEFUN_ENV_URL`, from a 0x88 board: iterative-deepening alpha-beta
search with PVS, a Zobrist transposition table, quiescence search over
captures and check evasions, MVV-LVA and killer move ordering, check
extensions, null-move pruning, late move reductions, and a material +
piece-square evaluation with a bishop-pair bonus. Repetition is handled
both inside the search and against the game's own history, which the
driver replays from the env's `start_fen` and `moves`. The search runs
to a fixed cumulative node budget of 110,000 nodes per move (never a
clock), so the same position always gets the same move and trials
replay exactly. Local practice on trial-0 scored 3.0 of 6 against the
house gauntlet (about Elo 1,275).

`main.py` is the readable source `engine.py` packed with the kit's own
`makefun compress` (an LZMA stream in a small stub), 3,236 bytes.

Run it with Python 3.13, standard library only:

    MAKEFUN_ENV_URL=<env origin> python3 -P -s main.py

MIT licensed (see LICENSE).
