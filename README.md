# MLB-Shift-Ban-Effects-Python

## Purpose
Starting in the 2023 Major League Baseball season, a rule was changed that banned defenders in the infield from placing themselves with 3 players on one side of the infield, and 1 player on the other side of the infield. The idea behind this rule change was to encourage more offense and hits to the pull side of the field.  The goal of this project is to use Python to quantify these effects in a way which we can compare the change in success league-wide and for individual hitters, potentially as a result of this shift ban.

## Process
### 1. Data Extraction/Cleaning
* First, I downloaded individual at-bat data from the MLB website, [Baseball Savant](https://baseballsavant.mlb.com), and compiled data from the 2022 season up to May 30, and from 2023 season up to May 30 for an equal comparison.  Using **Excel**, I cleaned the data by deleting unnecessary columns and insuring all data was accurate and consistent.
* Next, I loaded both the 2022 and 2023 data files into data frames using the **Pandas** package in **Python**.  Using data cleaning and mining methods such as aggregated functions and data frame merging, I calculated a statistic called "luck".  "Luck" measures the difference between the actual batting average of play or group of plays, and the [expected batting average(xBA)](https://www.mlb.com/glossary/statcast/expected-batting-average) of those plays based on a function of launch angle and exit velocity.  To put succinctly, a higher "luck" equates to more hits in a set of at-bats than you would statistically predict.

### 2. Data Manipulation
* Once I had the methodology for calculating my "luck" scores, I used **Pandas** to calculate the average "luck" league-wide broken down by ground balls, line drives, and fly balls for each of the years.  This allowed me to see any changes in the trends between 2022 and 2023 on a large scale.  Also in this file, I calculated the "luck" on ground balls and line drives for plays in 2022 that specifically had an infield shift on to examine how effective utilizing the shift was. This work can be found in the [EffectOnLeague notebook](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/blob/main/EffectOnLeague.ipynb).
* The next aspect I wanted to examine was the effect on individual hitters.  While the sample size is not too large for each of them, some exploration can be done that may help explain some of the differences in success for players from 2022 into 2023. In order to calculate "luck" for individual hitters, some addition work in **Pandas** was required.  This is where I hit a bit of a snag trying to aggregate multiple calculated fields by player_name.  To work around this, I created seperate data frames for each of the necessary fields, and merged them back together to calculate the increases in "luck" scores. Increases in "luck" scores were calculated for each hitter for ground balls and fly balls, then I calculated a weighted average of the two scores to get a final overall "luck" increase for each hitter. This work can be found in the [EffectOnPlayers notebook](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/blob/main/EffectOnPlayers.ipynb). The data for all the final scores was exported and can be found in the [luck_increase.csv file](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/blob/main/luck_increase.csv).

### 3. Data Visualization
* Now that I had the data on the desired final values, I wanted to visualize the data in a way that showed the wide range of "luck" increases between players while highlighting the ones that stood out the most.  To accomplish this, I used the **Python** library **MatPlotLib**. The resulting scatterplot plotted each players ground ball "luck" increase vs. their line drive "luck" increase, and then each player's point was colored on a scale corresponding to their overall "luck" increase. Finally, I annotated the graph with the names of the top 5 and bottom 5 players in terms of overall "luck" increase. This process can be found in the [PlayerPlots notebook](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/blob/main/PlayerPlots.ipynb), with the resulting visualization being shown below.

![image](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/assets/120417529/54a3da2c-b2dd-425f-b6d8-e05a13c883e2)

## Conclusions
#### 1. The final results of the effects league-wide are as follows:
* Ground Ball "luck" increased by 0.011 from 2022 to 2023
* Line drive "luck" increased by 0.007 from 2022 to 2023
* Fly ball "luck" decreased by 0.010 from 2022 to 2023
* With an infield shift on in 2022, ground ball "luck" was -0.031 and line drive "luck" was -0.011.

Therefore, we can conclude that the overall, taking away the shift may be a contributor to more hits on ground balls and line drives, while outfield positioning and defense may be getting better. In addition, we know that the infield shift was successful in causing hitter's "luck" on ground balls and line drives to be down quite significantly.
#### 2. The final results of the effects on individual hitters are as follows:
* "Luck" increases for different hitters do not seem to follow specific trends to the naked eye. This highlights the "randomness" element to baseball that makes it so unpredictable and exciting.
* The biggest luck increaser is Jack Suwinski at an increase of 0.169 in overall luck! Hopefully, he is enjoying it!
* The biggest luck decreaser is Chris Taylor at a decrease of 0.153 in overall luck! As a fan of Taylor's, I hope his luck turns positive soon!

For individual players, I we do not have a great enough sample size to conclude with certainty that their "luck" changes are due to the shift ban.  However, it is fun to look at and analyze to see which player's "luck" has changed the most in one year, and why that might be. The shift ban could be a predictor, but more data would be necessary to say with certainty.

## Areas of Expansion
* One area of expansion would be to revisit this project in 5 years, and look at a much greater sample size from before and after the shift was banned. This would either confirm or refute the our conclusions about these trends to a stronger degree.
* Another area of expansion would be to include other stats and factors into a regression model to help explain and subsequently predict changes in "luck". While the shift ban is one aspect that is different for hitters this year, other factors such as pitcher spin rate or fielding ability on tough plays may explain some of the variance.
* The last area of expansion I would consider would be to view the "luck" statistic from the pitchers perspective. This would mean that a positive "luck" for a pitcher would occur when less hits are given up in a set of at-bats than would be expected statistically.
