---
title: "I secretly tracked my friends' online poker games, and here's what I found."
collection: analysis
type: "Poker"
permalink: /analysis/poker_strategy_map
---

Sincerest apologies to my friends.

I started playing regular online poker games with a group of friends during lockdown. Without telling them, I began logging every bet, call, raise and fold using a VBA-based Excel tracker. There were two significant findings.

## A leopard never changes its spots.
The [three most important metrics in poker](https://pokercopilot.com/essential-poker-statistics) are:
- Voluntarily Put $ in Pot (VPIP): how often you voluntarily pay money into a hand before seeing the flop
- Pre-flop Raise (PFR): how often you raise before the flop is seen
- Post-flop Aggression Frequency (Agg): how aggressively you play postflop

Ideally, the VPIP should be 15-20%, the PFR should be 2-3% lower than the VPIP, and the Agg should be 50-60%.

In these scatter charts, each player is represented by a different symbol, and each of their games is plotted as a different point. The points belonging to each player are clustered in the same region, which suggests that each player's strategy is very consistent between games. This can be exploited by opponents - for example, Player B probably needs a strong hand if they see the flop so should be treated warily, whereas Player F sees too many flops and can be milked more aggressively.

<iframe width="900" height="300" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/poker_pre_flop_scatter.html"></iframe>
<iframe width="900" height="300" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/poker_post_flop_scatter.html"></iframe>

## Best practices are really best practices.
If you search the web for "tips for amateur poker players", you'll find helpful articles [[1](https://medium.com/bobs-economics/top-tips-for-amateur-poker-players-431d5eddc13d), [2]https://www.pokerlistings.com/11-simple-tricks-you-can-use-to-crush-your-poker-home-game)] containing a few ground truths: don't drink too much, don't see too many flops, and be decisive when you choose to see them.

In our friends' games, the most successful players were also the ones who stuck to the pre-flop rules of low VPIP and high PFR/VPIP the most often.  It's nice when practice validates theory! The post-flop aggression was less clear-cut.

| Player | Net Winnings | VPIP | PFR | PFR/VPIP | Agg |
|:------:|-------------:|:----:|:---:|:--------:|:---:|
|    D   |      $107.22 |  38% | 27% |    72%   | 32% |
|    B   |       $33.67 |  26% | 21% |    80%   | 28% |
|    A   |       $18.22 |  66% | 21% |    32%   | 25% |
|    E   |       -$6.53 |  48% | 40% |    84%   | 36% |
|    C   |      -$30.33 |  42% | 43% |   100%   | 38% |
|    F   |     -$122.23 |  83% | 54% |    65%   | 31% |

After logging the data with a VBA-based tracker in Microsoft Excel, I used Python’s pandas and Plotly libraries for the data manipulation and visualisations respectively. Check out the Jupyter notebook [here](https://github.com/luke-fitz/projects/blob/main/poker/poker_strategy_map.ipynb).
