<h1>Data Modelling Employee Resignation</h1>

---

<h4>Table of contents </h4>

- Introduction  
- Features overview  
- Methodolog  
	- Overview:  
	- Process:  
- Results: Data Exploration and Modelling  
	- Initial Data Exploration:  
	- Data Relationship Exploration:  
	- Data modelling:  
- Discussion  
- Recommendation  
- Conclusion  
- Reference  

---

<h2>Introduction:</h2>

Revolution Consulting (RC) is an IT company that offers services centred on AI machine learning and data science driven solutions. Revolution Consulting is a top performer in the field and it is an imperative for management that the company is able to attract and retain high-quality practitioners. Recently, the management team has reported increasing levels of negative feedback noting a decline in the quality of work being produced. A preliminary investigation has identified high rates of employee churn as a likely cause of the company's declining standards. The management team at Revolution Consulting provided the Analytics team with a CSV file containing data on current and past employees of the firm. The research goal of this report was to identify factors that are likely to be contributing to employee attrition, and then identify clusters of employees who share these attributes. With this data the management team will be able to identify employees with a high-risk of resigning and develop strategies designed specifically to target these employees This report details a preliminary exploration of the data as provided by RC’s Human Resources department. This exploration provides a broad overview of the company and its employees, to better inform the preceding exploratory analysis of relationships in the data. The following relationship analysis provides a deeper understanding of the relationships between attributes, with the intent to identify factors that impact rates of resignation and employee churn. By completing this analysis prior to modelling, the analyst team was able to omit potential sources of noise and irrelevant complexity from the data modelling process. The third section of this report details the machine learning models (K-means, DBSCAN) used to identify potential high-risk clusters of employees. This report then evaluates a high-risk cluster to determine its characteristics and provide a recommendation to the management team to combat the employee turn-over within the grouping.

---

<h2>Features Overview:</h2>

| Feature Name           | Unique Values | Type           | Description   |
|------------------------|:-------------:|:--------------:|---------------|
| EmployeeID             | 1470          | Nominal        | Unique ID number
| Age                    | 43            | Interval/Ratio | Employee age (18-60)
| Resigned               | 2             | Nominal        | Employment Status (Y/N)
| BusinessTravel         | 3             | Ordinal        | Frequency of work travel
| BusinessUnit           | 3             | Nominal        | Department
| EducationLevel         | 5             | Ordinal        | Qualification Level (1 = low)            
| Gender                 | 2             | Nominal        | Employee sex (M/F)
| JobSatisfaction        | 4             | Ordinal        | Self reported satisfaction (1 = low)
| MaritalStatus          | 2             | Nominal        | Employee marital status (Y/N)
| MonthlyIncome          | 1349          | Interval/Ratio | Take home pay
| NumCompaniesWorked     | 10            | Interval/Ratio | Previous jobs (0 = first job)        
| OverTime               | 2             | Ordinal        | Worked overtime past 12 months (Y/N)
| PercentSalaryHike      | 15            | Interval/Ratio | Pay increase last 12 months (%)          
| PerformanceRating      | 2             | Ordinal        | Manager performance rating (1 = low) 
| AverageWeeklyHours     | 23            | Interval/Ratio | Averaged working hours
| TotalWorkingYears      | 40            | Interval/Ratio | Employee's career / experience
| TrainingTimesLastYear  | 7             | Interval/Ratio | Number of completed training courses
| WorkLifeBalance        | 4             | Ordinal        | Self reported work-life balance (1 = low)
| YearsAtCompany         | 37            | Interval/Ratio | Time employed with company
| YearsInRole            | 19            | Interval/Ratio | Duration of tenure in current role
| YearsSinceLastPromotion| 16            | Interval/Ratio | Time since last promotion
| YearsWithCurrManager   | 18            | Interval/Ratio | Time spent under current manager

