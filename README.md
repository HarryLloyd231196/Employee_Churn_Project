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



