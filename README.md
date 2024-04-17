# Bellabeat_Marketing_Analysis

### Project Overview


In this case study, we will work for Bellabeat, a high-tech manufacturer of health-focused products for women. The Chief Creative Officer of Bellabeat knows that an analysis of available consumer data would reveal more opportunities for growth. She has asked the marketing analytics team to analyze smart device usage data to gain insight into how people already use their smart devices. Then, using this information, she would like high-level recommendations for how these trends can inform Bellabeat's marketing strategy.

### Data Sources

[Fitbit Fitness Tracker Data:](https://www.kaggle.com/arashnic/fitbit) This Kaggle data set contains personal fitness tracker data from thirty Fitbit users, including heart rate, steps, sleep monitoring and information about daily activity that can be used to explore users’ habits. 


### Tools

- Excel - Data preprocessing
- R - Data analysis
- Tableau - Creating visualizations

### Data Cleaning and Preparation

In the initial data preparation phase, we performed the following tasks:
- Data loading and inspection.
- Data cleaning and formatting.

### Data Analysis

- Following R code investigate the number of everyday consumers.

#### Installing and loading common packages and libraries

```{r}
install.packages('tidyverse')
library(tidyverse)
```
#### Loading CSV files

Here we'll create a dataframe named 'daily_activity' by doing a union between two CSV files from the dataset.

```{r}
daily_activity_apr <- read.csv("dailyActivity_merged_mar-apr.csv")
daily_activity_may <- read.csv("dailyActivity_merged_apr-may.csv")
```

```{r}
daily_activity <- rbind(daily_activity_apr,daily_activity_may)
```

#### Exploring the table

```{r}
colnames(daily_activity)
```

```{r}
n_distinct(daily_activity$Id)
```

#### Finding the percentage of everyday consumers

The normal values for daily steps, calories burned and sedentary minutes for females can vary but we can segment everyday consumers by applying general boundary values.

```{r}
everyday_consumer <- daily_activity %>%
  filter(TotalSteps > 5000 &
         Calories > 1200 &
         SedentaryMinutes < 8*60) %>%
  summarise(percentage = n_distinct(Id) / n_distinct(daily_activity$Id) * 100)
```

```{r}
everyday_consumer$percentage
```


### Results

The analysis results are summarized as follows:

1. Everyday consumers are among the primary users of smart products; from the above analysis using R, they are approximately 17 %. 

2. MET is used to estimate the intensity of physical activities, but users with low METs also have higher heart rates. This reflects that these smart wearables are used by Athletes, Fitness Enthusiasts and patients as well. 

![Sheet 4](https://github.com/MuhammadShamoon/bellabeat_CaseStudy/assets/52103515/76415451-59ce-4814-945c-b6ff2e4c8251)


### Recommendations

Based on the analysis, we recommend the following actions:

- Collaborate with influencers, fitness experts, healthcare professionals, and women advocates to endorse and promote the products to their audiences.

- Maintain a strong presence across various channels, including online retailers, the company's e-commerce website and social media platforms.

- Create informative and engaging content that educates and empowers the target audience about health and wellness topics relevant to women. 
This content can include blog posts, articles, videos, and infographics.

### Limitations

In this analysis, the sample consists of 35 observations. To increase the accuracy of the results, more observations are needed.