<h2>Methodology:</h2>
<h3>Overview:</h3>
The objective of this analysis was to identify key factors contributing to high rates of employee churn
and attrition within Revolution Consulting. First a preliminary data exploration was carried out
looking into single attributes within the data to identify relevant or causal factors. Then the team
engaged in a targeted relationship analysis of identified causal factors with the intent of deepening
our understanding of potential causes of employee churn. Following these evaluations, unsupervised
machine learning models were employed to analyse the data. This report used the K-Means and
DBSCAN machine learning models to cluster the data identified in the first two steps of this analysis.

<h2>Process:</h2>
<h3>Exploratory Analysis:</h3>
In order to understand the wider context within which the data modelling would take place, the data
analysis team first undertook a preliminary assessment of the data provided by Human Resources.
Designed with the intent to uncover potential causal factors, this exploratory analysis looked at 20
employee attributes that were believed to have an influence on employee resignation rates. Each
attribute was first assessed in isolation to identify any correlation it had with employee resignation.

<h3>Relationship Analysis:</h3>
Following the initial analysis, 10 pairs of selected attributes were analysed with the intent to deepen
the team's understanding of the situation, and to refine the attributes selected for the data
modelling process.

<h3>Steps:</h3>

- Import libraries into the environment for conducting the analysis
- Read in .csv data
- Preliminary dataframe check for missing, incorrect and NaN values
- Exploratory Analysis
- Correlation Evaluation

<h3>Data Modeling:</h3>

The data modeling carried out in this report utilised unsupervised machine learning algorithms (K-means & DBSCAN) in order to cluster a selected multi-dimensional dataframe. This is a commonly used technique employed to identify clusters within a dataset, allowing for a targeted analysis of the resulting clusters to reveal their specific attributes. In order to correctly generate these models it is important to first "tidy" the data to ensure there are no abnormal results.

The steps followed to tidy the employee dataframe are outlined below.

- Drop the target value (Resigned) from the dataframe to ensure it does not influence clustering.
- Drop sources of data leakage (EmployeeID).
- Drop uncorrelated values to simplify dataframe and avoid excessive multi-dimensionality.

<h4> K-means Modelling: </h4>

- Select a number fo K values for modelling the data (value for 'K' determined by the "Within Cluseter Sum of Squares" & "Silhouette Coefficient").
- Test clustering for assigned K value
- Recalibrate K and re-model for actionable clustering.

<h4> DBSCAN Modelling: </h4>

- Run Nearest Neighbours plot to determine epsilon (Eps) value for DBSCAN modelling.
- Test clustering for assigned Eps value.
- Recalibrate Eps and re-model for actionable clustering.

  <h3> Evaluation Strategy: </h3>

Once the machine learning models have generated actionable clusters, a single churn 
 employee cluster was selected for an attributes analysis, highlighting specific metrics to target for an employee churn reduction strategy.

 ---

 <h2> Results: Data Exploration and Modelling </h2>

 <h3> Emploratory Analysis: </h3>

 <h4> Resignation Status: </h4>

The first step of the data exploration process was an evaluation of the ‘Resigned’ status of the data frame.
Across Revolution Consulting, 16.1% of the surveyed employees had resigned within the survey period, with 83.9% maintaining their employment (Figure 1). With this baseline set, the analysis team then worked systematically through the twenty (20) attributes against each observation to generate a more comprehensive picture of the general pattern of resignation. The following section outlines key observations made through this exploratory analysis. A complete list of these plots and observations can be found in appendix 1.

<p align="center">
	<img src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/6db86f5e-cb05-419b-96f0-f52cbfa3f612"/>
</p>

<h4>Resignation by Monthly Income:</h4>

Remuneration is widely regarded as a prime causal factor leading to employee resignation. It is perceived as a yardstick against which an employee can gauge the value of their labour to an employer and indirectly how their employer values them. This belief is reflected within the data gathered on employee monthly incomes in figure 2. Ex-employees who resigned from RC in the surveyed period received a median monthly income (approx $3,300) that was substantially lower than those who maintained their employment at RC (approx $5,100). This stark difference in income between past and present employees highlights income as a causal factor in an employee's decision to resign.

