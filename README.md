# NYC Yellow Taxi Trips Data Analysis - Veronica Leong

### Problem Statement
**How did Yellow Taxi trips change as a whole throughout the first half of 2020?**

### Table of Contents
- [Hypothesis](#Hypothesis)
- [Data Source](#Data-Source)
    - *Note: Due to the large CSV file sizes, I attached a link to where the data could be found*
- [Data Inspection/Cleaning](#Data-Inspection/Cleaning)
- [Data Dictionary](#Data-Dictionary)
- [Challenges Encountered](#Challenges-Encountered)
- [Conclusion/Key Takeaways](#Conclusion/Key-Takeaways)
- [Future Analysis/Refinements](#Future-Analysis/Refinements)

### Hypothesis

Despite the number of trips decreasing MoM due to COVID, I expect to see:

1. Trips drop in March due to the WFH protocol
2. Trips to increase again in June, as that's when NYC begins to reopen and enter Phase 1 (6/8) + Phase 2 (6/22)
3. The average trip distance and total amount to increase, as people would potentially prefer taking taxis over public transportation
4. Single passengers to show an increase MoM vs. Group riders due to social distancing measures

### Data Source
**Note: Due to the large CSV file sizes, I attached a link to where the data could be found**

- [NYC Yellow Taxi Trip Records 2020](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
    - Date Range: Jan 2020 - Jun 2020 (1/1/20 - 6/30/20)
    
### Data Inspection/Cleaning
- Kept only `tpep_pickup_datetime` field and dropped `tpep_dropoff_datetime`, as `trip_distance` would theoretically correlate to trip duration
- Dropped fields `fare_amount`, `extra`, `mta_tax`, `tolls_amount`, `improvement_surcharge`, `congestion_surcharge`, as those fields would add up to `total_amount`
- Dropped fields `Vendor ID`,  `PULocationID`, `DOLocationID`, `store_and_fwd_flag`, as based on the Data Dictionary, those categorical fields wouldn't provide additional context to prove/debunk the hypothesis
- Dropped `tip_amount`, as `total_amount` was the only monetary field needed for the analysis
    
### Data Dictionary
- [Link](https://www1.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)

Fields the project analyzes:

|**Field Name**|**Description**|
|---|---|
|**tpep_pickup_datetime**|The date and time when the meter was engaged|
|**passenger_count**|The number of passengers in the vehicle. This is a driver-entered value|
|**trip_distance**|The elapsed trip distance in miles reported by the taximeter|
|**RatecodeID**|The final rate code in effect at the end of the trip (1 = Standard Rate; 2 = JFK; 3 = Newark; 4 = Nassau or Westchester; 5 = Negotiated Fare; 6 = Group Ride)|
|**payment_type**|A numeric code signifying how the passenger paid for the trip (1 = Credit Card; 2 = Cash; 3 = No Charge; 4 = Dispute; 5 = Unknown; 6 = Voided Trip)|
|**total_amount**|The total amount charged to passengers. Does not include cash tips|

### Challenges Encountered
- A lot of varying `trip_distance` vs `trip_amount`
    - For example, 3 mi trip distance would be `$7.50` for one record, but `$55` for another record
- A lot of possible human error when entering the data, which could've potentially skewed data if not cleaned/filtered properly
    - For example, a large number of 0 passenger trips or 0 mi trips

### Conclusion/Key Takeaways
1. **TRUE: Trips drop in March due to the WFH COVID protocol**
    - Specifically in the 2H of March, where the number of Yellow Taxi trips drop drastically by almost 9x in the 2H of March, achieving only 10% of overall March trips
2. **TRUE: Trips to increase again in June, as that's when NYC begins to reopen and enter Phase 1 (6/8) + Phase 2 (6/22)**
    - Additionally, the number of trips began to develop a pattern this month, with trip dips during the Weekends, as typical travelers are throughout the Weekdays, potentially front-line healthcare workers or essential business workers
    - Another potential increase in trips in June could be due to BLM protests
3. **DEPENDS: The average trip distance and total amount to increase, as people would potentially prefer taking taxis over public transportation**
    - Overall trip distance and trip amounts lower during COVID months April and May vs. Jan and Feb. However, the lower average numbers corresponds to the significantly lower number of trips during those months. When trips began to increase again in June, trip distance and trip amounts exceed that of pre-WFH months (Jan + Feb), despite having drastically lower trips
4. **TRUE: Single passengers to show an increase MoM vs. Group riders, potentially due to social distancing measures**
   - Single passenger rider percentage was at 73% for months prior to the WFH protocol (Jan and Feb). The percentage largely increase by +10% in April (83%), when there were the least Yellow Taxi trips made. In the latter months of 2020, single rider percentages remain greater than the percentages pre-WFH (May: 81% and June: 79%).

### Future Analysis/Refinements
- Analyze from another perspective (trip duration) by keeping the `tpep_dropoff_datetime` field
- Take a deeper look into `trip_distance` vs. `trip_amount` to properly filter and clean data, respective to `RatecodeID`
    - Deeper dive into `RatecodeID` and how trips differed for each code ID
- Further analyze trip duration of single riders MoM

### Additional Resources
More information on NYC Phase Reopens and BLM timeline:
- https://www.nytimes.com/article/new-york-phase-reopening.html
- https://www.nytimes.com/article/george-floyd-protests-timeline.html?auth=login-google
- https://en.wikipedia.org/wiki/George_Floyd_protests_in_New_York_City

Last Updated: 10/29/20