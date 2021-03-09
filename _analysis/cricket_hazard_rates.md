---
title: "Batting Hazard Rates in Test Cricket"
collection: analysis
type: "Cricket"
permalink: /analysis/cricket_hazard_rates
---

Understanding when batters are likely to lose their wicket

If you've ever studied for actuarial exams, the little orange book of mortality tables is like an old friend. It contains the answers to some of life's great questions, like the odds of a man on his 92nd birthday making it to 93<sup>[1](#qx)</sup>.

I created the equivalent set of hazard rates across a Test cricket innings. Here's how you read them: given that a batsman has made _N_ runs (the x-axis), what is the probability of them being dismissed before the next run (the y-axis)?

<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/batting_hazard_rates.html"></iframe>

There's a clear "excess mortality" bump between 90 and 120, owing first to the nervious nineties, and then to the proclivity to throw your wicket away after reaching 100 through either boredom or fatigue. This table lists the players with the highest conversion rate from 90 to 120, given a minimum of fifteen opportunities.

| Player          | Innings of 90+ | % where reached 120 |
|-----------------|----------------|---------------------|
| DG Bradman    | 27             | 88.9%               |
| JE Root       | 21             | 85.7%               |
| WR Hammond    | 20             | 80.0%               |
| CA Pujara     | 18             | 77.8%               |
| Younis Khan   | 32             | 75.0%               |
| KC Sangakkara | 39             | 74.4%               |
| GC Smith      | 28             | 71.4%               |
| PA de Silva   | 20             | 70.0%               |
| BC Lara       | 40             | 70.0%               |
| GS Sobers     | 26             | 69.2%               |

In a word, ruthless. These cricketers aren't slaves to the base-10 number system.

The other end of the spectrum seems to comprise opening batsmen, romantic dashers or occasionally, <a href="https://www.youtube.com/watch?v=8kxkEFaPAUI">both</a>.

| Player            | Innings of 90+ | % where reached 120 |
|-------------------|----------------|---------------------|
| KD Walters      | 15             | 20.0%               |
| PBH May         | 16             | 25.0%               |
| AI Kallicharran | 17             | 29.4%               |
| RR Sarwan       | 17             | 29.4%               |
| DR Martyn       | 15             | 33.3%               |
| MJ Slater       | 23             | 34.8%               |
| MC Cowdrey      | 24             | 37.5%               |
| ME Waugh        | 20             | 40.0%               |
| TW Graveney     | 15             | 40.0%               |
| G Boycott       | 24             | 41.7%               |

I used Python's BeautifulSoup, pandas and Plotly libraries for the web scraping, data manipulation and visualisations respectively. Check out the Jupyter notebook [here](https://github.com/luke-fitz/projects/blob/main/cricket/batting_hazards.ipynb).

<sup><a name="qx">1</a></sup> It's only 80.3%. Don't buy green bananas.