<p align="center">
	<img	src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/c8c5c718-b063-4e20-939f-c532c099218d"/>
</p>

<h4>Resignation by Age:</h4>

The exploratory analysis also revealed employees under the age of 40 as a key cohort in relation to employee resignation. Peaking at around 28-30 years of age, employees who are under 40 have a substantially higher propensity to resign than their older colleagues. Interestingly, employees under 20 years of age were more likely to resign than to stay with the firm, and employees aged 20-22 had
an approximately 50% chance of resigning. This churn of younger employees represents a significant long-term concern for Revolution Consulting. Younger employees are more likely to have received contemporary training and education prior to commencing their tenure and have the potential to modernise practices at the firm. These employees are also likely to require a higher degree of training and exposure, losing these employees after spending resources on their development is a poor outcome for RC.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/b783880f-1b4c-43fa-a25a-ab0f51aae2fa"/>
</p>

<h4>Resignation by Overtime:</h4>

Another cohort of concern identified in the exploratory analysis was employees who recorded having worked overtime within the survey period with 30.5% of these employees resigning. When contrasted against those who were not required to work overtime, with a 10.4% rate of resignation, this makes a substantial increase in the likelihood of an employee to resign. When expressed as an approximate fraction, this is an increase from 1 in 10 employees resigning, to 1 in 3.

<p align="center">
  <img
	src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/2433a2b6-59d2-4bb2-8ef5-943702abbcff" 
	width="45%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img
	src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/7daee86d-03f4-4a69-87a9-c0bbd0c2cf10" 
	width="45%">
</p>

<h4>Resignation by Average Weekly Hours Worked:</h4>

The average weekly hours worked by an employee was also found through the initial data exploration to have a notable impact upon rates of resignation for Revolution Consulting’s employees.For the majority of RC’s employees, the average working week is 40 hours (Figure 5), there is however a considerable cohort of individuals who routinely work above this threshold. 

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/38b33be0-5483-43b1-96c5-17ea8ef45038"
</p>
	
Interestingly, if an individual is required to work up to 45 hours a week, the additional workload has little influence on their likelihood to resign. However, when employees report working from approximately 50 hours to 60 hours a week, the likelihood they resign is substantially elevated (Figure 6).

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/905688c0-197a-4804-88e2-1457610ce69a"
</p>

<h3>Data Correlation Exploration:</h3>

Following the initial data exploration four (4) key attributes were identified as having a marked influence upon employee resignation; Monthly Income, Age, OverTime, Average Weekly Hours Worked. These four key attributes were then used as a launch pad into an in-depth exploration of relationships between the attributes provided in the data set.

<h4>Monthly Income / Average Weekly Hours Worked (AWHW):</h4>

Based on the previous findings for Monthly Income and AWHW, the analysis team hypothesised that as an individual worked longer hours, they would expect to be financially rewarded as a result, and those who were not, would likely be the employees who resign.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/be663e4f-c95a-4e02-baa5-7d799ee662f5"
</p>

Figure 7 illustrates Monthly Income as a function of AWHW for employees and reveals two key “at risk” clusters of employees. The first of these clusters is those employees working 40 hour weeks and receiving a Monthly Income of less than approximately $11,250. While it is difficult to discern from figure 7 alone the likelihood that employees falling into this grouping will resign, the plot demonstrates a clear relationship between the two attributes and their influence on an employee's decision to resign. The second cluster identified in figure 7 comprises those employees working approximately 49 to 57 hours a week and earning less than $11,250. Akin to the first cluster identified, this relationship between hours worked and remuneration has a clear influence on an employees propensity to resign. It is important to note in this second cluster, that as Monthly Income decreases the density of observations increases, with a clear concentration around employees earning $2,500 a month.

<h4> Monthly Income / Years in Role: </h4>

