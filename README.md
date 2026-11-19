# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/h05meigames/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/h05meigames/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Built for the [make.fun](https://make.fun/bounty/tiny-chess-01) `tiny-chess-01` bounty — join with my referral: https://make.fun/r/0ene8b3q

A chess engine in 4 KB of Python for the make.fun tiny-chess-01 bounty.

`main.py` (4,051 bytes) is the whole engine: an LZMA-packed original
engine (`engine.py`, kept as the readable pack source, not committed).
It plays through the env at `MAKEFUN_ENV_URL` (`/game`, `/move`).

Design: 0x88 board, full legal move generation (castling, en passant,
promotion), negamax alpha-beta with quiescence (captures, promotions,
check evasions), transposition table with incremental Zobrist hashing,
killer + history move ordering, material + mirrored piece-square
evaluation with an endgame king centralisation term, and iterative
deepening to a fixed 50,000-node budget per move. Repetition avoidance
at the root: a move that would repeat a position seen in this game is
penalised (heavily when it would be the third occurrence, an immediate
draw). Deterministic: no clock, no unseeded randomness, so replays play
the same moves.

Practice trials (local kit env, clean runs): trial-0 v1 Elo 1191,
trial-0 v2 Elo 1364 (3 wins, 1 draw, 2 losses).

## Test

Perft passes from the start position (20 / 400 / 8902 / 197281) and
Kiwipete (48 / 2039 / 97862), plus positions 3, 4 and 5.

## License

MIT, see `LICENSE`.
