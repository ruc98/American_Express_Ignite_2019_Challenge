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
