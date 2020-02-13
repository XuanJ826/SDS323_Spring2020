# SDS323 Exercise 1


## Data visualization: flights at ABIA

Considering the flights into and out of Austin, I am interested in what is the best day in a week and the best month in a year to fly to minimize delays. Therefore, I need to develop two models to answer these two questions. The two independent variables are DayOfWeek and Month separately. Based on the flights in and out of Austin, the dependent variable for into Austin is ArrDelay, while the dependent variable for out of Austin is DepDelay.

Besides these two variables, we need to consider other 15 variables on which variables to ignore and which variables to control:

 - Year all 2008: since the data are all from 2008, this variable can be ignored in this case.
 
 - DayOfMonth: we are analyzing the best month and day of week in this case, the day of month is unrelated since they are both time variable, so we can neglect this variable in this case
 
 - DepTime/CRSDepTime/ArrTime/CRSArrTime: These are data used to calculate the delay time for departure and arrival flights, so we can ignore them in this analysis.
 
 - UniqueCarrier/FlightNum/TailNum: In this analysis, we consider the delay time regardless of carrier information, so we ignore these three variables related to airline carrier.
 
 - ActualElapsedTime: The elapsed time is related to the air time, which may influence the delay time, so we will use the middle 50% of data which is the range between 57 and 164.
    
    min Q1 median  Q3 max   mean      sd     n     missing
     22 57    125 164 506 120.1822 61.4858 97659    1601
 
 - CRSElapsedTime: Since we have controlled the ActualElapsedTime, this variable will be ignored.
 
 - AirTime/TaxiIn/TaxiOut: Air time, taxi in and tax out time are all included in the elapsed time, so we would ignore all three variables.
 
 - Origin/Dest: In this analysis, we only consider the relationship between time and delay time, so we would ignore the origin and destination factors.
 
 - Distance: Distance is another important factor that might influence the delay time, so we would control this factor to the middle 50% range which is between 190 and 1085.
    
    min  Q1 median   Q3  max     mean     sd      n     missing
     66  190  775   1085 1770 705.0159 469.1021 99260       0
 
 - Cancelled: since the delay time is only related to scheduled flight, cancelled flight is not included. We need to filter the data to Cancelled==1 to clean the data.
 
 - Diverted: Diverted is a rare case, so we should control variable to Diverted==0, which only consider the case of flights that do not divert.
 
 - CarrierDelay/WeatherDelay/NASDelay/SecurityDelay/LateAircraftDelay:In this analysis, we don't consider the reason for delay, so these variables will be ignored.

Best Day of the Week:

For the flight out of Austin:
 
 DayOfWeek       MEAN   MIN   MAX   SD
 1               9.46   -19   442  31.2
 2               7.21   -20   413  29.4
 3             # 6.38   -19   353  27.0
 4               8.46   -19   412  28.9
 5               10.6    -22   483  31.1
 6             # 6.46   -20   405  27.6
 7               9.53   -22   382  30.8

From the data, we can see that the average departure delay time on Wednesday and Saturday are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

For the flight into Austin:
 DayOfWeek MEAN   MIN   MAX   SD
 1         7.04   -38   425  32.2
 2         4.82   -40   414  30.8
 3       # 3.72   -58   352  28.5
 4         6.24   -40   394  30.2
 5         8.29   -37   466  32.0
 6       # 3.10   -43   399  29.5
 7         6.49   -37   362  31.8
From the data, we can see that the average arrival delay time on Wednesday and Saturday are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

Therefore, we can conclude that the best day in a week to minimize the delays is Wednesday and Saturday.

Best Month of a Year:

For the flight out of Austin:
  Month  MEAN   MIN   MAX   SD
   1     7.88   -20   345  28.4
   2     9.70   -19   293  29.6
   3     12.5   -22   413  35.2
   4     7.18   -22   412  27.4
   5     8.23   -21   347  26.0
   6     10.8   -18   405  32.3
   7     9.44   -20   475  32.8
   8     8.96   -20   382  31.3
   9   # 2.49   -17   272  19.0
  10     3.58   -17   308  21.2
  11   # 3.35   -15   292  20.3
  12     14.6   -15   483  39.9
From the data, we can see that the average departure delay time on September and November are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

For the flight into Austin:
 Month MEAN      MIN   MAX   SD
  1     4.17     -39   339  29.3
  2     6.04     -39   320  31.0
  3     10.1     -58   414  36.5
  4     5.37     -32   394  28.8
  5     6.60     -40   378  28.2
  6     9.34     -40   399  33.5
  7     6.76     -33   465  33.7
  8     6.18     -37   364  32.4
  9  # -0.0788   -34   270  20.2
 10    0.991     -33   310  22.5
 11  # 0.0375    -43   263  22.0
 12    11.8      -37   466  40.8

From the data, we can see that the average arrival delay time on September and November are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

Therefore, we can conclude that the best month in a year to minimize the delays are September and November.

In conclusion, from the analysis of both flights into and out of Austin above, we can conclude that the best day of a week to minimize the delays in a week are Wednesday and Saturday, while the best month of year are September and November. This can be useful information when booking the flight. However, the conclusion might be inaccurate since there might be some uncontrolled variables that might influence the final result. In addition, the data are based on 2008's domestic flight information, the result may vary in different year and for international flights.


## Regression practice

In this case, the question we are considering is whether there is a relationship between patient's age and patient's creatine clearance rate. And whether we can develop a linear model based on the past data, which can be used in the future to predict patient's creatine clearance rate.

![Rplot_creatinine](https://user-images.githubusercontent.com/42823507/74471729-5650fb80-4e66-11ea-973e-89e4d7922be7.png)

