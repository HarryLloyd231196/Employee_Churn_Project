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








