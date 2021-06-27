# Avoiding Hassles When Traveling by Air
## by Maleina Bidek


## Dataset

We explored and analyzed a dataset containing flight arrival and departure details for commercial flights within the United States, including whether or not flights were cancelled or delayed and what the reason was. The data was obtained from the American Statistical Society and can be found [here.](https://community.amstat.org/jointscsg-section/dataexpo/dataexpo2009) Specifically, we explored a set of data from January through December 2008 in order to identify patterns in cancellations and delays, hoping to answer the following questions: 

1. What's the best (and worst) time to fly? 
2. What is the best (and worst) combination of airport and carrier to fly?

The data set was relatively clean however we performed the following modificaitons:
- Removed columns that were unnecessary for our analysis (DepTime, ArrTime, TailNum, ActualElapsedTime, CRSElapsedTime, AirTime, Distance, TaxiIn, TaxiOut)
- Filled nulls with zeros for the following columns: ArrDelay, DepDelay, CarrierDelay, WeatherDelay, NASDelay, SecurityDelay, and LateAircraftDelay
- Converted Diverted and Cancelled columns to Boolean type
- Converted CRSDepTime and CRSArrTime columns to datatype (timedelta) type, first converting any time values of 24:00 or greater into their equivalents that are less than 24:00
- Removed 550 duplicate rows
- Removed one extraneous record that contained 0's in all columns

Our final data set contained 7,009,177 rows and 20 columns.

## Summary of Findings

### Data Distribution
- The flights in our set are generally quite evenly distributed across time (i.e. months, days of month, days of week). There are, however, slighly fewer flights on Saturdays than other days of the week.
- There were more departures from 6am to 8pm, gradually tapering off throughout the day, with the fewest from the late evening to the early morning. 
- Arrival times increased gradually over the morning hours, were steady over the afternoon hours, until gradually tapering off in the evening.
- Diversions are very rare, comprising only 0.2% of the flights in our set.
- Cancellations are relatively rare, making up only 2% of the data in our set. 
- With respect to cancellation reasons, Weather and Carrier cancellations were almost equal at 39.95% and 39.53% respectively. NAS cancellations comprised 20.51% and security cancellations were extremely low (0.01%) compared to the other three types.
- Delays occur much more frequently (18.9% for departure delays and 21.8% for arrivals delays) for an overall combined average of 21.8% of flights. (Note, the same flight that has an arrival delay often started with a departure delay, hence the average of 21%.) 
- Both departure and arrival delays were normally distributed when all values were plotted (i.e. positive and negative). However, as we are interested in positive delays, i.e. flights that are late, if we plot only positive values we notice that they are right skewed. Delay types were similarly right skewed.

### Cancellations

- There are more cancellations in the winter months. 
- There are also proportionately more delays on Fridays than any other day of the week and proportionately less on Saturdays.
- The highest number of cancellations are betwwen 3pm and 9pm.
- "Weather" cancellation types seem to be normally distributed with the time of departure, peaking in the early evening, as opposed to the other three cancellation types, which seem relatively consistent over departure time.
- Some of the big, well known carriers, such as American(AA) and United(UA) tend to have a higher percentage of Carrier cancellations. Otherwise, there is a lot of variation by carrier and cancellation type.
- Smaller, regional airports have a higher percentage of cancellations.

### Delays

- Friday has the highest percentage delays. Saturday has the lowest percentage of delays, however it does have the highest number of security delays. 
- There is a relatively high percentage of delays (over 15% each day.)
- There are generally more delays in the winter, however, there are also more in the summer, as well. The most common delays during these times are carrier, weather and late aircraft delays.
- After a short drop off in the early morning, the percentage of delayed flights increases by the hour from about 5am to 10pm.
- There is a curious spike in security delays at aroun 6am, however, other types of delays appear to roughly normally distributed, with peaking around mid-afternoon and early evening.
- Large carriers American(AA) and United(UA) tend to have a proptionately higher percentage of delays, like they did with cancellations.
- Smaller regional airports tend to have a higher percentage of delays.
- There's not much variation between average arrival delay time by day of week. 
- The summer months (especially June and July) and December have the longest average delays when we look at months. 
- The longest average delays occur between 3am to 5am. 
- There's a lot of variation in delay amounts between carriers, however Mesa Airlines (YV) and JetBlue (B6) had the longest average delays.
- When looking at the origin airports with the highest percentage of arrival delays, Newark (EWR) is the only large airport that made the list in this category. Otherwise it was dominated by smaller, regional airports.
- Departure and arrival delays are very closely positively correlated. Late aircraft and carrier delays seem to be somewhat positively correlated to both arrival and departure delays, while weather and NAS delay are a little less positively correlated and secuity delays not much at all.
- The five delay types have little correlation to one another.

### Putting it all together

- Out of our total set of flights:
    - 0.24% were diverted
    - 1.96% were cancelled
    - 21.75% were delayed
    - 76.05% were on-time (or early!)

- In general, early and on-time arrivals to tend to occur in the morning, no matter the day, even if delays were more common in the earliest morning hours. 
- Cancellations were higher Tuesday and Friday evenings and fluctuated quite a bit in the early morning hours.
- Each airport has airlines that do well with respect to arrival delays and others that do not so well, and vice versa. The now defunct US Airways seems to be the one exception in this set, as it had a relatively lower number of average delay times across all locations.

## Key Insights for Presentation


### When is the best (and worst) time to fly?
- Time of year: To avoid cancellations, fly in the fall and spring, avoid the winter and summer
- Day of Week and Hour: Early and on-time arrivals to tend to occur in the morning, no matter the day. Flight hassles tend to increase in the afternoon and evening, especially on Tuesdays and Thursdays. Early mornings are also prone to hassles.

### Best (and worst) airport and carrier combination to avoid hassles
- Small or regional airports tend to have a higher percentage of cancellations and delays
- Newark was the only large aiport in the top 10 airports with associated arrival delays
- The winning combination is flying with 9 Air Company (AQ) and departing from Las Vegas (LAS). The worst combination at the time of our data was the now defunct Continental Airlines (CO) departing from Charlotte (CLT). 
- When looking for consistently good performance across airports, U.S. Airways had the best record. Unfortunately, they no longer exist.
