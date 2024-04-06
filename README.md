# Bellabeat_Marketing_Analysis

### Project Overview


In this case study, we will work for Bellabeat, a high-tech manufacturer of health-focused products for women. Sršen, Chief Creative Officer of Bellabeat, knows that an analysis of available consumer data would reveal more opportunities for growth. She has asked the marketing analytics team to analyze smart device usage data to gain insight into how people already use their smart devices. Then, using this information, she would like high-level recommendations for how these trends can inform Bellabeat's marketing strategy.

### Data Sources

[Fitbit Fitness Tracker Data:](https://www.kaggle.com/arashnic/fitbit) This Kaggle data set contains personal fitness tracker data from thirty Fitbit users, including heart rate, steps, sleep monitoring and information about daily activity that can be used to explore users’ habits. 


### Tools

- Excel - Data preprocessing
- R - Data analysis
- Tableau - Creating visualizations

### Data Cleaning and Preparation

In the initial data preparation phase, we performed the following tasks:
- Data loading and inspection.
- Added Column “trip_length_min” to track the duration of each ride in minutes.
- Added Column “day_of_week” to analyze customers' behaviour on weekdays and weekends. 
- Handling missing values.
- Data cleaning and formatting.

### Data Analysis

- Following SQL code investigate the number of rides across each day in a week for both categories of users.

```sql
SELECT 
  member_casual
  ,day_of_week
  ,COUNT(ride_id) AS ride_count

FROM 
  `casestudy-416218.bike_share.Q1` 

GROUP BY
  member_casual
  ,day_of_week

ORDER BY 
  day_of_week
  ,member_casual
```

- Following SQL code helps to explore when most users use bikes during the day.

```sql
SELECT  
  FORMAT_DATETIME('%H',started_at) AS start_time
  ,member_casual
  ,COUNT(ride_id) AS ride_count

FROM 
  `casestudy-416218.bike_share.Q1` 
  
GROUP BY 
  start_time
  ,member_casual  

ORDER BY 
  member_casual 
  ,start_time
```

### Results

The analysis results are summarized as follows:

1. The average trip length of casual riders is approximately four times of annual members.

![trip length comparison](https://github.com/MuhammadShamoon/cyclistic_case_study/assets/52103515/cf941372-5a5a-4891-92f0-808945ca85f8)

2. During weekends, the annual members use bikes from afternoon to evening, but during weekdays they mostly use them at 8 am and 5 pm to commute to work.

![Annual members](https://github.com/MuhammadShamoon/cyclistic_case_study/assets/52103515/9ed02246-bd2d-40bc-ab4a-ce18b9bd704b)

3. The number of Casual riders reached its peak value around 2 pm and performed a bell-shaped pattern. They are more likely to ride for leisure.

![Casual Riders Population](https://github.com/MuhammadShamoon/cyclistic_case_study/assets/52103515/154e52dd-ef2e-40d4-8ead-83b337f44604)


### Recommendations

Based on the analysis, we recommend the following actions:

- Create segments based on behaviour patterns such as trip length and timing of bike usage and identify the daily subscribers who demonstrate patterns similar to annual members in terms of usage.

- Highlight how an annual membership provides unlimited bike access, encouraging more frequent and varied usage.

- Provide incentives such as free months, discounted rates, or bonus ride credits to encourage conversion.

- Organize community events or group rides to engage current daily subscribers and showcase annual membership benefits.

- Incorporate user feedback to refine and improve the conversion process over time.

### Limitations

Due to privacy reasons, user information is not included in the dataset. Therefore, this analysis is based on the behaviour of individual rides instead of the customers.







