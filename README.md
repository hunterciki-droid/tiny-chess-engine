# Tiny Chess — 4 KB engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/hunterciki-droid/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/hunterciki-droid/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A from-scratch chess engine in one Python file (stdlib only). 0x88 board,
incremental material + piece-square evaluation, Zobrist hashing, a
transposition table, MVV-LVA captures, killer and history ordering, null-move
pruning, and alpha-beta with iterative deepening on a fixed 50,000-node
budget per move (never a clock), plus quiescence search over captures,
promotions and replies to check. Repetition and insufficient-material draws
are scored inside the search.

Practice Elo (6-game trials vs the house gauntlet, depth-2 .. nodes-500k):
trial-0: 1,654 (5W/1L), trial-1: 1,279 (3W/3L), trial-2: 1,451 (3W/2D/1L);
mean 1,461. House baseline (sunfish 4 KB) rates ~1,365 mean on the same
trials; the floor to enter the final is 1,154. Beats all three fixed-depth
house engines in nearly every trial; competitive with the node-budget ones.

`main.py` is the whole engine (<= 4,096 bytes as committed, packed with the
kit's `makefun compress` from the readable source written in this session).
It reads no other file and stores no data outside its own bytes.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:18080 python3 -P -s main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=tc0h9t5n&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
