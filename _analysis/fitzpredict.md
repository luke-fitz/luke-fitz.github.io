---
title: "Under the hood of FitzPredict"
collection: analysis
type: "Cricket"
permalink: /analysis/fitzpredict
---

You can find the files [here](https://github.com/luke-fitz/projects/tree/main/fitzpredict).

Step 1: Scrape the training data using BeautifulSoup
------
Without access to a Test cricket database, I had to build my own data set. Fortunately, Cricinfo Statsguru came to the rescue. I used Python's BeautifulSoup package to scrape the [result data](https://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;filter=advanced;orderby=start;page=1;size=200;template=results;type=team;view=results) (the model target) and  [fall-of-wicket data](https://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;filter=advanced;orderby=start;page=1;size=200;template=results;type=fow;view=innings) (the model features) to create the training set.

In the interests of simplicity, I made two decisions to limit the scope of the model:
- Predict only the results of completed matches. Although predicting draws would be great, it would require extra contextual data as well as a more sophisticated model structure.
- Fit a parsimonious model of win likelihood, with three features only: innings number, number of wickets lost, and number of runs ahead or behind the opposition.

The modeling data set contained one row per unique score in the match. For example, Australia began the third innings of the [2020-21 Boxing Day Test](https://www.espncricinfo.com/series/india-in-australia-2020-21-1223867/australia-vs-india-2nd-test-1223870/full-scorecard) 131 runs in arrears. They scored four runs before losing the first wicket. The first six rows of training data are thus:

| match_id | innings | runs_diff | wickets | win_ind |
|----------|---------|-----------|---------|---------|
| 2398     | 3       | -131      | 0       | 0       |
| 2398     | 3       | -130      | 0       | 0       |
| 2398     | 3       | -129      | 0       | 0       |
| 2398     | 3       | -128      | 0       | 0       |
| 2398     | 3       | -127      | 0       | 0       |
| 2398     | 3       | -127      | 1       | 0       |

Step 2: Fit the model using scikit-learn
------
The model was trained on post-World War I data because batting averages [stabilised](
https://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;filter=advanced;groupby=decade;orderby=start;template=results;type=batting) after this point.

A logistic regression model was fit. Importantly, the modeled curves are monotonic with respect to wickets and runs. This guarantees that a team's likelihood of winning will increase when it scores a run or takes a wicket.

Equally importantly, the model fits the test data well.

<script>
    function go(loc){
      console.log(loc);
        document.getElementById('iframe').src = loc; 
    }
</script>

<div class="iframe_container">
    <form align="center">
        <input type="radio" name="iframe" value="type" checked onClick= "go('https://luke-fitz.github.io/files/fitzpredict_actual.html')"/>&nbsp;&nbsp;&nbsp;Actual &nbsp;&nbsp;&nbsp;  	
        <input type="radio" name="iframe" value="type" onClick = "go('https://luke-fitz.github.io/files/fitzpredict_predicted.html')"/>&nbsp;&nbsp;&nbsp;Predicted&nbsp;&nbsp;&nbsp;
    </form>
</div>
<div class="logins_details_container"><!--The top container-->
	<iframe width="900" height="600" frameborder="0" scrolling="no" id="iframe" src="https://luke-fitz.github.io/files/fitzpredict_actual.html"></iframe>
</div>

<img src="https://luke-fitz.github.io/files/fitzpredict_actual_vs_predicted.png">

Step 3: Deploy the model using Flask
------
I created a program to scrape Cricinfo live match scorecards, parse the features, and score the model.

I followed [this tutorial](https://towardsdatascience.com/how-to-easily-deploy-machine-learning-models-using-flask-b95af8fe34d4) for the Flask deployment. It was hosted on [PythonAnywhere](https://www.pythonanywhere.com/).
