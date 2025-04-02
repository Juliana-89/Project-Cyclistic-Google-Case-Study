# Project-Cyclistic-Google-Case-Study
## 📝 Introduction 
The **Cyclistic Bike Share Case Study** is a capstone project for the **Google Data Analytics Professional Certificate** on Coursera. In this case study, I will perform various real-world tasks of a junior data analyst at a fictional company called Cyclistic. Ask, prepare, process, analyze, share, and act are the stages of the data analysis process that I will use to solve the key business problems.

## 💬 Background
Cyclistic is a bike-sharing service offering 600 docking stations and over 5,800 bikes, including unique options like cargo bikes, hand tricycles, and recumbent bikes, making the service accessible to people with disabilities. While 8% of riders use assisted bikes, most opt for standard bicycles. Over 30% of riders use bikes for commuting, though many also ride for leisure.

Cyclistic’s marketing strategy has focused on brand awareness and broad consumer demographics, supported by flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Customers with single-ride or day passes are casual riders, while annual subscribers are members.

Financial analysts note that members are far more profitable than casual riders. Moreno, the director of marketing, believes converting casual riders into members is key to future growth, as they already recognize the benefits of cycling. The marketing team aims to:

* Understand differences between casual riders and members.
* Identify reasons behind casual riders’ purchasing decisions.
* Assess digital media’s impact on marketing strategies.

To achieve this, the team will analyze historical bike trip data to uncover trends and guide targeted marketing campaigns.

### Scenario
At Cyclistic, a Chicago-based bike-share company, I am stepping into the role of a junior data analyst on the marketing analytics team. The company’s future success hinges on increasing annual memberships, as emphasized by the director of marketing. My team aims to analyze how annual members and casual riders use Cyclistic bikes differently to develop a targeted marketing strategy that converts casual riders into annual members.

However, our recommendations must first gain approval from Cyclistic’s executives, meaning they must be backed by data-driven insights and expert visualizations.

This project follows the six-step data analysis process outlined in the Google Data Analytics Certificate:

    Ask – Define the business problem.

    Prepare – Gather and organize relevant data.

    Process – Clean and validate the data.

    Analyze – Identify patterns and trends.

    Share – Present findings through visualizations and reports.

    Act – Recommend strategies based on insights.

The goal is to provide actionable recommendations that help Cyclistic boost annual membership conversions through data-backed marketing decisions.

## ⚙ Approach/Steps
### 1. Ask
Mission

To create marketing strategies that encourage casual riders to become annual members.
Analysis Questions

The next marketing campaign will be guided by three key questions:

* How do annual members and casual riders use Cyclistic bikes differently?
* Why would casual riders purchase an annual membership?
* How can Cyclistic leverage digital media to influence casual riders to become members?

Moreno has assigned me the first question to answer:
"How do annual members and casual riders use Cyclistic bikes differently?"

### 2. Prepare
I will use Divvy trip data, a valuable historical dataset provided by Motivate International Inc. under license, to analyze trends in Cyclistic bike usage from January to December 2022.

