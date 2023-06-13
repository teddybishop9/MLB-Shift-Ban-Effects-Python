# MLB-Shift-Ban-Effects-Python

## Purpose
Starting in the 2023 Major League Baseball season, a rule was changed that banned defenders in the infield from placing themselves with 3 players on one side of the infield, and 1 player on the other side of the infield. The idea behind this rule change was to encourage more offense and hits to the pull side of the field.  The goal of this project is to use Python to quanitify these effects in a way that could be used to compare the change in success for individual hitters.

## Process
### 1. Data Extraction/Cleaning
* First, I downloaded individual at-bat data from the MLB website, [Baseball Savant](https://baseballsavant.mlb.com), and compiled data from the 2022 season up to May 30, and from 2023 season up to May 30 for an equal comparison.  Using **Excel**, I cleaned the data by deleting unnecessary columns and insuring all data was accurate and consistent.
* Next, I loaded both the 2022 and 2023 data files into data frames using the **Pandas** package in **Python**.  Using data cleaning and mining methods such as aggregated functions and data frame merging, I calculated a statistic called "luck".  "Luck" measures the difference between the actual batting average of play or group of plays, and the [expected batting average(xBA)](https://www.mlb.com/glossary/statcast/expected-batting-average) of those plays based on a function of launch angle and exit velocity.  To put succinctly, a higher "luck" equates to more hits in a set of at-bats than you would statistically predict.

### 2. Data Manipulation
* Once I had the methodology for calculating my "luck" scores, I used **Pandas** to calculate the average "luck" league-wide broken down by ground balls, line drives, and fly balls for each of the years.  This allowed me to see any changes in the trends between 2022 and 2023 on a large scale.  Also in this file, I calculated the "luck" on ground balls and line drives for plays in 2022 that specifically had an infield shift on to examine how effective utilizing the shift was. This work can be found in the [EffectOnLeague notebook](https://github.com/teddybishop9/MLB-Shift-Ban-Effects-Python/blob/main/EffectOnLeague.ipynb).
* The next aspect I wanted to examine was the effect on individual hitters.  While the sample size is not too large for each of them, some exploration can be done that may help explain some of the differences in success for players from 2022 into 2023. In order to calculate "luck" for individual hitters, some addition work in **Pandas** was required.  This is where I hit a bit of a snag trying to aggregate multiple calculated fields by player_name.  To work around this, I created seperate data frames for each of the necessary functions, and merged them back together to be able to calculate "luck" scores.

### 3. Data Visualization

## Conclusions

## Areas of Expansion
