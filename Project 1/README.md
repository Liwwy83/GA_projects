# Project 1: Standardized Test Analysis

## Problem Statement
The ACT was introduced as an alternative standardized test to the SAT in 1959. The ACT has seen a gradual increase in the number of test takers since its inception, and in 2012 the ACT surpassed the SAT for the first time in total test takers.

In the three years from 2017 to 2019, ACT participation rates saw a general declining trend (national 60% in 2017 to 52% in 2019) while SAT participation rates saw an increase (more than 1.8 million in 2017 to more than 2.2 million in 2019).

What are the contributing factors for this trend? As a stakeholder in College Board, how can we further increase the popularity of SAT?

## Data Dictionary
|Feature|Type|Dataset(s)|Description|
|---|---|---|---|
|**state**|*object*|**ALL**|Name of each of the 50 states in US and District of Columbia (ACT_2019/2017 also includes National)| 
|**participation**|*float*|**ALL**|Participation rate (value between 0 and 1)|
|**composite**|*float*|ACT|Average composite ACT score (value between 1 and 36)|
|**english**|*float*|ACT_2017|Average ACT score for English section (value between 1 and 36)|
|**math**|*float*|ACT_2017|Average ACT score for Math section (value between 1 and 36)|
|**reading**|*float*|ACT_2017|Average ACT score for Reading section (value between 1 and 36)|
|**science**|*float*|ACT_2017|Average ACT score for Science section (value between 1 and 36)|
|**ebrw**|*integer*|SAT|Average SAT score for Evidence-Based Reading and Writing section (value between 200 and 800)|
|**math**|*integer*|SAT|Average SAT score for Math section (value between 200 and 800)|
|**total**|*integer*|SAT|Average SAT total score (value between 400 and 1600)|

Note: Features in merged files are tagged with '_201X' to indicate the year, and '_act' or '_sat' to indicate which test as necessary.

## Analysis
There were many states with 100% ACT participation rates while only a handful with 100% SAT participation rates. 

### States with the highest and lowest participation rates
|Test|Year|State(s) with highest participation (rate) [Number of states]|State(s) with lowest participation (rate) [Number of states]|
|---|---|---|---|
|ACT|2017|Alabama, Arkansas, Colorado, Kentucky, Louisiana, Minnesota, Mississippi, Missouri, Montana, Nevada, North Carolina, Oklahama, South Carolina, Tennessee, Utah, Wisconsin, Wyoming (100%) [17]|Maine (8%) [1]|
|ACT|2018|Alabama, Arkansas, Kentucky, Louisiana, Mississippi, Missouri, Montana, Nebraska, Nevada, North Carolina, Ohio, Oklahama, South Carolina, Tennessee, Utah, Wisconsin, Wyoming (100%) [17]|Maine (7%) [1]|
|ACT|2019|Alabama, Arkansas, Kentucky, Louisiana, Mississippi, Montana, Nebraska, Nevada, North Carolina, Ohio, Oklahama, Tennessee, Utah, Wisconsin, Wyoming (100%) [15]|Maine (6%) [1]|
|SAT|2017|Connecticut, Delaware, District of Columbia, Michigan (100%) [4]|Iowa, Mississippi, North Dakota (2%) [3]|
|SAT|2018|Colorado, Connecticut, Delaware, Idaho, Michigan (100%) [5]|North Dakota (2%) [1]|
|SAT|2019|Colorado, Connecticut, Delaware, Florida, Idaho, Illinois, Michigan, Rhode Island (100%) [8]|North Dakota (2%) [1]|

Median ACT participation rate declined from 69% in 2017 to 54% in 2019, while median SAT participation rate increased from 38% to 54%.

There is an obvious trend that SAT is gaining popularity while ACT is losing popularity.

Three states in particular, Colorado, Illinois and West Virginia, had drastic increase in their SAT participation rates from less than 20% to 100% or almost 100%.

## Conclusion and Recommendations
### Factors influencing SAT participation rates
Higher SAT participation rates are strongly associated with higher SAT participation rates in other years, lower ACT participation rates, and lower total scores.

In particular, we researched into the three states of Colorado, Illinois and West Virginia, to see what may have caused the drastic increase in their SAT participation rates. 

### Recommendations
It is recommended that we work on convincing more states to switch over from ACT (or other tests) to SAT.
1. Continuously monitor any changes to the Common Core standards and align the SAT to them.
2. Actively reach out to the Departments of Education in more states to persuade them of the strengths of the SAT and the benefits it offers to their students.
3. Continue partnering with Khan Academy to provide free test prep. Review test prep resources to ensure quality and alignment to the SAT.