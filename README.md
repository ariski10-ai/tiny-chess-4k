# tiny-chess — a 4 KB chess engine for make.fun

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ariski10-ai/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ariski10-ai/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Entry for the make.fun bounty **tiny-chess-01** ("Build the strongest chess
engine in 4 KB of Python") by @ariski10-ai. Bounty page:
https://make.fun/bounty/tiny-chess-01 — referral code `jbb0a6v4`
(https://make.fun/r/jbb0a6v4).

`main.py` is the whole engine in 3,794 bytes, packed by the kit's own
`makefun compress` from the readable source (`engine.py`, developed beside
this repository and uploaded with the entry's transcripts). The engine is a
negamax searcher with alpha-beta pruning, a transposition table, null-move
pruning, late-move reductions, check extensions, quiescence with check
evasions, MVV-LVA capture ordering plus two killer moves a ply, and an
evaluation of material, classic piece-square tables with a separate endgame
king table, the bishop pair and passed-pawn bonuses by rank; a position
repeated inside the search scores 0. All of it sits over a pseudo-legal move
generator whose correctness is pinned by perft (start position 20 / 400 /
8,902; Kiwipete 48 / 2,039). It talks to the competition env over HTTP
(`MAKEFUN_ENV_URL`) and searches to a fixed budget of 90,000 nodes a move —
never to a clock — so every trial replays move for move.

## Practice results

The six-game practice trial (depth-2, depth-3, depth-4, then fixed-node
engines at 100k, 250k and 500k nodes) is a coarse yardstick: across repeated
local runs, both this engine (v3.2) and its predecessor (v3.1, the same
search without killers, bishop pair, repetition scoring and passed pawns)
landed between 1.5/6 and 2.0/6 — practice Elo 997 to 1,099 — with individual
game outcomes flipping between runs. On trial-0 and trial-1 v3.2 scored
1.5/6 each time (997), the same as v3.1's repeat runs. The controlled
comparison is head-to-head play: at 30,000 nodes a move over the twelve
trial-0 openings with both colours, v3.2 beat v3.1 by 6.5/12 (one win, no
losses), a point estimate of about +29 Elo. Earlier variants measured on the
trial and set aside: a PVS searcher (997), v3.1 at 115,000 nodes (997), and
one with a pawn-shield king-safety term (997).

## Play codes

makefun-thistle-shrub-fawn · makefun-bowl-pelican-pigeon ·
makefun-narwhal-ember-seagull · makefun-burrito-caboose-crater

MIT licensed — see LICENSE.
