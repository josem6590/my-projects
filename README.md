# PROJECTS
### Prologue
I decided to host a web page of little projects, based on questions that I wanted to answer. In doing so, I hope to offer employees a window into my work, thought processes and satisfy my curiosities. 


# PROJECT 1
## How good an F1 driver is Carlos Sainz?

### Introduction
After the death of my hero Ayrton Senna at Imola in 1994, which I watched live, I started to fall out of love with Formula 1. I then stopped watching when Michael Schumacker kept winning every race and championship - it had become very boring. But something changed in the early 2000's, a young Spanish lad called Fernando Alonso started to make waves. I started watching again and have not stopped. It's well known how good Fernando Alonso is and now at the age of 44 after having won 2 F1 Championships he is still driving and performing well. 

There was a new Spanish driver who entered F1 in 2015, Carlos Sainz, son of the famous rally driver of the same name. Having paid close attention to his career, I have often felt that he has been undervalued and in early 2025, Ferrari chose to replace Carlos Sainz with Lewis Hamilton. Now, its hard to argue when the person who is to replace you is a 7 time F1 champion, but I would have thought Carlos Sainz would have been snapped up by one of the top three teams. He wasn't and in 2024 he signed to Williams. 

I still can't help to thinking that the top teams are missing out on this...in his own words...'smooth operator'. I wanted to have a look at the F1 Data and at how Sainz's race results compare with his team mates, by year. Comparing to his teammates gives us a more accurate comparison because they are in the same car, albeit sometimes with slightly different set ups. My hypothesis is that on average he will have had better results than he's teammates. Let's find out.

### Kaggle
I downloaded the F1 data set from kaggle.com, a community that offers a lot of data sets, runs competitions and keeps its community up to date with the latest news on Machine Learning and Data Science.

### Oracle Cloud
I signed up for a free Oracle Cloud account and created an autonomous database so that I could store my data files as objects within buckets.
![F1 SQL](Bucket.png)


### SQL
I imported the Oracle SQL plugin on my VS Code IDE and continued to download the data from my Oracle Cloud database, as per below example:
![F1 SQL](CloudSQL.png)

I then continued to create the tables that I needed so that I could begin to query the data. I checked to see when Sainz started his career and what years he was at what teams. I did initially create a view that encompassed the basic information that I needed to then query that view. However, in order to showcase the use of cte's I created one query with a cte that pulls in all the information needed.

Pulling the avg. race results by year, driver and team only for the teams that Carlos Sainz was part of, I started to develop a picture of where he stood in comparison to his teammates. Realising that the race count would be important, I decided to add that also as there are certain drivers who had only driven two races in the year. The sample size is not significant but I have kept them in the data to show a real picture of who were his teammates.

![F1 SQL](VS_CODE.png)

### Graph 1
After pulling the data from SQL, I built a graph and made it as clear as possible to the viewer. Choosing a bar chart helps visually to compare Sainz (in blue for easy comparison) vs. his team mates, making it easy to spot who outperformed who, in a given season. Adding a line for the GP_count provides context for the drivers who only drove partial seasons, helping to avoid false conclusions from small samples, but providing an accurate depiction of what took place.

![F1 SQL](graph.png)

### Insights
To provide a more objective interpretation of the data, I have established a simple quantitative framework for my qualitative insights. These descriptions are based on the average race result difference (delta) between Sainz and his teammates over the season.

**Slight edge:** Average race result delta is less than 1.0 position.  
**Clear advantage:** Average race result delta is between 1.0 and 2.5 positions.  
**Dominated:** Average race result delta is greater than 2.5 positions.  

A key point of our analysis is that these qualitative statements are based on the average position difference and are not a formal measure of statistical significance. However, by providing this framework, we can offer a more consistent and transparent interpretation of the quantitative data.

