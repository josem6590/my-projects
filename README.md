# PROJECTS
### Prologue
I realised after a few months of not getting a job that I should try and showcase some work. How can a company really see what I will be able to offer without this. Therefore, I set out to host a web page of little projects, based on questions that I wanted to answer. In doing so, I hope to offer employees a window into my work, thought processes and satisfy my curiosities. I have chosen the narrative form in a hope to engage the reader - everybody likes a story. I tried to inject some of my personality into the work itself and so offering an understanding of myself. 


# PROJECT 1
## How good an F1 driver is Carlos Sainz?

### Introduction
After the death of my hero Ayrton Senna at Imola in 1994, which I watched live, I started to fall out of love with Formula 1. I then stopped watching when Michael Schumacker kept winning every race and championship - it had become very boring. But something changed in the early 2000's, a young Spanish lad called Fernando Alonso started to make waves. I started watching again and have not stopped. It's well known how good Fernando Alonso is and now at the age of 44 after having won 2 F1 Championships he is still driving and performing well. 

There was a new Spanish driver who entered F1 in 2015, Carlos Sainz, son of the famous rally driver of the same name. Having paid close attention to his career, I have often felt that he has been undervalued and in early 2025, Ferrari chose to replace Carlos Sainz with Lewis Hamilton. Now, its hard to argue when the person who is to replace you is a 7 time F1 champion, but I would have thought Carlos Sainz would have been snapped up by one of the top three teams. He wasn't and in 2024 he signed to Williams. 

I still can't help to thinking that the top teams are missing out on this...in his own words...'smooth operator'. I wanted to have a look at the F1 Data and at how Sainz's race results compare with his team mates, by year. Comparing to his teammate gives us a more accurate comparison because they are in the same car, albeit sometimes with slightly different set ups. My hypothesis is that on average he will have had better results than he's team mates. Let's find out.

### Kaggle
I downloaded the F1 data set from kaggle.com, a community that offers a lot of data sets, runs competitions and keeps its community up to date with the latest news on Machine Learning and Data Science.

### Oracle Cloud
I signed up for a free Oracle Cloud account and created an autonomous database so that I could store my data files as objects within buckets.
![F1 SQL](Bucket.png)


### SQL
I imported the Oracle SQL plugin on my VS Code IDE and continued to download the data from my Oracle Cloud database, as per below example:
![F1 SQL](CloudSQL.png)

I then continued to create the tables that I needed so that I could begin to query my data. I checked to see when Sainz started his career and what years he was at what teams. I did initially create a view that encompassed basic information that I needed to then query that view. However in order to showcase the use of cte's I created one query with a cte that pulls in all the information needed.

Pulling the avg. race results by year, driver and team only for the teams that Carlos Sainz was part of, I started to develop a picture of where he stood in comparison to his team mates. Realising that the race count would be important, I decided to add that also as there are certain drivers who had only driven two races in the year. The sample size is not significant but I have kept them in the data to show a real picture of who were his team mates.

![F1 SQL](VS_CODE.png)

### Graph 1
After pulling the data from SQL, I built a graph and made it as clear as possible to the viewer. Choosing a bar chart helps visually to compare Sainz (in blue for easy comparison) vs. his team mates, making it easy to spot who outperformed who, in a given season. Adding a line for the GP_count provides context for the drivers who only drove partial seasons, helping to avoid false conclusions from small samples, but providing an accurate depiction of what took place.

![F1 SQL](graph.png)

### Insights

2015 (Toro Rosso) Slightly outperformed by Max, both did full seasons (19 GPs)  
2016 (Toro Rosso) Sainz comfortably outperformed Kvyat, but Verstappen was faster in limited races  
2017 (Toro Rosso) Dominated his teammates statistically  
2018 (Renault) Outperformed by Hülkenberg  
2019 (McLaren) Beat Norris fairly clearly  
2020 (McLaren) Slight edge to Sainz again  
2021 (Ferrari) Essentially tied, slight edge to Sainz  
2022 (Ferrari) Slightly outperformed by Leclerc  
2023 (Ferrari) Leclerc ahead more clearly  
2024 (Ferrari) Leclerc ahead again, though not by a huge margin  



### SQL - Delta
Seeing the average race result by season vs. his teammate was good but i really wanted a picture of how each driver performs vs each other by GP round. A head2head visual that shows when both drivers finished the race who came out ontop and by how much. I wanted to also see the count for the season, how many times in the season did Sainz come out ontop and how many times did his colleague come out ontop? Then I can summarise the % of times that Sainz finished higher than his teammate by team. Therefore, I amended my SQL query that references the cte to be able to do this as per below: 
![F1 SQL](sql_2.png)

### Graph - Delta
I created the below graphs to show the delta, the difference between Sainz race results and his teammates. A positive number, meaning Sainz finsihed higher than his teammate and a negative number meaning he finished lower than his team mate. The greater the difference from 0, the greater the difference from where both team mates finished. I only wanted to show races where both drives finished the race hence there are some numbers missing from the GP Rounds. I choose to keep the Y axis bounds consistent through all the graphs for ease of comparison and also highlighted the totals for that year on the right of the chart. 

![F1 SQL](DS.png)

### Insights - Delta
2015 - 2017 (Toro Rosso) Whats interesting to note here is that when we look at his average race result previously max had outperformed Sainz in 2015. However, what the H2H data tells us is that when looking at races both drivers managed to finish, they had both finished higher than each other a total of five times. When we look at his career at Toro Rosso we see Sainz finishing higher that his team mates a whopping 70% of the time.  
2018 (Renault) Hulkenburg outperforms Sainz  
2019 - 2020 (Mclaren) Sainz over his two years at MClaren finishes higher than Lando Norris 61% of the time and often by quite a margin or around 5 positions especially in his first season.  
2021 - 2024 (Ferrari) Apart from 2022 where Sainz and Lecrec beat each other equally, Lecrec finishes higher in teh other three years. Although looking at the delta not by much. However, I noticed that when Sainz did beat Lecrec he beat him by a greater margin which prompted me to just check the driver standings for each year. What I found was Sainz finished higher than Lecrec in the driver standings for 2021 but not if any other year at Ferrari. Sains only managed to beat Lecrec in 31% of the H2H. 

### Summary
Looking at the data I have compiled as a whole we see a very good driver performing very well apart from 2018 in his one season at Renault and perhaps the last two seasons at Ferrari. However, he is consistant and even in the seasons he does not perform well the delta to his teammate is not significantly large as highlighted in 2021 where he still finished higher than lecrec in the driver standings. It's interesting to note when he was at Mclaren he performed better than his team mate Norris and Norris is currently fighting for the Championship, as he was last year. It does make me wonder - what if Sainz didn't leave Mclaren. We can only speculate but looking at his past performance, I would say he would be on to win his first F1 Championship. 


