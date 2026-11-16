# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Chiiii318/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Chiiii318/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python. `main.py` is the whole
engine: it talks to the tiny-chess-01 env at `MAKEFUN_ENV_URL` and plays
the house gauntlet — eight anchored alpha-beta engines from depth-2 up
to a 2,000,000-node search — one game after another.

Inside the 4 KB: a negamax alpha-beta search with a transposition table,
quiescence search with in-check evasions, check extensions, null-move
pruning, late-move reductions, killer-move ordering, and tapered
piece-square tables, all under a fixed node budget — never a clock — so
every position always gets the same move.

The board is a 120-character string that rotates after every move, so
the side to move is always the uppercase army at the bottom. The root
is repetition-aware: it replays the game's moves, and when the engine
stands better it will not drift into a threefold draw, while a worse
position is allowed to take the draw.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 main.py
```

Point `MAKEFUN_ENV_URL` at a tiny-chess-01 env; the engine plays every
game of the gauntlet until the env reports the run done.

---

<sub>Entered on [make.fun](https://make.fun/?ref=b1txph5j&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
