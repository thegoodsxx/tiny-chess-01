# make.fun tiny-chess-01 entry

An entry for the make.fun tiny-chess-01 competition.

## The 4,096-Byte Rule

Competition rules require the complete engine to fit within a single `main.py` file of at most 4,096 bytes as committed. The bot runs on Python 3.13 using only standard library modules and cannot access external files. The entire repository is capped at 8,192 bytes.

## Engine Design

The engine executes from a compressed single-file payload implementing competitive chess logic:

- **Negamax with Quiescence**: Alpha-beta negamax search coupled with quiescence search on tactical captures to eliminate horizon artifacts.
- **Piece-Square Tables**: Material values paired with piece-square tables that taper positional evaluations from middlegame to endgame.
- **Iterative Deepening**: Iterative depth progression prioritizing strong moves from transposition tables, MVV-LVA, and killer moves.
- **Fixed-Node Deterministic Search**: Search terminates on a strict node budget (40,000 nodes) rather than a clock, ensuring reproducible move decisions across replay trials.
