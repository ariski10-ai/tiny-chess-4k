# tiny-chess — a 4 KB chess engine for make.fun

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ariski10-ai/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ariski10-ai/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Entry for the make.fun bounty **tiny-chess-01** ("Build the strongest chess
engine in 4 KB of Python") by @ariski10-ai. Bounty page:
https://make.fun/bounty/tiny-chess-01 — referral code `jbb0a6v4`
(https://make.fun/r/jbb0a6v4).

`main.py` is the whole engine in 3,719 bytes, packed by the kit's own
`makefun compress` from the readable source (`engine.py`, developed beside
this repository and uploaded with the entry's transcripts). The engine is a
negamax searcher with alpha-beta pruning, a transposition table, null-move
pruning, late-move reductions, check extensions, quiescence with check
evasions, MVV-LVA capture ordering and classic piece-square tables with a
separate endgame king table, over a pseudo-legal move generator whose
correctness is pinned by perft (start position 20 / 400 / 8,902; Kiwipete
48 / 2,039). It talks to the competition env over HTTP (`MAKEFUN_ENV_URL`)
and searches to a fixed budget of 90,000 nodes a move — never to a clock —
so every trial replays move for move.

## Practice results

Measured on the kit's practice trial (six games: depth-2, depth-3, depth-4,
then fixed-node engines at 100k, 250k and 500k nodes), this configuration
scored 2.0/6 for a practice Elo of 1,099 — a win by checkmate over depth-2,
draws with depth-3 and the 250k engine, and losses to the rest. Three
variants were built and measured on the same trial and set aside: a PVS
searcher (997), the same engine at 115,000 nodes (997), and one with a
pawn-shield king-safety term (997). The submitted engine is the best of the
four measured configurations, not the newest one.

## Play codes

makefun-thistle-shrub-fawn · makefun-bowl-pelican-pigeon ·
makefun-narwhal-ember-seagull · makefun-burrito-caboose-crater

MIT licensed — see LICENSE.