The analysis team hypothesised that employees who believe they are underpaid for their experience in a given role would be another cohort likely to resign. However the data showed that once an employee had over 10 years in a role the likelihood of their resignation dramatically decreased. In fact, the employees who were most likely to resign were those with under 5 years in a role who were earning less than $7,500 a month. This pattern of resignation intensifies as YearsInRole and MonthlyIncome decrease.

<p align="center">
	<img src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/5f62b13c-3861-44a6-b1a7-8e008dac0a09"
 <p/>

<h4> Total Working Years (TWY) / Average Weekly Hours Worked (AWHW): </h4>

In a continued investigation into the influence of AWHW, the analysis team paired the attribute with the reported Total Working Years of employees. The analysis team hypothesised that young employees at the start of their careers would feel overworked if they are extended beyond an average of 40 hours a week too early in their careers and would likely resign as a result. Figure 9 demonstrates that the team’s hypothesis was for the most part accurate, with a distinct cluster of resigned employees who reported less than 13 Total Working Years that were concurrently working between 49 to 57 hours a week. Equally important, once employees had over 15 Total Working Years reported, the proportion who resigned substantially decreased.

<p align="center">
	<img src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/c48e7eef-8b19-4610-bd1a-78876f0ac3d9"
 <p/>

<h3> Data Modelling: </h3>

The data used within the K-Means and the DBSCAN modelling techniques only included attributes found within the exploratory and relationship analysis to have an influence on rates of resignation. For example, 16.1% of employees with a performance rating of 3 resigned, compared to 16.4% of employees with a rating of 4. From this observation it is clear that performance rating has little to no effect on the choice to resign, and as such it is dropped from the modelling data. Nominal data has also been removed.

<h4> Model 1: K-Means Cluster: </h4>

The analysis team employed the K-Means clustering technique to evaluate two selected data frames for meaningful employee clusters. The first dataframe included 14 attributes deemed to be significant and are as follows; Age, BusinessTravel, EducationLevel, JobSatisfaction, MonthlyIncome, OverTime, AWHW, TotalWorkingYears, TrainingTimesLastYear, WorkLifeBalance, YearsAtCompany, YearsInRole, YearsSinceLastPromotion, YearsWithCurrManager.  

In order to determine an appropriate K value to run through the model, a Within Cluster Sum of Square (WCSS) and a Silhouette Coefficient were graphed and have been provided below. When appraising a WCSS score, the “elbow” within the chart is used to denote an appropriate value for "K", in this instance 3. This value is confirmed with a silhouette score of 0.62

<p align="center">
	<img src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/afbeee2a-386c-44ac-bc94-3a3705341905"
 <p/>

<p align="center">
	<img src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/2bdfa4fa-83b3-492d-9732-f9fa23651b6e"
 <p/>

When the K-means machine learning algorithm was run however the clustering result did not provide meaningful or actionable data. The clustering result provided insignificant deviation from the general rate of resignation of 16.1% illustrated in figure 1, with Cluster 0 only increasing by 3.4%

<p align="center">
  <img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/f72a2330-724f-4e9d-9ac2-772a5dda9f24" 
	width="30%">
	
&nbsp; &nbsp;

  <img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/bac9dab6-0b91-41f8-98de-918af8b86a15" 
	width="30%">
 
&nbsp; &nbsp;

   <img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/060ee6b5-f5ad-465d-bca9-9c6d7dbd40e9" 
	width="30%">
</p>

Despite 3 appearing to be the most appropriate "K" value for model clustering, the intent of this report is to provide recommendations to the management team in order to reduce employee turnover. The above modelling result as such does not suit the requirements of management and the model was reconfigured and re-run.

<h4> Model 1 Re-worked: K-Means Cluster: </h3>

The second appropriate "K" value identified in the Silhouette Score plot was 7, with a silhouette score of slightly lower than 0.62 as run in the previous model when "K" = 3. This second clustering model produced a series with a greater degree of significance, however only cluster 0 was deemed by the analysis team to be of merit due to its size and ‘Resigned’ rate of 26.2% (Cluster ratios in Appendix 3). Cluster 3 is also of note with a 0% Resignation rate.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/5f12df59-ab03-46d4-a4df-074be72b8a82"
</p>

