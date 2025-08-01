# PROJECTS
### Prologue
I realised after a few months of not getting a job that I should try and showcase some work. How can a company really see what I will be able to offer without this. Therefore, I set out to host a web page of little projects, based on questions that I wanted to answer. In doing so, I hope to offer employees a window into my work, thought processes and satisfy my curiosities. I have chosen the narrative form in a hope to engage the reader - everybody likes a story. I tried to inject some of my personality into the work itself and so offering an understanding of myself. 


# PROJECT 1
## How good an F1 driver is Carlos Sainz?

### Introduction
After the death of my hero Ayrton Senna at Imola in 1994, which I watched live, I started to fall out of love with Formula 1. I then stopped watching when Michael Schumacker kept winning every race and championship - it had become very boring. But something changed in the early 2000's, a young Spanish lad called Fernando Alonso started to make waves. I started watching again and have not stopped. It's well known how good Fernando Alonso is and now at the age of 44 after having won 2 F1 Championships he is still driving and performing well. 

There was a new Spanish driver who entered F1 in 2015, Carlos Sainz, son of the famous rally driver of the same name. Having paid close attention to his career, I have often felt that he has been undervalued and in early 2025, Ferrari chose to replace Carlos Sainz with Lewis Hamilton. Now, its hard to argue when the person who is to replace you is a 7 time F1 champion, but I would have thought Carlos Sainz would have been snapped up by one of the top three teams. He wasn't and in 2024 he signed to Williams. 

I still can't help to think that the top teams are missing out on this...in his own words...'smooth operator'. I wanted to have a look at the F1 Data and at how Sainz's race results compare with his team mates, by year. Comparing to his teammate gives us a more accurate comparison because they are in the same car, albeit sometimes with slightly different set ups. My hypothesis is that on average he will have had better results than he's team mates. Let's find out.

### Kaggle
I downloaded the F1 data set from kaggle.com, a community that offers a lot of data sets, runs competitions and keeps its community up to date with the latest news on Machine Learning and Data Science.

### Oracle Cloud
I signed up for a free Oracle Cloud account and created an autonomous database so that I could store my data files as objects within buckets.
![F1 SQL](Bucket.png)


### SQL
I imported the Oracle SQL plugin on my VSCode IDE and continued to download the data from my Oracle Cloud database, as per below example:
![F1 SQL](CloudSQL.png)

I then continued to create the tables that I needed so that I could begin to query my data. I checked to see when Sainz started his career and what years he was at what teams. I did initially create a view that encompassed basic information that I needed to then query that view. However in order to showcase the use of cte's I created one query with a cte that pulls in all the information needed.

Pulling the avg. race results by year, driver and team only for the teams that Carlos Sainz was part of, I started to develop a picture of where he stood in comparison to his team mates. Realising that the race count would be important, I decided to add that also as there are certain drivers who had only driven two races in the year. The sample size is not significant but I have kept them in the data to show a real picture of who were his team mates.

![F1 SQL](VS_CODE.png)

### Graph
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


### Summary
At the beginning of his F1 career Sainz generally matched or outperformed his teammates with the exception of Verstappen in 2015-16 (Verstappen limited races in 2016). From 2018-2020 Sainz outperformed Norris but was behind Hulkenburg, which makes me want to do the same analysis on Hulkenburg, another driver who I have often thought of as undervalued. At Ferrari, Sainz was generally out performed by Leclerc apart from his first season in 2021. However, as someone who watched those season he was also very unfortunate with strategy, race incidents and the performance of the car. Short stints by Hartley, Gasley, Bearman and Verstappen in 2016 shouldn't be compared to Sainz's full season.

Sainz's is a consistent driver with average races finishes trending down, which will now begin to trend up since joining Williams. It's interesting to note when he was at Mclaren he performed better than his team mate Norris and Norris is currently fighting for the Championship, as he was last year. It does make me wonder - what if Sainz didn't leave Mclaren. We can only speculate but looking at his past performance, I would say he would be on to win his first F1 Championship. 


