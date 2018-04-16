---
layout: post
title: MTA Turnstiles Analysis
---

In my first week with Metis, I worked with some awesome teammates to conduct Project Benson, a data analysis over MTA turnstile Data. The project incorporates Python modules such as Pandas and Seaborn to perform EDA and data visualization to solve a “real world” question.

## Question:
We received an inquiry from the organization WomenTechWomenYes(WTWY) with the following information:

>_"WomenTechWomenYes (WTWY) has an annual gala at the beginning of the summer each year. As we are new and inclusive organization, we try to do double duty with the gala both to fill our event space with individuals passionate about increasing the participation of women in technology, and to concurrently build awareness and reach._

>_To this end we place street teams at entrances to subway stations. The street teams collect email addresses and those who sign up are sent free tickets to our gala._

>_Where we’d like to solicit your engagement is to use MTA subway data, which as I’m sure you know is available freely from the city, to help us optimize the placement of our street teams, such that we can gather the most signatures, ideally from those who will attend the gala and contribute to our cause."_

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

![_config.yml]({{ site.baseurl }}/images/project1-images/1.png)


We first took a look at stations with the busiest traffic to gain a general view of our top picks. It unsurprisingly contains the NYC hotspots like Grand Central, Penn Station and Port Authority Station, but also includes stations hot for transferrings between lines, such as 34 St, Union Square and Fulton St.

![_config.yml]({{ site.baseurl }}/images/project1-images/2.png = 500x)

Then we graphed the traffic for the top 10 stations from morning and afternoon separated by 12 PM. As the traffic of the busiest station in the morning period roughly aligns with that of the least busiest traffic in afternoon, the street team should surely go out in an afternoon period.

![_config.yml]({{ site.baseurl }}/images/project1-images/3.png)

We had an intuition that subways would be less busy on the weekends, but we wanted to use our data to confirm this. The graph shows the top 15 stations by volume and their ridership by day of the week. The number of passengers substantially drops offs on the weekend and displays a rather constant pattern over weekdays.

With a primary list of the busiest stations, we would like to introduce some demographic information for us to better choose the locations for the street team. Once we decide on the stations, we would look more into the heatmap of the station’s traffic and define the best time period in the afternoon and the weekday for WTWY.

![_config.yml]({{ site.baseurl }}/images/project1-images/5.png)

To look at where the target groups might work at, we mapped the locations of women owned business in Manhattan. Around the Midtown area, high density clusters appear near Penn Station, 34th Street Herald Square, Grand Central, and the 28th Street station at 7th avenue. Workers from the above locations could be highly possible to use the stations from our top 10 list, such as Grand Central and 34th Street Herald Square.

![_config.yml]({{ site.baseurl }}/images/project1-images/6.png)

Going towards lower Manhattan, women-owned business clusters densely near the Fulton Street and Wall Street stations.

![_config.yml]({{ site.baseurl }}/images/project1-images/7.png)

The top 15 neighborhoods by median income also confirms the world trade center area to be ideal to meet our target groups.

Therefore, combining our EDA and demographic information, we select the following four stations: Grand Central, 34th Street Herald Square, Fulton Street, World Trade Center.

![_config.yml]({{ site.baseurl }}/images/project1-images/4.png)

Listing the heatmap (example as above) for each station, we believe the following location and schedule to benefit the WTWY street teams to maximize their outreach.

Grand Central Station: 4pm to 8pm on Thursdays.  
34th Street Herald Square: 4pm to 8pm on Thursdays.  
Fulton Street: 4pm to 8pm on Thursdays.  
World Trade Center: 4pm to 8pm on Fridays.  