<h4> Model 2: DBSCAN (Eps 200) </h4>

The DBSCAN method was implemented as a means to strengthen the results of the data modelling process. DBSCAN modelling clusters data points based on their relative density to one another and unlike k-means modelling, self-identifies the number of clusters through a calculation of density as a function of distance (epsilon) and a minimum number of neighbours (MinPts). The variable assigned to MinPts is usually set to the number of attributes, in this case 14, plus 1, giving a final value of MinPts = 15. Epsilon is calculated in a similar fashion to WCSS, and is plotted on the following page. In a similar fashion to selecting for K with the WCSS value, epsilon is decided by locating the ‘elbow’ in the plot. In this instance an epsilon of 200 was selected. When the model was run however the clustering result was ineffectual, with the vast majority of observations evaluated into a single cluster (cluster 0) with a resignation rate (17.1%) similar to the firm wide value (16.1%) in figure 1.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/55fd0e3d-198d-4a4e-ab55-2d3546941798"
</p>

<h4> Model 2 Re-worked: DBSCAN (Eps 100) </h4>

Following the over-clustering of the previous DBSCAN Model, the algorithm was recalibrated with a decreased epsilon value of 100 in an  attempt to raise the observation density required before the DBSCAN model attributed a cluster value to an observation. This change was made in an attempt to coerce the DBSCAN algorithm into generating a productive clustering outcome model to aid in our investigation. In spite of this change, the resulting model was dominated by a single cluster
and the algorithm classified a large number of variables as ‘noise’.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/9613e94e-0ce1-4971-a895-b044367330d1"
</p>

<h2> Discussion: </h2>

<h4> Recommended Model: </h4>
Of the two approaches implemented in this analysis, the K-means model was able to produce a meaningful set of clusters, with the DBSCAN model proving ineffective. A likely cause for this error was the high dimensionality of the dataframe utilised in the models, and given an extended project timeline the dimensionality of the data could be refined to produce a clearer model of clusters. Out of the 4 models run in this analysis the re-worked Model 1 produced the most applicable set of clusters upon which the following recommendations are based. Cluster 0 is a key cohort for the management team to address and its general characteristics are laid out below. It captures approximately 33% of the total employee structure and has a rate of resignation of 26.2%, or just over 1 in 4 employees.

<h4> Overtime: </h4>

has been identified throughout this report as a major factor contributing to the likelihood of employee resignation. Within cluster 0, If an employee worked overtime they were more likely to resign, than to continue their tenure with the company. Reducing the % of employees who are required to work overtime should be a core priority for the management team.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/ed58000e-cfd1-43ae-8f15-af0d6f3fafa3"
</p>

<h4> Average Weekly Hours Worked (AWHW): </h4>

AWHW is inherently tied to Overtime, however it provides more detailed insights than the binary attribute it falls under. Employees who complete over 40 AWHW but remain under 45, have a far higher retention rate than those who exceed 45 hours.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/6a1bc792-e66b-448a-9602-ee956ae0e3fa"
</p>

<h4> Monthly Income: </h4>

Monthly Income is another core attribute contributing to employee resignation. Within cluster 0, employee’s monthly income ranged from $1,009 to $3,622. Employees who earn under approximately $1,750 a month are more likely to resign than to continue their tenure with the company. Reducing the number of employees taking home less than $1,750 a month will reduce the rate of employee churn amongst low level employees.

<p align="center">
	<img
src="https://github.com/HarryLloyd231196/Employee_Churn_Project/assets/142588638/b24c27f4-0af2-4d4d-86be-f882b37e16a1"
</p>

<h2> Recommendation: </h2>

