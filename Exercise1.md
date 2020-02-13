# SDS323 Exercise 1


## Data visualization: flights at ABIA

Considering the flights into and out of Austin, I am interested in what is the best day in a week and the best month in a year to fly to minimize delays. Therefore, I need to develop two models to answer these two questions. The two independent variables are DayOfWeek and Month separately. Based on the flights in and out of Austin, the dependent variable for into Austin is ArrDelay, while the dependent variable for out of Austin is DepDelay.

Besides these two variables, we need to consider other 15 variables on which variables to ignore and which variables to control:

 - Year all 2008: since the data are all from 2008, this variable can be ignored in this case.
 
 - DayOfMonth: we are analyzing the best month and day of week in this case, the day of month is unrelated since they are both time variable, so we can neglect this variable in this case
 
 - DepTime/CRSDepTime/ArrTime/CRSArrTime: These are data used to calculate the delay time for departure and arrival flights, so we can ignore them in this analysis.
 
 - UniqueCarrier/FlightNum/TailNum: In this analysis, we consider the delay time regardless of carrier information, so we ignore these three variables related to airline carrier.
 
 - ActualElapsedTime: The elapsed time is related to the air time, which may influence the delay time, so we will use the middle 50% of data which is the range between 57 and 164.
    <img width="406" alt="Screen Shot 2020-02-13 at 1 43 03 PM" src="https://user-images.githubusercontent.com/42823507/74471984-c8c1db80-4e66-11ea-8478-2a8461fc6aa3.png">
 
 - CRSElapsedTime: Since we have controlled the ActualElapsedTime, this variable will be ignored.
 
 - AirTime/TaxiIn/TaxiOut: Air time, taxi in and tax out time are all included in the elapsed time, so we would ignore all three variables.
 
 - Origin/Dest: In this analysis, we only consider the relationship between time and delay time, so we would ignore the origin and destination factors.
 
 - Distance: Distance is another important factor that might influence the delay time, so we would control this factor to the middle 50% range which is between 190 and 1085.
    <img width="440" alt="Screen Shot 2020-02-13 at 1 42 02 PM" src="https://user-images.githubusercontent.com/42823507/74471912-a4fe9580-4e66-11ea-9b0e-142f24bf4634.png">
 
 - Cancelled: since the delay time is only related to scheduled flight, cancelled flight is not included. We need to filter the data to Cancelled==1 to clean the data.
 
 - Diverted: Diverted is a rare case, so we should control variable to Diverted==0, which only consider the case of flights that do not divert.
 
 - CarrierDelay/WeatherDelay/NASDelay/SecurityDelay/LateAircraftDelay:In this analysis, we don't consider the reason for delay, so these variables will be ignored.

Best Day of the Week:

For the flight out of Austin:
 
 <img width="271" alt="Screen Shot 2020-02-13 at 1 44 17 PM" src="https://user-images.githubusercontent.com/42823507/74472077-f3139900-4e66-11ea-9a07-e2a81cdc807b.png">

From the data, we can see that the average departure delay time on Wednesday and Saturday are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

<img width="273" alt="Screen Shot 2020-02-13 at 1 45 08 PM" src="https://user-images.githubusercontent.com/42823507/74472148-12122b00-4e67-11ea-999c-4f4ed8d66ca0.png">

From the data, we can see that the average arrival delay time on Wednesday and Saturday are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

Therefore, we can conclude that the best day in a week to minimize the delays is Wednesday and Saturday.

Best Month of a Year:

For the flight out of Austin:

<img width="243" alt="Screen Shot 2020-02-13 at 1 46 19 PM" src="https://user-images.githubusercontent.com/42823507/74472250-3d951580-4e67-11ea-9289-943fc7eae892.png">

From the data, we can see that the average departure delay time on September and November are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

For the flight into Austin:

<img width="264" alt="Screen Shot 2020-02-13 at 1 46 57 PM" src="https://user-images.githubusercontent.com/42823507/74472315-556c9980-4e67-11ea-8c24-08f258a7a0ea.png">

From the data, we can see that the average arrival delay time on September and November are lowest. In addition, they also have the lowest standard deviation, which indicates the number has low fluctuation.

Therefore, we can conclude that the best month in a year to minimize the delays are September and November.

In conclusion, from the analysis of both flights into and out of Austin above, we can conclude that the best day of a week to minimize the delays in a week are Wednesday and Saturday, while the best month of year are September and November. This can be useful information when booking the flight. However, the conclusion might be inaccurate since there might be some uncontrolled variables that might influence the final result. In addition, the data are based on 2008's domestic flight information, the result may vary in different year and for international flights.


## Regression practice

In this case, the question we are considering is whether there is a relationship between patient's age and patient's creatine clearance rate. And whether we can develop a linear model based on the past data, which can be used in the future to predict patient's creatine clearance rate.

Based on the data in the creatinine.csv, we first create a plot of clearance rate vs age, which is shown below:
![Rplot_creatinine](https://user-images.githubusercontent.com/42823507/74471729-5650fb80-4e66-11ea-973e-89e4d7922be7.png)

From the plot, we can see there is a linear relationship between clearance rate and age, and the next step is to develop a fitted equation based on the data, which can be used in the future to preditct clearance rate from age.
Based on the past data, R helps to develop the following fitted equation: clearance rate = 147.81 - 0.62 * age
<img width="301" alt="Screen Shot 2020-02-13 at 1 52 05 PM" src="https://user-images.githubusercontent.com/42823507/74472773-125ef600-4e68-11ea-98f7-41c51d33502a.png">

Therefore, we can use this model to predict patients' clearance rate based on their ages.
 - For a 55-year-old, we expect the creatinine clearance rate should be, on average, 113.72 mL/minute.
<img width="267" alt="Screen Shot 2020-02-13 at 1 55 53 PM" src="https://user-images.githubusercontent.com/42823507/74473059-94e7b580-4e68-11ea-976f-8f881b78291a.png">

 - The model also indicates that we expected that the clearance rate will decrease, on average, 0.62 mL/minute, if the age increase by 1 year.
 
 - Based on the model: For a 40-year-old, we expect the creatinine clearance rate should be, on average, 123.02 mL/minute; while for a 60-year-old, we expect the creatinine clearance rate should be, on average, 110.62 mL/minute. Therefore, the 40-year-old patient (135 mL/min) is 11.98 mL/minute (9.74%) above average, while the 60-year-old patient (112 mL/min) is 1.38 mL/minute (1.25%) above average. Because the clearance rate is the higher, the better, we can conclude that the 40-year-old patient is healther.
 <img width="309" alt="Screen Shot 2020-02-13 at 1 58 44 PM" src="https://user-images.githubusercontent.com/42823507/74473318-07f12c00-4e69-11ea-8949-b96347ac6251.png">