**Data Source:** [divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html) <br>
[Note that the data has been made available by Motivate International Inc. under this [<ins>license</ins>](https://www.divvybikes.com/data-license-agreement).]

**Tools:** <br>
- Data cleaning & processing - SQL on PostgreSQL
- Data visualization - Microsoft Power BI

### 3. Process
The basis for this analysis is **2022** data and the steps for processing the data are as follow:

![Data Combining](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Combining%20Months%20Data%20Cyclistic%20.sql)

![Data Exploration](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Data%20Exploration.sql)

![Data Cleaning](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Data%20Cleaning.sql)

![Data Analysis](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Analysis%20Cyclistic.sql)

#### Data Combining
After importing the tables into PostgreSQL, the next step involves merging the twelve monthly tables into a single consolidated table for the year 2022. This consolidation enables more efficient and integrated analysis of the data for that period.

Since all tables had the same column structure and data types, we used the UNION ALL operation to combine them. The resulting table, named cyclistic_2022, contains a total of 5,733,451 rows.

#### Data Exploration
Before cleaning the data, one of the first steps I took was to familiarize myself with the table's structure and its data to identify potential inconsistencies.

The following table lists all column names and their data types. Notably, the ride_id column was set as the primary key, ensuring the uniqueness of each record in the table.

| **No.**|  **Variable**       |  **Description**                                        |**Type**.       |**Null** |
|--------|------------------   | --------------------------------------------------------|----------------|---------|
| 1      | ride_id             | Unique ID assigned to each ride                         | Primary Key    | No      |
| 2      | rideable_type       | classic, docked, or electric                            | Mediumtext     | Yes     |
| 3      | started_at          | Date and time at the start of trip                      | Datetime       | Yes     |
| 4      | ended_at            | Date and time at the end of trip                        | Datetime       | Yes     |
| 5      | start_station_name  | Name of the station where the ride journey started from | MediumText     | Yes     |
| 6      | start_station_id    | ID of the station where the ride journey started from   | MediumText     | Yes     |
| 7      | end_station_name    | Name of the station where the ride trip ended at        | MediumText     | Yes     |
| 8      | end_station_id      | ID of the station where the ride trip ended at          | MediumText     | Yes     |
| 9      | start_lat           | Latitude of starting station                            | Double         | Yes     |
| 10     | start_lng           | Longitude of starting station                           | Double         | Yes     |
| 11     | end_lat             | Latitude of ending station                              | Double         | Yes     |
| 12     | end_lng             | Longitude of ending station                             | Double         | Yes     |                     
| 13     | member_casual       | Type of membership of each rider                        | MediumText     | Yes     |

#### Data Cleaning

Removed missing values – All rows with empty or null entries were deleted.
Added new columns – Three new columns were created:

* ride_length (trip duration)
* day_of_the_week
* month

Filtered invalid trips – Excluded rides lasting less than 1 minute or more than 1 day.
Total rows removed: 1,400,282

### 4. Analyze

Data Analysis
The analysis question is: 
> How do annual members and casual riders use Cyclistic bikes differently?

The cleaned data is imported into Tableau for analysis and the figures plotted are displayed in the following.

### - Total Rides and Bike Type Usage in 2022

The initial comparison focuses on "Bike type preferences between members and casual riders".

The figure below shows the **total number of rides and Bike Type Usage in 2022** carried out by Cyclistic members and casual riders in **2022**. 

![Membership Types](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Count%20Bike%20Types.png)

* Members account for 59.74% of total riders, while casual riders make up 40.3%.
* Bike type usage analysis shows:
    * "Classic" bikes are the most popular.
    * "Electric" bikes come in second.
    * "Docked" bikes are the least used and exclusive to casual riders.

### - Total of Bike Trips By Month, Week and Day

Next, we examine the distribution of trips by month, day of the week, and hour of the day.
![Total of Bike Trip by Day](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Total%20Duration%20Day.png)
![Total of Bike Trip By Week](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Total%20Duration%20Week.png)
![Total of Bike Trip by Month](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Total%20Duration%20Month.png)

Time of Day Analysis
* Members: Peak usage occurs during morning (6–8 AM) and evening (4–8 PM), suggesting commuter behavior.
* Casual Riders: Usage gradually increases throughout the day, peaking in the late afternoon before declining.

Day of the Week Analysis
* Casual riders take more trips on weekends, likely for leisure.
* Members show higher usage on weekdays, with a drop on weekends—further supporting work-related commuting.

Monthly Trends
* Both groups show higher usage in spring/summer and lower usage in winter.
* The smallest gap between casual and member usage occurs in July (summer peak).

Key Insight
*  Members primarily use bikes for work commuting (weekdays, rush hours).
*  Casual riders favor leisure trips (weekends, daytime).
*  Seasonal influence: Both groups ride more in warm months, but casual riders show stronger weekend patterns.

### - Average Bike Trip Durations by Month, Week and Day

An analysis of ride durations was conducted to compare usage patterns between casual riders and annual members.

![Average Trips](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Average%20Duration.png)

Average Ride Length
*  Casual riders have significantly longer trip durations (≈2x) compared to members.
*  Members maintain consistent ride lengths year-round, with no notable fluctuations by season, day, or time.

Casual Rider Trends
*  Seasonal: Longer rides in spring/summer, shorter in winter.
*  Weekly: Peak durations on weekends (leisure use).
*  Daily: Longest rides between 10 AM–2 PM; shortest during 5–8 AM (off-peak hours).

Behavioral Insight
*  Casual riders prioritize longer, less frequent trips, aligning with recreational use.
*  Members’ consistent, shorter rides reinforce utilitarian commuting (e.g., work routines).

Key Insight
The data underscores a clear divide—casual users favor leisure-oriented, extended rides, while members opt for efficient, habitual trips. Seasonal and time-of-day patterns further highlight this distinction.

### - Bike Trip Start and End Locations

To further understand the differences between casual riders and members, we analyze the locations of trip start and end stations. We select stations with the highest trip volume, applying filters to derive the following insights

![Bike Trip End LOcations](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Departure%20location.png)
![Bike Trip End Locations](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Departure.png)

Casual:
*  Start trips primarily near tourist and leisure destinations, including: Museums, Parks, Beaches, Marinas (docking points) and Aquariums

Member:
*  Start trips more frequently near practical and daily-use locations, such as: Universities, Residential areas, Restaurants, Hospitals, Supermarkets, Theaters, Schools, Banks, Factories, Train stations, Parks and plazas

Key Insight:
*  Casual riders favor recreational and scenic spots, suggesting leisure-based usage.
*  Members show commuter-oriented patterns, with trips starting near essential services, workplaces, and transit hubs.

![Bike Trip Start Locations](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Arrival1.png)
![Bike Trip Start Locations](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Arrival%202.png)

Casual:
*  End trips predominantly near leisure and recreational areas, including: Parks, Museums and Tourist attractions

Member:
*  End trips most frequently near daily-use destinations, such as: Universities, Residential neighborhoods and Commercial districts.

Key Insight:
The data reinforces a clear behavioral divide:
*  Casual riders primarily use bikes for leisure and tourism, with trips concentrated around recreational hotspots.
*  Members rely on bikes for routine commuting and practical errands, with trips tied to work, education, and essential services.

### 5. Share

![DashBoard](https://github.com/Juliana-89/Project-Cyclistic-Google-Case-Study/blob/main/Dashboard%20cyclistic.png)

Casuas 
*  They travel twice as much, but less frequently than the members.
*  They begin and end their journeys near parks, museums, coastal areas, and other recreational spaces.
*  They prefer using bicycles during the day, especially on weekends in the summer and spring seasons, for leisure activities.

Members
*  They travel more frequently, but on shorter trips (approximately half the duration of casual cyclists' trips).
*  They begin and end their journeys near universities, residential, and commercial areas.
*  They prefer cycling on weekdays during peak hours (8 AM/5 PM) in spring and summer.

### 6. Act

After identifying the differences between casual cyclists and member cyclists, marketing strategies can be developed to convert casual cyclists into members. The following recommendations are suggested:
1. Launch marketing campaigns during spring and summer in tourist and recreational areas that are popular among casual cyclists.
2. Offer seasonal or weekend-only memberships, considering that casual cyclists are more active during these periods.
3. Provide discounts for longer rides, given that casual cyclists tend to use bikes for longer durations than members.

## 🔮 Conclusion
This analysis offers key insights into the distinct behaviors and preferences of Cyclistic's member and casual riders. By adapting strategies to these differences, the company can more effectively encourage casual users to become potential members.





