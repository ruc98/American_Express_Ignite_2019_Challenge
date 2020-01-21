# American_Express_Ignite_2019_Challenge
Winner of Competition hosted by AmEx

## Problem Statement
Cricket Analytics using RNN for modelling a cricket match.
To predict the win probability of a match at regular intervals during the match given the ball-by-ball stats.
The LSTM/GRU Model will take as input the total ball-by-ball data available as well as the match details
available in the training dataset. It should be able to give as output either directly the win probability at
any time stamp or runs or any other metric from which win probability can be determined.

## Dataset
Dataset used contains ODIs from 1971 onwards.

https://cricsheet.org/downloads/

No of matches = 1597 ODIs

No of overs in an inning: 50

Rows: per ball details

Attributes:

Each ’ball’ line has the following fields:

* The word ’ball’ to identify it as such
* Innings number, starting from 1
* Over and ball
* Batting team nam
* Batsman
* Non-striker
* Bowler
* Runs-off-bat
* Extras
* Kind of wicket, if any
* Dismissed played, if there was a wicket

It also has the following match statistics

team, gender, season, date, series, match number, venue, city, toss winner, toss decision, player of match,
umpire,umpire ,tv umpire ,match referee, winner, winner runs.

## Comparison between four different models

Models studied:

1. All overs input and single output:
Model checkpoint: cric prediction batch.pth
(Match prediction batch.ipynb)

2. All overs input and multi output:
Model checkpoint: cric prediction all output batch.pth
(Match Prediction all output batch.ipynb)

3. Random sample input and single output:
Model checkpoint: cric prediction M1B1 randomsample.pth
(Match Prediction M1B1 Architecture batch.ipynb)

4. Input as cumsum of runs:
Model checkpoint: cric prediction cumsum.pth

## Conclusion:
• The above model is the current best performing model.
• Right from the 10th Over, it predicts 83% of the matches correctly into win or lose!
• The accuracy of predicting the match increases further to around 86% at the 20th Over and 88% at
the end of 30th Over. Which increases to 96.4% at the end of the match.
• However, at the end of the match, the model should be predicting 100% results as correct given the
target score of first innings and all the runs in the second innings but somehow the model fails to
capture this trivial result.
• One reason for this is the extra balls which increases the total number of balls to 321 instead of 300
as the RNN requires fixed length sequences for every data point.This results in data imputation for
other matches which may cause confusion in the model.
• Other reason is due to abandoned matches due to unforeseen situations like the rains which resulted
in deciding the winning team by some other algorithm rather than the general one or may lead to
match ties in which case the win is ambiguous. However, except these matches, the model predicts
most of the matches correctly in the end.
• The model can be deployed in practice to predict matches after the 10th Over as the accuracies
are influential for the first 10 overs. It goes from 63% after 1st Over, 72.4% by 5th Over to 83% by
the 10th Over.