The data analysis team proposes the introduction of an employee incentive program tailored to target the three attributes summaries above; OverTime, Average Weekly Hours Worked & Monthly Income. The program would allow low income employees earning under $3,800 a month to apply to work an extra 5 hours across the working week in return for an elevated hourly rate across those extra hours. By encouraging employees to share the load of overtime hours, the program will directly reduce the total number of employees working over the critical 45 average hours per week. By directing this incentive at employees earning below $3,800, the program concurrently targets those who are earning below the at-risk monthly income threshold of $3,622 and offers them remuneration above their standard rate. This is designed to lift their monthly income as high as possible without crossing the high risk 45 hour mark. Additionally, Rather than seeing an increase in total overtime worked at the firm, this program is designed to redistribute the required labour and as such will not place additional financial stressors on the firm.

<h2> Conclusion: </h2>

This report steps through three core stages of the data science pipeline. First evaluating each attribute in an exploratory analysis, identifying target variables within the survey data (MonthlyIncome, Age, OverTime, AverageWeeklyHoursWorked) Following this stage, these identified attributes were used as a launching pad to undertake an analysis into the complex relationships between employee attributes and how these influence employee churn and attrition. Finally the report produced 􀃅 unsupervised machine learning models (2 K-Means & 2 DBSCAN), to cluster the data into meaningful groups, allowing for the generation and recommendation of an incentives program designed to retain high churn risk employees.

<H4> Limitations: </H4>

This report utilised the K-Means and the DBSCAN unsupervised machine learning
models to interpret the complex data provided by Human Resources. These models, while effective, can be vastly improved through the implementation of various scaling techniques. Additionally, other machine learning techniques may have been better suited to the provided data, however an investigation into these alternate machine learning models was outside of the scope of this report.

<H4> Additional Comments: </H4>

Throughout the plotting process the colour schemes of Seaborn and Matplotlib repeatedly inverted, resulting in colouring against usual convention. ie. Blue for negative values ie ‘Resigned’ and Red for positive. This occurrence was also inconsistent, with some plots generating appropriately whilst others did not. The colour schemes used throughout this document should be amended to ensure they are consistent and in keeping with convention prior to circulation.

<h4> References: </h4>

ChartExpo (2023) How to Read a Box Plot Chart? Easy-to-follow Steps, ChartExpo, accessed 7 February 2023. [https://chartexpo.com/blog/how-to-read-a-box-plot] 

Corey Schafer 2020 Matplotlib Tutorial (Part 3): Pie Charts, Youtube, accessed 7 February 2023 [https://www.youtube.com/watch?v=MPiz50TsyF0]

Datagy 2022 Seaborn histplot – Creating Histograms in Seaborn, Datagy.io, accessed 8 February 2023 [https://datagy.io/seaborn-histplot/] 

MatPlotlib, n.d., MatPlotlib 3.6.3 Documentation, MatPlotlib, accessed 8 February 2023 [https://matplotlib.org/stable/index.html] 

RMIT University, n.d, Easy Cite referencing guide, RMIT Library, accessed 10 February 2023 [https://www.lib.rmit.edu.au/easy-cite/?styleguide=styleguide-1#stn-5#subtype-36]  

Seaborn (2022) Seaborn.catplot, Seaborn, accessed 7 February 2023
[https://seaborn.pydata.org/generated/seaborn.lineplot.html]

Seaborn (2022) Seaborn.histplot, Seaborn, accessed 7 February 2023
[https://seaborn.pydata.org/generated/seaborn.histplot.html]

Seaborn (2022) Seaborn.lineplot, Seaborn, accessed 10 February 2023
[https://seaborn.pydata.org/generated/seaborn.lineplot.html]

Seaborn (2022) Seaborn.boxplot, Seaborn, accessed 7 February 2023
[https://seaborn.pydata.org/generated/seaborn.boxplot.html]

Seaborn (2022) Seaborn.boxplot, Seaborn, accessed 7 February 2023
[https://seaborn.pydata.org/generated/seaborn.stripplot.html#seaborn.stripplot]

Statology (2022) ‘How to Change Axis Labels on a Seaborn Plot (With Examples)’, Statology, accessed 10 February 2023 [https://www.statology.org/seaborn-axis-labels/]