**2015 (Toro Rosso):** Slightly outperformed by Max Verstappen. The average race results were very close, with Verstappen holding a **slight edge** (average delta less than 1.0 position). Both drivers completed a full season (19 GPs).  
**2016 (Toro Rosso):** Sainz had a **clear advantage** over Daniil Kvyat. However, it's worth noting that Verstappen was a teammate for only a limited number of races before his promotion to Red Bull, making the sample size for that comparison small.  
**2017 (Toro Rosso):** Sainz **dominated** his teammates statistically, holding a clear and consistent performance advantage across the season.  
**2018 (Renault):** Sainz was slightly outperformed by Nico Hulkenberg, who held a **slight edge** in average race results.  
**2019 (McLaren):** Sainz held a **clear advantage** over Lando Norris in his first year at McLaren.  
**2020 (McLaren):** Sainz maintained a **slight edge** over Norris again, with both drivers being very closely matched throughout the season.  
**2021 (Ferrari):** The competition was extremely close, with Sainz and Charles Leclerc effectively tied in terms of average race result. Sainz finished the season with a very **slight edge.**  
**2022 (Ferrari):** Leclerc held a **slight edge** over Sainz, outperforming him by a small margin.  
**2023 (Ferrari):** Leclerc's advantage became more pronounced, giving him a **clear advantage** in average race results for the season.  


### SQL - Delta
Seeing the average race result by season vs. his teammate was good but I really wanted a picture of how each driver performs vs each other by GP round. A head2head visual that shows when both drivers finished the race, who came out on top and by how much. I wanted to also see the count for the season i.e. how many times in the season did Sainz come out on top and vice versa. Then I can summarise the % of times that Sainz finished higher than his teammate by team. Therefore, I amended my SQL query that references the cte to be able to do this as per below: 

![F1 SQL](sql_2.png)


### Graph - Delta
I created the below graphs to show the delta, the difference between Sainz race results and his teammates. A positive number, meaning Sainz finished higher than his teammates and a negative number meaning he finished lower than his teammates. The greater the difference from 0, the greater the difference from where both teammates finished. I only wanted to show races where both drives finished the race, hence there are some numbers missing from the GP Rounds. I choose to keep the Y axis bounds consistent through all the graphs for ease of comparison and also highlighted the totals for that year on the right of the chart. 

![F1 SQL](D3.png)


### Insights - Delta
The head-to-head delta analysis provides a more granular view of driver performance by focusing on races where both drivers finished. The positive and negative values represent Sainz's race result relative to his teammate's.

**2015 - 2017 (Toro Rosso):** Our previous analysis showed Verstappen with a slight edge over Sainz in 2015. However, the head-to-head data reveals a closer competition, with both drivers finishing ahead of the other in a total of five races. For his career at Toro Rosso as a whole, Sainz finished higher than his teammates in a significant 70% of head-to-head races. This demonstrates a strong consistency beyond what a single average can show.  
**2018 (Renault):** The head-to-head results confirm the average race results, with Hulkenberg consistently outperforming Sainz when both finished.  
**2019 - 2020 (McLaren):** Over his two years at McLaren, Sainz consistently finished higher than Lando Norris in 61% of head-to-head races. The graphs show that when he won the head-to-head, it was often by a significant margin (around 5 positions), especially in his first season.  
**2021 - 2024 (Ferrari):** This period shows a very tight battle. Sainz and Leclerc were dead even in their head-to-head wins in 2022. In the other three years, Leclerc finished ahead more often. However, the delta graphs show that when Sainz did beat Leclerc, he sometimes did so by a larger margin, which prompted the check of the driver standings. The fact that Sainz finished ahead of Leclerc in the 2021 driver standings, despite the tight head-to-head results, speaks to his consistency and ability to capitalize on opportunities. Overall at Ferrari, Sainz finished ahead of Leclerc in 31% of the head-to-head races.  

### Conclusion
Based on the above analysis of Carlos Sainz's race results, we see a driver who consistently delivers strong results accross multiple teams over the years.

### Key Findings 
**Consistent Front-Runner:** Carlos Sainz has been a very good driver throughout his career, often matching or outperforming his teammates.  

**Strong McLaren Performance:** He had his most dominant period at McLaren, where he finished ahead of Lando Norris in 61% of their head-to-head races over two seasons. This performance, in hindsight, is a testament to his skill and adaptability.  

**Highly Competitive at Ferrari:** While Charles Leclerc held a slight edge during their time as teammates, the competition was incredibly close. In their first season together, Sainz finished ahead in the driver standings, and in subsequent years, the race delta was never overwhelmingly large.  

**Undervalued Talent:** The data suggests that Sainz is an excellent and consistent performer. The fact that he was not immediately picked up by another top team for 2025 is surprising given his track record, especially in comparison to his former teammate Lando Norris's current success.

### Summary
In summary, the hypothesis that Carlos Sainz has, on average, had better results than his teammates holds up well across the majority of his career. He is a "smooth operator" not just in his driving style but also in his ability to extract performance from the car and deliver solid, reliable results. 

