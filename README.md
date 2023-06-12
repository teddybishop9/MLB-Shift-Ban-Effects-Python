# MLB-Shift-Ban-Effects-Python

## 1. Purpose
Starting in the 2023 Major League Baseball season, a rule was changed that banned defenders in the infield from placing themselves with 3 players on one side of the infield, and 1 player on the other side of the infield. The idea behind this rule change was to encourage more offense and hits to the pull side of the field.  The goal of this project is to use Python to quanitify these effects in a way that could be used to compare the change in success for individual hitters.

## 2. Process
* First, I downloaded individual at-bat data from the MLB website, [Baseball Savant](https://baseballsavant.mlb.com), and compiled data from the 2022 season up to May 30, and from 2023 season up to May 30 for an equal comparison.  Using Excel, I cleaned the data by deleting unnecessary columns and insuring all data was accurate and consistent.
* Next, I loaded both the 2022 and 2023 data files into data frames using the **Pandas** package in **Python**.  Using data cleaning and mining methods such as aggregated functions and data frame merging, I calculated a statistic called "luck".  "Luck" measures the difference between the actual batting average of an event or group of events, and the expected batting average(xBA) of those events based on a function of launch angle and exit velocity.
* 

## 3. Conclusions

## 4. Areas of Expansion
