## Executive Summary

### Problem Statement
#### Given the observations of the SAT and competitor ACT state participation data from 2017/2018, how might we improve the SAT participation rate for the State of Florida?

The analysis is done in [this Jupyter Notebook.](/code/sat-act-analysis.ipynb)

### Contents:
- [2017 Data Import & Cleaning](/code/sat-act-analysis.ipynb#Data-Import-and-Cleaning)
- [2018 Data Import and Cleaning](/code/sat-act-analysis.ipynb#2018-Data-Import-and-Cleaning)
- [Exploratory Data Analysis](/code/sat-act-analysis.ipynb#Exploratory-Data-Analysis)
- [Data Visualization](/code/sat-act-analysis.ipynb#Visualize-the-data)
- [Descriptive and Inferential Statistics](/code/sat-act-analysis.ipynb#Descriptive-and-Inferential-Statistics)
- [Outside Research](/code/sat-act-analysis.ipynb#Outside-Research)
- [Conclusions and Recommendations](/code/sat-act-analysis.ipynb#Conclusions-and-Recommendations)

### Data Sources
- [SAT](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/)
- [ACT](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows)

### Data Dictionary

<code>final.csv</code> contains the combined information from the <code>act_2017.csv</code>, <code>act_2018_updated.csv</code>, <code>sat_2017.csv</code> and <code>sat_2018.csv</code> datasets, inner joined on the 'state' column.
The data files are found [here](/data).

The properties of each feature are described according to the state post-cleaning and processing in <code>final.csv</code>, with the 'Dataset' attribute describing the original data file the feature came from.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*string*|sat_2017, sat_2018, act_2017, act_2018_updated |One entry for each state in the United States and the District of Columbia.| 
|**sat_2017_participation**|*float*|sat_2017|The percentage of the junior student population taking the SAT in 2017. e.g. 0.33 means 33%.|
|**sat_2018_participation**|*float*|sat_2018|The percentage of the junior student population taking the SAT in 2018. e.g. 0.33 means 33%.|
|**act_2017_participation**|*float*|act_2017|The percentage of the junior student population taking the ACT in 2017. e.g. 0.33 means 33%.|
|**act_2018_participation**|*float*|act_2018_updated|The percentage of the junior student population taking the ACT in 2018. e.g. 0.33 means 33%.|
|**sat_2017_total**|*integer*|sat_2017|The average total SAT score of the state in 2017. The minimum possible score is 400 and maximum is 1600. The score is the sum of the Math and Evidence-Based Reading and Writing scores.|
|**sat_2018_total**|*integer*|sat_2018|The average total SAT score of the state in 2018. The minimum possible score is 400 and maximum is 1600. The score is the sum of the Math and Evidence-Based Reading and Writing scores.|
|**act_2017_composite**|*float*|act_2017|The average composite ACT score of the state in 2017. The minimum possible score is 1 and maximum is 36. Each score is derived from the average of the English, Math, Reading and Science scores.|
|**act_2018_composite**|*float*|act_2018_updated|The average composite ACT score of the state in 2018. The minimum possible score is 1 and maximum is 36. Each score is derived from the average of the English, Math, Reading and Science scores.|
|**sat_2017_math; sat_2017_evidence-based_reading_and_writing**|*integer*|sat_2017|The average score of the state in 2017 for SAT Math and SAT Evidence-Based Reading and Writing respectively. The minimum possible score is 200 and maximum is 800 for each subject.|
|**sat_2018_math; sat_2018_evidence-based_reading_and_writing**|*integer*|sat_2018|The average score of the state in 2018 for SAT Math and SAT Evidence-Based Reading and Writing respectively. The minimum possible score is 200 and maximum is 800 for each subject.|
|**act_2017_english; act_2017_math; act_2017_reading; act_2017_science**|*float*|act_2017|The average score of the state in 2017 for ACT English, Math, Reading and Science respectively. The minimum possible score is 1 and maximum is 36 for each subject.|
|**act_2018_english; act_2018_math; act_2018_reading; act_2018_science**|*float*|act_2018_updated|The average score of the state in 2018 for ACT English, Math, Reading and Science respectively. The minimum possible score is 1 and maximum is 36 for each subject.|



### Conclusions and Recommendations

1. The ACT still dominates participation, with close to 20 states having almost 100% participation. However, [only about half of these states require it, and the other half do not require it but administer it for free.](https://blog.collegevine.com/states-that-require-the-act/) The College Board should work closely with states that do not have a legal requirement for the ACT, and try to win them over to fund free SAT administrations. The case of Colorado switching from ACT to SAT has shown that this can be done.


2. Concerns that the SAT poses obstacles for those of underprivileged or minority backgrounds are causing movements for universities to do away with standardised testing scores. This is happening even in Delaware, a state traditionally with fully SAT participation. The College Board should look into how to alleviate such concerns, for example through creating and publicising more initiatives to help minorities and underprivleged through helping them to take advantage of the already free training resources such as Khan Academy.


3. Increased assessibility to testing and accomodation to student schedules has shown success for the SAT gaining popularity over the ACT in Florida.  The SAT Test Days have proven to be popular and increased participation in the affected districts, so it is sensible to roll out these initiatives to more districts in the state.