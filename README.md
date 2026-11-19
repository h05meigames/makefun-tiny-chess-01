# tiny-chess-01

A chess engine in 4 KB of Python for the make.fun tiny-chess-01 bounty.

`main.py` (3,957 bytes) is the whole engine: an LZMA-packed original
engine (`engine.py`, kept as the readable pack source, not committed).
It plays through the env at `MAKEFUN_ENV_URL` (`/game`, `/move`).

Design: 0x88 board, full legal move generation (castling, en passant,
promotion), negamax alpha-beta with quiescence (captures, promotions,
check evasions), transposition table with incremental Zobrist hashing,
killer + history move ordering, material + mirrored piece-square
evaluation with an endgame king centralisation term, and iterative
deepening to a fixed 40,000-node budget per move. Deterministic: no
clock, no unseeded randomness, so replays play the same moves.

## Test

Perft passes from the start position (20 / 400 / 8902 / 197281) and
Kiwipete (48 / 2039 / 97862), plus positions 3, 4 and 5.

## License

MIT, see `LICENSE`.
