Why is mental health important?
Mental health includes our emotional, psychological, and social well-being. It affects how we think, feel, and act. It also helps determine how we handle stress, relate to others, and make choices. Mental health is important at every stage of life, from childhood and adolescence through adulthood. - mentalhealth.gov

According to a September 2017 report conducted by the World Health Organization (WHO), mental health costs the global economy an estimated US$ 1 trillion per year in lost productivity. Disturbances to our mental and emotional well-being affect our ability to do our jobs properly and efficiently. This, in turn, affects an organization’s time, resources, and eventually the bottom line. For every US$ 1 put into scaled up treatment for common mental disorders, there is a return of US $4 in improved health and productivity.

Data Source
Open Sourcing Mental Illness (OSMI) is a non-profit organization dedicated to raising awareness, educating, and providing resources to support mental wellness in the tech and open source communities. They put out a survey in hopes of learning more about the mental health population in the tech workplace.

2014: 1200 responses. 26 questions 
2016: 1433 responses. 63 questions 
2017 and 2018:  123 questions. In 2018 they received 417 responses, in 2017, they received 756 responses. 
New data for the current year is being collected. 

Identifying data
To gather the most information across all survey results, the least common denominator, i.e, 2014 dataset, was used identify the features of the dataset. 

Cleaning data
2017 & 2018 data had to remove some html artifacts in the column names.
Converted column names to lowercase and renamed them to abbreviated labels.
Dropped those who identified themselves as self-employed since they did not answer the same questions
Normalize responses using .replace()
‘No’ = 0, ‘yes ‘= 1
‘Don’t know’ : “I don’t know”
‘Somewhat difficult': 'Difficult', 'Very difficult': 'Difficult',  'Very easy': 'Easy', 'Somewhat easy': 'Easy'
Gender was free-text, so categorized gender to M, F, or non-binary
Dropped age if < 18 or > 90
Dropped NAN values

This left 3089 rows of data.
0 no_employees
['6-25' 'More than 1000' '26-100' '100-500' '1-5' '500-1000']


1 tech_company
[1. 0.]


2 benefits
['Yes' "I don't know" 'No' 'Not eligible for coverage / NA']


3 care_options
['I am not sure' 'No' 'Yes']


4 wellness_program
['No' "I don't know" 'Yes']


5 seek_help
['Yes' "I don't know" 'No']


6 anonymity
['Yes' "I don't know" 'No']


7 leave
['Easy' "I don't know" 'Difficult' 'Neither easy nor difficult']


8 supervisor
['Yes' 'No' 'Some of them' 'Maybe']


9 coworkers
['Some of them' 'No' 'Yes' 'Maybe']


10 treatment
[1 0]


11 family_history
['No' 'Yes' "I don't know"]


12 phys_health_interview
['Maybe' 'No' 'Yes']


13 mental_health_interview
['No' 'Yes' 'Maybe']


14 obs_consequence
['No' 'Yes' 'Maybe/Not sure']


15 age
[37 44 32 31 33 35 39 42 23 29 36 27 46 41 34 30 40 38 50 24 18 28 26 22
 19 25 45 21 43 56 60 54 48 55 20 57 58 47 62 51 65 49 53 61 72 52 66 59
 63 74 70 64]


16 gender
['F' 'M' 'nonbinary']

Target values were identified based on questions to predict the following: 
Can we predict if the employees will seek treatment? (self- awareness)
Does this dataset predict that the company is primarily a technology company? (industry)
Does the dataset predict if the company offers a wellness program? (company support)

The following models were used due to the data being categorical and supervised.
1. Logistic Regression
2. K Neighbor (KNN)
3. Random Forest
4. SVM
5. Deep Neural Network (DNN)

Visualizing the dataset
Tableau
Look the the following link to Tableua to better understand the dataset. 
https://public.tableau.com/profile/ladydatadigger#!/vizhome/MentalHealthinTechCompaniesOSMISurvey2014-2018/MentalHealthinTech?publish=yes

Visualizing the models
https://public.tableau.com/profile/ladydatadigger#!/vizhome/MHpredictorsandscores/ModelingPredictors?publish=yes

DNN and Random Forest were not great models for the dataset, although the training had lead to great accuracy scores, the test data was very low. The knn, logistic regression, and svm models had consistent scores for the models.

Test data accuracy scores- (these score may vary depending on when you run the models)
Tech Company
knn 76.46%
logistic regression 78.78%
svm 78.53%
Family history had a strong weight

Wellness prgraom
knn 71.15%
logistic_regression 74.51%
svm 72.96%
Seek Help had a higher importance

Treatment
knn 68.69%
logistic regression 73.74%
svm 71.67%
Number of employees (1-5) had a strong weight

Each model for the specific target were about the same. Technology company had the highest accuracy score of the 3 targets and would be the best target to predict from this dataset. 

Since we are limited to the 2014 dataset with our common features across all four years, there were columns in the dataset from the most recent survey that may have been better used for features to predict information about mental health in the workplace. As OSMI collects more data in the future, there may be more valuable data to build a stronger predictive model. 

Powerpoint slides are found:
https://docs.google.com/presentation/d/1yMnbbChTID_9j47PwyVKneCFkPziqOBo0LZMMm5KFas/edit?usp=sharing

Sources:
2018 - https://www.kaggle.com/osmihelp/osmi-mental-health-in-tech-survey-2018
2017 - https://www.kaggle.com/osmihelp/osmi-mental-health-in-tech-survey-2017
2016 - https://www.kaggle.com/osmi/mental-health-in-tech-2016
2014 - https://www.kaggle.com/osmi/mental-health-in-tech-survey



