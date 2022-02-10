#  Project 1: Standardized Test Analysis

### Overview

For this  project, we're going to take a look  ACT scores and participation rates in the United States. We'll seek to identify trends in the data and combine our data analysis with outside research to address our problem statement.

The ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)).
* [ACT](https://www.act.org/content/act/en.html)

Standardized tests have long been a controversial topic for students, administrators, and legislators. Since the 1940's, an increasing number of colleges have been using scores from students' performances on tests like the ACT as a measure for college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). Supporters of these tests argue that these scores can be used as an objective measure to determine college admittance. Opponents of these tests claim that these tests are not accurate measures of students potential or ability and serve as an inequitable barrier to entry.

### Problem Statement


> * As an employee of the ACT - the organization that administers the ACT - I am a part of a team that tracks statewide participation  and success rate and recommends where money is best spent to improve ACT success rates.  This project aims to explore trends in  ACT participation for the years 2017-2019 and seeks to identify states that have increased the level of participation and to see if the level of success also improved or if there is a need to improve their composite.


---

### Datasets


There are 3 datasets included in the [`data`](./data/) folder for this project that I used and combine them in one Dataset to allow me to work on it . 

* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2019.csv`](./data/act_2019.csv): 2019 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`all_act.csv`](./data/all_act.csv): Combine ACT Scores by State for 2017-2019


####  Data Dictionary 

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*object*|all_act| the names of the State in the USA |
|**participation_17**|*float* |all_act|The percentage of high school graduate who did the ACT in 2017 in the state(scale 0-1)|
|**english_17**|*float*| all_act| the average of the in the english subject of the ACT in 2017|
|**math_17**|*float*| all_act| the average of the in the math subject of the ACT in 2017|
|**reading_17**|*float*| all_act| the average of the in the reading subject of the ACT in 2017|
|**science_17**|*float*| all_act| the average of the in the science subject of the ACT in 2017|
|**composite_17**|*float*|all_act|The average score of ACT in 2017 in the state (scale is 0-36)|
|**participation_18**|*float*|all_act|The percentage of high school graduate who did the ACT in 2018 in the state(scale 0-1)|
|**composite_18**|*float*|all_act|The average score of ACT in 2018 in the state (scale is 0-36)|
|**participation_19**|*float*|all_act|The percentage of high school graduate who did the ACT in 2019 in the state(scale 0-1)|
|**composite_19**|*float*|all_act|The average score of ACT in 2019 in the state (scale is 0-36)|

---


---

###  Data  Import & Cleaning  

Import the datasets 
1. Display the data: print the first 5 rows of each dataframe to your Jupyter notebook.
2. Check for missing values.
3. Check for any obvious issues with the observations (keep in mind the minimum & maximum possible values for each test/subtest).
4. Fix any errors you identified in steps 2-3
5. Display the data types of each feature.
6. Fix any incorrect data types found in step 5.
    - Fix any individual values preventing other columns from being the appropriate type.
    - If your dataset has a column of percents (ex. '50%', '30.5%', etc.), use the function you wrote in Part 1 (coding challenges, number 3) to convert this to floats! *Hint*: use `.map()` or `.apply()`.
7. Rename Columns.
    - Column names should be all lowercase.
    - Column names should not contain spaces (underscores will suffice--this allows for using the `df.column_name` method to access columns in addition to `df['column_name']`).
    - Column names should be unique and informative.
8. Drop unnecessary rows (if needed).
9. Merge dataframes that can be merged.
10. Perform any additional cleaning that you feel is necessary.
11. Save your cleaned and merged dataframes as csv files.



### Exploratory Data Anlysis
1. Summary Statistics.
2. Use a **dictionary comprehension** to apply the standard deviation function you create in part 1 to each numeric column in the dataframe.  
    - Assign the output to variable `sd` as a dictionary where: 
        - Each column name is now a key 
        - That standard deviation of the column is the value 
        - *Example Output :* `{'ACT_Math': 120, 'ACT_Reading': 120, ...}`
3. Investigate trends in the data.
    - Using sorting and/or masking (along with the `.head()` method to avoid printing our entire dataframe), consider questions relevant to your problem statement. Some examples are provided below (but feel free to change these questions for your specific problem):
        - Which states have the highest and lowest participation rates for the 2017, 2019, or 2019 SAT and ACT?
        - Which states have the highest and lowest mean total/composite scores for the 2017, 2019, or 2019 SAT and ACT?
        - Do any states with 100% participation on a given test have a rate change year-to-year?
        - Do any states show have >50% participation on *both* tests each year?
        - Which colleges have the highest median SAT and ACT scores for admittance?
        - Which California school districts have the highest and lowest mean test scores?
   


### Visualization
---

### Conclusion and Recommendation

According to the exploration of data , we see that in general  the states with a lower participation rate have the highest  composite score.As increasing  the number of participant also decrease the composite score.

But by analysing the state with the same participating rate , first where the participation was the same for consecutive years 2018 and 2019 we found that the composite  of 2019 were lower than 2018.

Secondly, by comparing the state where the participation is mandatory meaning that it is 100%, we can see that the maximun score is getting lower  even thought the distribution is almost the same.

As conclusion,even if  increasing the participation can be perseve as one of the cause of lower  composite score on State level , with this data we can see that even if the participation level is the same the composite score is getting lower as the year come.

My recommendation is that because the composite score have a correlation with the individual score, and according to this date if the sum of score of every graduate  in the subject there is a chance to increase the composite of state.
One way to that is get involve in plan changes and improvement in the curriculum of high schools.

---


