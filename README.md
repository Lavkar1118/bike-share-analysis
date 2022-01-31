# bike-share-analysis

## Performed as a Capstone for Google Data Analytics Professional Certificate

### Business Tasks:

* Understand how  annual members and casual riders use Cyclistic bikes differently?
* Find insights to pitch membership proposals to casual riders
* Collect evidence towards preferrable digital media forums to promote membership among casual riders

### Tools and Methods:

* Annual data for bike share made available by Motivate International Inc. was downloaded from [link provided in the project pdf](https://divvy-tripdata.s3.amazonaws.com/index.html)
* Data Wrangling was perfomed in R primarily using packages: tidyverse, lubridate, janitor, chron and ggplot

```
#create new col with just the dates

Annual_data2 <- Annual_data %>% mutate(start_date = as.Date(started_at)) %>% mutate (end_date = as.Date(ended_at))

# individual cols for month, date, year and week of the day

Annual_data2 <- Annual_data2 %>% mutate(month_trip = format(as.Date(start_date), "%b")) %>% mutate(day_trip = format(as.Date(start_date), "%d")) %>% mutate(year_trip = format(as.Date(start_date), "%Y")) %>% mutate(day_of_week = format(as.Date(start_date), "%A")) %>% mutate(month_year = paste (month_trip, " ", year_trip))

#calculating the ride lengths in hours

Annual_data2 <- Annual_data2 %>% mutate(ride_length = round(difftime(ended_at, started_at, units = "hours"), digits = 2))

#converting the ride length in factors to numeric
Annual_data2 <- Annual_data2 %>% mutate(ride_length = as.numeric(as.character(ride_length)))


#extracting time into separate column

Annual_data2 <- Annual_data2 %>% mutate(start_time = format(started_at, "%T"))

#extracting start time (just the hour) into separate column

Annual_data2 <- Annual_data2 %>% mutate(start_time_hrs = format(started_at, "%H"))
#creating categorical variable for time of the day

Annual_data2 <- Annual_data2 %>% mutate(time_cat = cut(times(start_time) , breaks = (1/24) * c(0,5,12,16,19,24), 
    labels = c("past_midnight", "morning", "afternoon", "evening", "night")))

Annual_data2 <- Annual_data2 %>% filter(time_cat != "NA")

str(Annual_data2)

```
* Comprehensive [dashborads](https://public.tableau.com/app/profile/lavanya.muthukumar1967/viz/CyclisticBikeShareAnalysis_16436078655310/Dashboard2#1) were created using Tableau to summarize ride trends.

![Ride Trends](https://github.com/[Lavkar1118]/[bike-share-analysis/Trensds.jpge)


### Key Takeaways:
* While members bike to work, casual riders use bikes to tour the city
* Weekend (casual) users hence might not prefer annual subscriptions
* Company can consider introducing  weekend passes (Fri - Sun) on a monthly basis to engage casual riders 
* Implementation of annual summer passes might also encourage more casual riders to purchase memberships
* A survey among (new) casual riders might help in understanding specific preferences of day passes over memberships

