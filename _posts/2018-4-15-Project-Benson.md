---
layout: post
title: Project Benson: A Data Analysis on NYC MTA Turnstiles
---

In my first week with Metis, I worked with some awesome teammates to conduct Project Benson, a data analysis over MTA turnstile Data. The project incorporates Python modules such as Pandas and Seaborn to perform EDA and data visualization to solve a “real world” question.

## Question:
We received an inquiry from the organization WomenTechWomenYes(WTWY) with the following information:

_"WomenTechWomenYes (WTWY) has an annual gala at the beginning of the summer each year. As we are new and inclusive organization, we try to do double duty with the gala both to fill our event space with individuals passionate about increasing the participation of women in technology, and to concurrently build awareness and reach._

_To this end we place street teams at entrances to subway stations. The street teams collect email addresses and those who sign up are sent free tickets to our gala._

_Where we’d like to solicit your engagement is to use MTA subway data, which as I’m sure you know is available freely from the city, to help us optimize the placement of our street teams, such that we can gather the most signatures, ideally from those who will attend the gala and contribute to our cause."_

To meet WTWY’s request, we would utilize data and analytics to optimize the effectiveness of the street team at subway stations to spread awareness and attract attendants to the WTWY Annual Gala. The goal of our analysis is to allocate the best subway stations to collect email signatures and reach out to target group efficiently.

We decided to use MTA turnstile data to find station with heavy traffic and define the best time range and weekday for the street team to go to these stations. We would  also use demographic information such as women and minority-owned business in NYC and NYC income distribution to better associate locations with the project’s target group.

## Data:
1. MTA turnstile Data:
    - Available on the official mta website. ([link](http://web.mta.info/developers/turnstile.html))
    - Provides information of people traffic at turnstiles of each station in a time period.
2. Women and Minority-Owned Business: ([link](http://www1.nyc.gov/nyc-resources/service/2479/minority-and-woman-owned-business-enterprise-mwbe-program)):
    - Lists businesses in New York City which are over 1 year old and are at least 51% owned, operated, and controlled by a minority or woman.
3. American Community Survey 2016 5-year Estimates:([link](https://www.census.gov/acs/www/data/data-tables-and-tools/data-profiles/2016/))
    - Provide income data for NYC zip codes

## Assumptions:
We have held the following assumptions to guide our future analysis:
1. The target group of WTWY’s outreach by NYC subway stations are ideally women workers in technology industry, but can be broadened to people who are supportive on this concept and interested in the Gala itself. We would like to reach to a crowd as large as possible to meet women workers, technology industry participants, and also any passengers who show interests.
2. Women business owners can become potential donors for the Gala supporting women leadership, and would be more likely to hire more women employees. Therefore, we decide to look at the locations of women-owned business in order to seize such demographic.
3. The total traffic at one turnstile is the combination of entries and exits.
4. Afternoon could be a better time frame for the street teams to outreach and collect emails, since workers don’t like to be stopped at the morning rush period, bearing the risk of being late.
5. We use MTA data dated at Feb 25 - Apr 6, 2018. Workers from our target group tend to commute via subway with a constant travel pattern over their period of employment at the current company. A more recent dataset, rather than data from early summer in the past years, can reflect the traffic of working population more accurately.

## Data Information:
For this project, we use MTA turnstile data ranges from Feb 25 - Apr 6 this year with over 1 million rows. It records cumulative entries and exits of each turnstile 6 times day. This sizable dataset over a long duration of time allows us to find a reliable pattern over the subway traffic.

However, the major errors in the dataset which can interfere with our analysis are unreasonable large cumulative number, uneven time block for timestamps, counter resets on the cumulative numbers. Therefore, we performed some data cleaning to conceal effects of the mentioned errors over the total traffic counts. We only keep data for a turnstile whose number of entries/exits is between 0 and 60 per minute.

## Analysis:

 _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
