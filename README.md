# SDS323 Exercise 1


## Data visualization: flights at ABIA

Considering the flights into and out of Austin, I am interested in what is the best day in a week and the best month in a year to fly to minimize delays. Therefore, I need to develop two models to answer these two questions. The two independent variables are DayOfWeek and Month separately. Based on the flights in and out of Austin, the dependent variable for into Austin is ArrDelay, while the dependent variable for out of Austin is DepDelay.

Besides these two variables, we need to consider other 15 variables on which variables to ignore and which variables to control.
-Year all 2008: since the data are all from 2008, this variable can be ignored in this case.
-DayOfMonth: we are analyzing the best month and day of week in this case, the day of month is unrelated since they are both time variable, so we can neglect this variable in this case.
-DepTime/CRSDepTime/ArrTime/CRSArrTime: These are data used to calculate the delay time for departure and arrival flights, so we can ignore them in this analysis.
-UniqueCarrier/FlightNum/TailNum: In this analysis, we consider the delay time regardless of carrier information, so we ignore these three variables related to airline carrier.
-ActualElapsedTime: The elapsed time is related to the air time, which may influence the delay time, so we will use the middle 50% of data which is the range between 57 and 164.
-CRSElapsedTime: Since we have controlled the ActualElapsedTime, this variable will be ignored.
-AirTime/TaxiIn/TaxiOut: Air time, taxi in and tax out time are all included in the elapsed time, so we would ignore all three variables.
-Origin/Dest: In this analysis, we only consider the relationship between time and delay time, so we would ignore the origin and destination factors.
-Distance: Distance is another important factor that might influence the delay time, so we would control this factor to the middle 50% range which is between 190 and 1085.
-Cancelled: since the delay time is only related to scheduled flight, cancelled flight is not included. We need to filter the data to Cancelled==1 to clean the data.
-CancellationCode: this is ignored for we do not consider cancelled flight.
-Diverted: Diverted is a rare case, so we should control variable to Diverted==0, which only consider the case of flights that do not divert.
-CarrierDelay/WeatherDelay/NASDelay/SecurityDelay/LateAircraftDelay:In this analysis, we don't consider the reason for delay, so these variables will be ignored.
