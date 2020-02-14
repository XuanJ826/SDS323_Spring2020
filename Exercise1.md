# SDS323 Exercise 1


## Data visualization: flights at ABIA

Considering the flights into and out of Austin, I am interested in what is the best day in a week and the best month in a year to fly to minimize delays. Therefore, I need to develop two models to answer these two questions. The two independent variables are DayOfWeek and Month separately. Based on the flights in and out of Austin, the dependent variable for into Austin is ArrDelay, while the dependent variable for out of Austin is DepDelay.

Besides these four variables, we need to consider other 15 variables on which variables to ignore and which variables to control:

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

In conclusion, from the analysis of both flights into and out of Austin above, we can conclude that the best day of a week to minimize the delays in a week are Wednesday and Saturday, while the best month of year are September and November. This can be useful information when booking the flight. However, the conclusion might be inaccurate since there might be some uncontrolled variables that might influence the final result, and the small available sample size after filter may distort the final result. In addition, the data are based on 2008's domestic flight information, the result may vary in different year and for international flights.


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


## Green Buildings

In this case, besides the recommendations from developer, there are many factors needed to be controled. Based on the data set in greenbuildings.csv, we can see that the data for green buildings is small compared to the data for non-green buildings.This may lead to biased conclustion from the analysis.
![Rplot](https://user-images.githubusercontent.com/42823507/74485987-a093a600-4e81-11ea-921d-ed56a23b14e0.png)

There are in total 23 variables from the data set. Rent, gas costs and electricity costs are three major dependent variables we need to analyze to see whether investing a green building is worthy in the long term. Green_rating is our independent variable that we used to compare the revenue and cost between green and non-green buildings.

Besides these four variables, we need to consider other 19 variables one by one to see whether we need to control these variables in our analysis:
 - CS. Property ID: this variable will be ignored since it is just a primary ID.
 - cluster: this variable is an identifier for the building cluster, which is unrelated to our analysis.
 - size: The size factor would not be controlled in this case because based on the graph, there is no relationship between size and rent.
 ![Rplot01](https://user-images.githubusercontent.com/42823507/74486469-a2119e00-4e82-11ea-9f47-3985f968fb12.png)
 - empl_gr: we will set it to be top 25% since the Austin's y-o-y employment growth rate ranks the 2nd in last year.
 - leasing rate: there are some outliers in occupancy rate; thus, we need to remove these outliers in our analysis
 - stories: since we plan to build a 15 stories building, we can set the range from 10 to 19, which is the range between median and 75th percentile
 <img width="403" alt="Screen Shot 2020-02-13 at 5 15 05 PM" src="https://user-images.githubusercontent.com/42823507/74487166-6d064b00-4e84-11ea-9618-4dac56c3a1c7.png">
 
 - age: the age influence the rent in a negative way based on the plot, since our building is new, we can control it to be less than 34, which is the median building age in the data set.
 
 ![Rplot02](https://user-images.githubusercontent.com/42823507/74487286-b191e680-4e84-11ea-9cad-1ab5a26914c5.png)
 
 - renovated: we would not control this factor since we set the age to be lower than 34, which is comparatively new building
 - class a/class b: we would set the building to be either a or b class since it represents the average quality.
 - LEED/Energy star: since these two variables are categories of the green_rating, we would not control them in this case.
 - amenities: By looking at the map, the amenities is 1 in the planning region; thus, we control this as amenities == 1.
 - cd/hd/total.dd: we would not control these three factor in this case as they influence the rent in a neglected way.
 - Percipitation: we would control this to the middle 50% range based on the Austin's precipitation rate.
 - Cluster rent: regional rent rate has huge influence in the rent based on the plot, which positively influence the rent. 
 Based on the East Austin(zip code:78702)'s median rent rate, it is included in top 25% of national median rent rate. Thus, we control it in the top25% range in this case. 

 ![Rplot03](https://user-images.githubusercontent.com/42823507/74487727-e05c8c80-4e85-11ea-956f-e064f57e5bbd.png)

After controlling all variables, we get the following dataset:
<img width="1405" alt="Screen Shot 2020-02-13 at 5 28 56 PM" src="https://user-images.githubusercontent.com/42823507/74487917-5c56d480-4e86-11ea-8af0-32c1675cbc78.png">

This data set shows us that it is not economic to invest in the green building because the average and median rent rates of green buildings are both lower than those of non-green buildings. Besides, the gas and electricity costs are the same. Therefore, in the long-run, it might earn higher profit by building a non-green building in consideration of high implementation cost with low revenue.


## Milk prices

From milk.csv, we can see there are two variables: price and sales quantity.
In order to derive the function used to maxmize the profit, we need to set up some variables:
 - N-net profit
 - Q - sales quantity
 - P - price per unit
 - C - cost per unit

Since the net profit is the total revenue minus total cost, we can get the equation: N = Q (P-C). 
Meanwhile, we know that Q is determined by customer, while the P is determined by store.

So the question is for what price the store should set to maximize the net profit. To get the result, we need first consider how Q and P is related. And the plot between two is shown below:

![Rplot04](https://user-images.githubusercontent.com/42823507/74488514-084cef80-4e88-11ea-8a19-da507fb4657d.png)

From the graph, we can see there is a negative relationship between Q and P, and the next step is to develop a fitted equation based on the data, which can be used by store to preditct quantity from price.

Based on the power laws, we know that Q = KP^E, where K is a constant and E is price elasticity of demand(PED).
To derive the value of K and E, we can use log-transformed linear regression model between Q and P:

![Rplot05](https://user-images.githubusercontent.com/42823507/74488706-b22c7c00-4e88-11ea-9397-1eb718cb3bee.png)

The equation is: log(Q) = 4.72 - 1.62log(P), and K = e^4.72 = 110, E = -1.62 based on the trick.

<img width="380" alt="Screen Shot 2020-02-13 at 5 46 33 PM" src="https://user-images.githubusercontent.com/42823507/74488787-e738ce80-4e88-11ea-8d03-42cbee3db8ca.png">

Therefore, we know that Q = 110*P^-1.62, AND N = (110*P^-1.62)(P-C). Using the calculus dN/dP = 0, we know that when P = 2.61C, WHICH IS THE PROFIT-MAXMIZING PRICE.

In the case when c=1, we can check the plot in R to know that the profit-maxmizing price is about 2.61

![Rplot06](https://user-images.githubusercontent.com/42823507/74488992-8231a880-4e89-11ea-8729-90110083bc95.png)
