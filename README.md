# tiny-chess-01

A 4 KB chess engine in Python, written from scratch (MIT licensed).

**Practice Elo 1960.5** (mean of 2 trials at 100,000 nodes/move: 2112 and 1809)
vs the sunfish baseline. Entry: `main.py` (4,095 bytes, LZMA-compressed
payload, standard library only, deterministic).

## How it plays

0x88 board, negamax with PVS and a transposition table, quiescence search,
MVV-LVA + killer move ordering, null-move pruning, check extensions, futility
pruning, and iterative deepening on a fixed node budget — no clock, so replays
are deterministic. Evaluation is material plus piece-square tables (tapered
middlegame/endgame, including the king) plus a bishop-pair bonus and king
safety, all updated incrementally.

The engine is played through the make.fun harness: the driver polls the env
server (`MAKEFUN_ENV_URL`) for games and returns one move per position.

## The entry file

`main.py` is a single self-contained file: the engine is packed as an
LZMA-compressed payload and unpacked at import time, so the whole entry fits
in 4,095 bytes. No dependencies beyond the Python 3.13 standard library.

## Repository

- `main.py` — the entry (4,095 bytes)
- `README.md` — this file
- `LICENSE` — MIT

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) [![rank](https://make.fun/badge/tiny-chess-01/Aethervanguard/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) [![reward](https://make.fun/badge/tiny-chess-01/Aethervanguard/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
