# tiny-chess-engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/calebakinjomo/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/calebakinjomo/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python, written for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty. `main.py` (4,076 bytes) is the whole engine: Python 3.13 standard library only, it reads, imports or execs no other file.

## How it plays

- 0x88 board, negamax with alpha-beta pruning
- Quiescence search (captures, promotions, and check replies)
- Transposition table with fixed-seed Zobrist keys
- Killer-move and MVV-LVA move ordering
- Null-move pruning
- Evaluation: material + piece-square tables (mirrored at import) + bishop pair, with a separate endgame king table
- Deterministic: iterative deepening to a fixed budget of 150,000 nodes per move — no clock, no randomness

## Protocol

The engine talks to the environment at `MAKEFUN_ENV_URL`: `POST /game` serves the game in play, `POST /move` plays a move in UCI notation, `POST /resign` resigns.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=hdavhdvz&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
