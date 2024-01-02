# tableau-challenge
Analysis of bike data collected monthly, organized, and made public on the [Citi Bike Data](https://citibikenyc.com/system-data) webpage in order to find patterns and phenomena.
## Repository Contents
  - *DataCleaning.ipynb* Jupyter Notebook script focused on cleaning and preparing the original data for visualization, supplementing them with zip codes and grouping by stations <br>
  - *CityBike_.twbx* Tableau workbook with visualizations, maps and dashboards composed into a Story<br>
  - **Resources** directory contains: <br>
    - **Original Data** folder with raw data for October and November 2023 from [Citi Bike Data](https://citibikenyc.com/system-data) <br>
  - 3 *.csv* files with cleaned/supplemented/grouped data used for visualization purposes <br>
  - **Images** directory with visual screenshots<br>
  
## Usage
 - *Localy*: having Tableau open CityBike_.twbx <br>
 - *Online*: preview visualization published to Public Tableau [here](https://public.tableau.com/views/CityBike_/CityBike?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)<br>
 
# Data Analysis Report
This analysis is built on data from the most recent complete months as of December 2023: October and November of the same year.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Totals.png" width="275">
</p>

*Dynamics over this period* shows the overall trend for decreasing number of rides, with a rapid increase in a week started October 22 and the highest decrease in a week started November 19.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Weekly_Growth_Decrease.png" width="750">
</p>

 - The spike at the end of October can be caused by Halloween celebrations, as roads could be closed that days and people could use the bikes for commuting among different events in the city.<br>
 - High decrease closer to end of November is likely connected to the Thanksgiving holiday, as people tend to spend time with families that days. It could also be related with weather conditions, but it seems that weather did not dramatically change that period.<br>
 
Let us now compare *Loyal Members* and *Random Customers* (those who are not Members) trends.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Timeline_Members_Random_Count_Duration.png" width="750">
</p>

The proportion between them is pretty constant over time, except for Thanksgiving period, when the percentage of Loyal Members was much lower than usual. However:<br>
 -  Average Duration of a bike ride for random customers is a little higher than average duration of a ride for loyal members.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/RandomCustomerDuration_LoyalMemberDuration.png" width="275">
</p>

Most likely random customers are not so familiar with the area and less mature with shortcuts using. Their rides may be not so well planed or without a plan at all, just exploring the area.<br>
Proceeding with exploring of Loyal Members vs Random Customers, we can notice the following pattern within *Date X Time* peaks:
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/DayTime_Loyal_NotAMember.png" width="750">
</p>

| Loyal Members | Random Customers |
| -------------- | ----------------- |
| Ride peaks in the morning and evening Monday-Friday. However, worth to mention that Friday mornings and evenings are not so busy, which is interesting why.| More rides during daytime of Weekends in addition to evenings of Monday-Friday.|

This could mean that the goal of a ride for non-members is different, rather than routing commutes (e.g. 'to' and 'from' work). They could be used for more pleasure-related things. Which is also an additional reason for extra duration.<br>
And what about correlation between duration and distance?
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Duration_Distance_Member_Random.png" width="650">
</p>

 - Noticeable part of rides has *disproportionately* small distances relative to their durations.<br>
This could be related to round trip usage, when a bike is returned to a station pretty close to the one it was picked-up from.<br>

From the other hand, there are several records with *nonsense data*, e.g.:
- ride with same start/end station display zero duration, yet report a traveled distance of 3 km.
- Additionally, there are records with suspiciously extensive distances covered in relatively small timespans, such as 14 km within 4 min. Upon further investigation of the original latitude and longitude coordinates, it appears that some stations, such as *Freeman St & Southern Blvd*, may have inaccurately recorded geodata.
- There are also locations with coordinates placed anomalously among the river. For example, the *6 Ave & Broome St* at Latitude 40.7314471333333 and Longitude -74.02434595.  This also seems to be related with issues with geodata logged.
- Moreover, the dataset included instances where the start time was logged after the end time, which were cleaned before visualization. <br>
These anomalies might indicate that there are few bikes that need repair OR that there are some cheating tricks. Regardless of the cause, there are definitely issues with the system which should be investigated.


Let us move on to *stations investigation* and check the correlation between pick-ups and drop-offs count.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Start_End_Stations_RidesCount_Correlation.png" width="550">
</p>

There is pretty strong correlation between pick-ups and drop-offs, which means that station locations are very well planned and follow the overall commuting patterns within the region.<br>
There are two stations with the highest percentage of rides, approximately 5% of total rides each: 
 - *Grove St PATH*
 - *Hoboken Terminal - River St & Hudson Pl*
   <br>
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Top10.png" width="750">
</p>

Their popularity could be related with the proximity to major train stations in areas with a high density of tourists, e.g.:
 - Grove Street train station;
 - PATH Hoboken Station, which makes the whole cluster of bike stations around it very popular.
   <br>
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/Start_End_Map.png" width="750">
</p>

Respectively the most popular zip codes are: *07030* and *07302*.<br>
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/ZipCodes.png" width="750">
</p>

Interesting that for these stations the peak of rides is Monday-Thursday 4PM-5PM. No such peak in the morning.<br>
The *Lower Manhattan area* has set of end points but none of start points. So those one-way rides could add extra efforts to manually returning the bikes.<br>
There was an assumption that there could be notable percentage of rides, which start and end at the same point, but it does not seem to be the case. However interesting thing that for rides with same start and end points the *Liberty Light Rail* station has pretty big percentage of such rides coupled with the highest average duration of approximately 40 minutes. 
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/StartEqualEndMap.png" width="750">
</p>

This could mean that the station is frequently used for leisure purposes, possibly due to its proximity to park areas. <br>
When saying about a *duration*, we may want to investigate long rides in unexpected way, by previeving *bike routes*.
<p align="center">
<img src="https://github.com/ValentynaK17/tableau-challenge/blob/main/Images/SuperLongRides.png" width="750">
</p>
  
And surprisingly we can notice interesting pattern: there are few goups of rides that share common endpoints each. For example, a notable number of long rides conclude at *Church Sq Park - 5 St & Park Ave*. <br>
Is It because there are some special activities at this location, such as events at the church or maybe exercise sessions in the park, but definitely interesting to learn.
