# PyBer_Analysis
---
## Deliverables
- Import your data into a Pandas DataFrame.
- Merge your DataFrames.
- Create a bubble chart that showcases the acerage fare versus the total number of rides with bubble size based on the total number of drivers for each city type, including urban, suburban, and rural. 
- Determine the mean, median, and mode for the following:
    - The total number of rides for each city type
    - The average fares for each city type.
    - The total number of drivers for each city type.
- Create box-and-whisker plots that visualize each of the following to determine if there are any outliers:
    - The number of rides for each city type.
    - The fares for each city type.
    - The number of drivers for each city type.
- Create a pie chart that visualizes each of the following data for each city type:
    - The percent of total fares.
    - The percent of total rides.
    - The percent of total drivers.
---

## Analysis Overview
In this assignment we were given instruction to provide a multiple-line graph to show the total weekly fares for each city type. We will reuse some code from prevoius deliverables to determine our analysis along with Pandas and Matplotlib.

---
## Results
In order to perform our analysis we need to provide a few statistics before creating a new dataframe. These Values will be listed below:
- Total rides for each city type
    - Rural: 125
    - Suburban: 625
    - Urban: 1625
- Total divers for each city type
    - Rural: 78
    - Suburban: 490
    - Urban: 2405
- Total Fares for each city type
    - Rural: $4,327.93
    - Suburban: $19,356.33
    - Urban: $39,854.38
- Average fare per ride for each city type
    - Rural: $34.62
    - Suburban: $30.97
    - Urban: $24.53
- Average fare per driver for each city type
    - Rural: $55.49
    - Suburban: $39.50
    - Urban: $16.57

Using these values we can put together a new dataframe using Pandas. The following code looks as follows:
```
pyber_summary_df = pd.DataFrame({"Total Rides": total_rides_type,
                                "Total Drivers": total_driver_type,
                                "Total Fares": total_fare_type,
                                "Average Fare per Ride": ave_fare_per_ride,
                                "Average Fare per Driver": ave_fare_per_driver})
```

Using this new dataframe we then constrained our data within a specific time frame, 1/1/2019 and 4/28/2019. This was done using the `.loc` method to get the data within that timeframe and then we created a new dataframe using the methond `.resample` by week. 

This new dataframe was used to plot the line graph requested for this project. We used an object oriented approach to create this graph, and matplotlib to use a style for the graph. The code for that, along with the graph is shown below.
```
ax=sum_fare_by_week.plot(figsize = (20,6), label=["Rural", "Suburban", "Urban"])
ax.set_title("Total Fare by City Type")
ax.set_xlabel("Date")
ax.set_ylabel("Fare($USD)")
from matplotlib import style
style.use('fivethirtyeight')
```
![alt_text](https://github.com/HotMochaNoWhip/PyBer_Analysis/blob/main/analysis/PyBer_fare_summary.png)

---
## Summary
Using this information let us determine 3 recommendations based on our analysis

1) There are more drivers than riders in Urban areas. Due to this, the value for Average fare per driver while accurate mathematically, is included in those not making any money. At the very least ~780 drivers are not making any money. Based on this, to keep individuals interested in our business model, we might want to initialize a cap for logged in drivers during certain periods. This could let others pursue other revnue options in times when they could be logged in not receiving any ride request. 

2) Holiday's! They seem to have higher averages for rides. We should drive an incentive program for drivers during these times.

3) Rural area's receive very high fares. If we could be sure that there were enough drivers to cover all traffic hours, this could turn a high profit for the company. Incentives for longer drives for our drivers could be put into place. 
