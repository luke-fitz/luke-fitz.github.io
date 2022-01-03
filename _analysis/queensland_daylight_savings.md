---
title: "Daylight Savings in Queensland"
---

Should Queensland introduce daylight savings in summer, and if so, what parts of Queensland?

Amid the swirl of opinions in Queensland's daylight savings debate, there are two important points which I feel are not widely understood.

## 1. Queenslanders spoke loudly in the 1992 referendum
Ignore the 46/54 overall result -- it masks a clear geographical pattern. This cartogram shows the Yes vote in each electorate. There is strong support in the south-east (as high as 74% in Merrimac), strong antipathy in the north and west (only 10% in Tablelands and 8% in Warrego), and an exceedingly smooth progression in between.

<iframe width="400" height="800" frameborder="0" scrolling="no" src="https://luke-fitz.github.io/files/ds_ref_1992_cartogram.html"></iframe>

## 2. Daylight savings doesn't work in the tropics
Look at this map of the world. There are almost no regions between the Tropic of Cancer and the Tropic of Capricorn where daylight savings is observed. This is because sunrise and sunset times don't vary enough across the year for daylight savings to be beneficial. So if you're north of Rockhampton, daylight savings doesn't make much sense. It's more than just the cows fading!

<img width="67%" src="https://luke-fitz.github.io/files/ds_world_map_tropics.png">

Putting it all together, daylight savings doesn't seem feasible in northern or western Queensland. It has strong support in south-east Queensland. So why not an SEQ-only solution? It actually wouldn't be too difficult to implement: the existing local government areas form obvious boundaries, and there is sparse population at the boundary edges (which avoids the sort of confusion in Coolangatta-Tweed that we see today). Some US states enforce summer time at a county level, so it's not as ludicrous as it might seem.

I used Python's pandas and Plotly libraries for the data manipulation and visualisations respectively. Check out the Jupyter notebook [here](https://github.com/luke-fitz/projects/blob/main/daylight_savings/daylight_savings_referendum.ipynb).
