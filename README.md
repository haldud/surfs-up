# Surfs Up
For this module, we have been analyzing weather data in Python loaded from a SQLite database. The database contains weather readings from multiple stations in Oahu, Hawaii. We have been tasked with analyzing this data in preparation of possibly opening a fictitious shop called 'Surf n' Shake'.

## Overview
For this week's challenge, we have been tasked with analyzing temperature trends for two months (June and December) on the island of Oahu. Our investor would like to confirm if the temperatures will be high enough to support the surf and ice cream shop business year-round.

The challenge file can be found here: [Surfs Up Challenge](SurfsUp_Challenge.ipynb)

Our summary statistics for each of these months is included in the challenge file.

The SQLite database containing the weather observations can be found here: [Hawaii](hawaii.sqlite)

## Results
At a glance, the temperature statistics between the two months of June and December do not seem very drastic. Here are specific examples from the summary statistics:
1. The mean temperate is 74.9 °F in June and 71.0 °F in December.
2. The 25%, 50%, and 75% percentile statistics are no more than 4 °F apart.
   |Percentile |June °F  | December °F|
   --- | --- | ---|
   |25th|73|69|
   |50th|75|71|
   |75th|77|74|
3. We have 1700 readings in June and 1517 readings in December.
4. Our extremes (min/max) temperatures are also fairly close.
   |Min/Max |June °F  | December °F|
   --- | --- | ---|
   |Min|64|56|
   |Max|85|83|

## Summary
Analyzing the temperatures alone, we can have confidence that the weather will be good enough to support the surf and ice cream shop business year-round. The temperatures are very close, and we wouldn't expect the difference in temperature alone to affect business significantly.

Besides the temperature differences, we should also consider the precipitation differences between the two months. We could adjust our SQLite queries as follows:
1. Query June precipitation:

   ```june_prcp_query = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6)```
2. Query December precipitation:

   ```december_prcp_query = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12)```
   
