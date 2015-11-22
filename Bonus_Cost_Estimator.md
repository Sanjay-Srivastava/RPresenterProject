Bonus Cost Estimator
========================================================
author: Sanjay Srivastava
date: Nov 21, 2015
transition: rotate

Motivation:
<small>
This application helps interactvely forecast the cost of a Sales Bonus Scheme based on inputs provided by a user.
</small>

What is a Sales Bonus Scheme?
========================================================
Many organizations pay their sales personnel, a bonus based on their performance. These employees are assigned a sales territory and an expectation of how much sales the organization expects from that sales territory. This 'expectation of sales' is called a Sales Target. At the end of the period, actual sales achieved by the salesperson is measured, and the Attainment % is calculated as 'Actual Sales' / 'Sales Target'. This Attainment % then becomes the basis for calculating an employee's sales bonus. 

A sample Bonus Scheme
========================================================
Organizations typically have several bonus programs or schemes for different groups of employees. Below is a sample bonus scheme:

1. If the Attainment is 0% - 50%, the salesperson is not eligible for any bonus
2. If the Attainment is > 50% <= 100%, bonus is calculated as (Attainment % - 50%) * 2.5 * Base Pay
3. If the Attainment is = 100%, bonus exactly equals the Base Pay (user input)
4. If the Attainment is > 100% <= 150%, bonus is calculated as (100% + (Attainment % - 100%) * 4) * Base Pay
5. If the Attainment is > 150%, the saleperson gets the maximum bonus of 3 x Base Pay

<small>
(Note: Attainment % = Actual Sales / Sales Target)

Notice that bonus rapidly declines as attainment falls below 100% and at 50% attainment, there is no bonus. On the other hand, bonus is much steeper once the employee crosses the Sales Target assigned to them. Because of this behavior, the variability of attainment around mean implies that aggregate bonus does not vary in a simple linear proportion. 
</small>

How does this Bonus Scheme actually work?
========================================================
Let there be 6 sales employees in the company XYZ Inc, all with a Base Pay of $10,000 and attainment of respectively: 47%, 65%, 100%, 125%, 150%, 200%. 
The bonus calculations are shown in the below table:


```
[1] "Total Base Pay: $60000"
```

```
[1] "Total Bonus: $93000"
```

```
[1] "Bonus Cost (Total Base Pay/ Total Bonus) = 155%"
```

```
  Attainment% Bonus$     Performance
1          47      0 Poor - No Bonus
2          65   3000       Below Par
3         100  10000       Below Par
4         125  20000       Above Par
5         150  30000       Above Par
6         200  30000   Top Performer
```

Notice that bonus caps at 3x Base Pay and that below 50% attainment, there is no bonus.


Real-World Application
========================================================
At the start of the financial year, the Accounting department wants to determine what to budget for sales bonuses. This app estimates the aggregate sales bonus for all sales employees, based on user inputs, and certain assumptions:

- The attainment by each sales employee is completely random and independent of any other sale employee
- The attainment is normally distributed



Forecasting Bonus Cost
========================================================
Below is a table that shows how Total Bonus Cost (as % of Total Basic Pay) varies as mean Attainment % changes. 
For this example, we have assumed the following:

- Number of sales employees = 100
- Base Pay for each employee = $10,000
- Standard deviation of attainment = 30%


```
   MeanAttainment% BonusCost%
1               50         25
2               60         38
3               70         58
4               80         72
5               90        105
6              100        131
7              110        135
8              120        185
9              130        214
10             140        229
11             150        255
```

For a demo of the actual application, please visit [here](https://mydataexperiments.shinyapps.io/Bonus_Cost_Estimator)
