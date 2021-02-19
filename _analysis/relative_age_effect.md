---
title: "Relative Age Effect"
collection: analysis
type: "Cricket"
permalink: /analysis/relative_age_effect
---

Is there a relative age effect in cricket?

The <a href="https://en.wikipedia.org/wiki/Relative_age_effect">relative age effect</a> is the phenomenon where children born early for their age-level cohort are over-represented among elite performers in later life. A <a href="https://www.espncricinfo.com/story/how-much-does-the-relative-age-effect-impact-the-careers-of-cricketers-1246344">recent Cricinfo article</a> studied its impact on cricket by analysing the birth dates of two England Under-19 squads. To impart more rigour to these findings, I scraped player data from all Under-19 World Cups and Australian Men's Internationals between 2007 and 2020.

The age-group birthday cutoff is September 1 for junior cricket in Australia, New Zealand and England. There is clear evidence of the relative age effect: whereas you would expect 33.4% of players to be born between September and December<sup>[1](#seasonality)</sup>, these countries have had 62.8%, 59.8% and 39.1% respectively.

<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/relative_age_u19.html"></iframe>

Even more disheartening is the flow-on effect at senior level. The relative age effect has been just as strong in the Australian Senior Men's team as the Under-19 squad.

<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/relative_age_australia.html"></iframe>

How many potential greats have been lost to cricket before their tenth birthday?

I used Python's BeautifulSoup, pandas and Plotly libraries for the web scraping, data manipulation and visualisations respectively. Check out the Jupyter notebook [here](https://github.com/luke-fitz/projects/blob/main/cricket/relative_age_cricket.ipynb).

<sup><a name="seasonality">1</a></sup> Well, almost. The <a href="https://academic.oup.com/humrep/article/16/7/1512/693437">_Journal of Human Reproduction_</a> seems to be an authority on such questions.
