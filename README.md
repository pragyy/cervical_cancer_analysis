# Cervical Cancer Predictor

- In this project the risk factors associated with the cervical cancer in women is analysed. 
- Then using the risk factors as independent variable for regression it is predicted whether they have cervical cancer or not.

## Codes and resources used

**Python version:** 3   
**Packages:** pandas, numpy, matplotlib, seaborn, sklearn    
**Dataset Link:** https://archive.ics.uci.edu/ml/datasets/Cervical+cancer+%28Risk+Factors%29#     
**Multioutput regression Model Article:** https://machinelearningmastery.com/multi-output-regression-models-with-python/     

## About the Dataset

The dataset was collected at 'Hospital Universitario de Caracas' in Caracas, Venezuela. The dataset comprises demographic information, habits, and historic medical records of 858 patients. Several patients decided not to answer some of the questions because of privacy concerns (missing values).

The features cover demographic information, habits, and historic medical records. This dataset focuses on the prediction of indicators/diagnosis of cervical cancer.

#### Attribute Information:

- (int) Age     
- (int) Number of sexual partners    
- (int) First sexual intercourse (age)      
- (int) Num of pregnancies       
- (bool) Smokes        
- (bool) Smokes (years)        
- (bool) Smokes (packs/year)         
- (bool) Hormonal Contraceptives         
- (int) Hormonal Contraceptives (years)         
- (bool) IUD         
- (int) IUD (years)         
- (bool) STDs         
- (int) STDs (number)         
- (bool) STDs:condylomatosis         
- (bool) STDs:cervical condylomatosis         
- (bool) STDs:vaginal condylomatosis         
- (bool) STDs:vulvo-perineal condylomatosis         
- (bool) STDs:syphilis         
- (bool) STDs:pelvic inflammatory disease         
- (bool) STDs:genital herpes         
- (bool) STDs:molluscum contagiosum         
- (bool) STDs:AIDS         
- (bool) STDs:HIV         
- (bool) STDs:Hepatitis B         
- (bool) STDs:HPV          
- (int) STDs: Number of diagnosis         
- (int) STDs: Time since first diagnosis        
- (int) STDs: Time since last diagnosis         
- (bool) Dx:Cancer         
- (bool) Dx:CIN         
- (bool) Dx:HPV         
- (bool) Dx         
- (bool) Hinselmann: target variable         
- (bool) Schiller: target variable         
- (bool) Cytology: target variable         
- (bool) Biopsy: target variable     

## Data Cleaning

There are a lot of missing values in the dataset. So I made the following changes in the dataset.

- Dropped rows with more that 15 cell value missing.
- Dropped columns: *"STDs: Number of diagnosis, STDs: Time since first diagnosis, STDs: Time since last diagnosis"* as these columns are not much revelant. Moreover, many values are missing so imputation will skew the result a lot.
- Filled missing column values *Number of sexual partners* with 18 (assuming the stanrdard age for first sexual intercourse).
- Imputed contraceptive information (both IUD and Hormonal contraception) with zeros assuming women did not go for sexual protection.
- For missing values in regarding the smoking history, computed the mean which came out to be approx. 0.14 so, filled with zero since it is boolean.

## Exploratory Data Analysis

Below are the few highlights of the EDA:

![Plot 1](/cervical_cancer_analysis/violinplot.PNG)
![Plot 2](/cervical_cancer_analysis/catplot.PNG)

## Model Building

I split the dataset into 80:20 for training and testing. 

The dataset has multiple inputs as well as multiple target variable. The risk factors associated with cervical cancer are input variables and the columns *Hinselmann, Schiller, Cytology, Biopsy* are the target variables and if anyone of it is True then it indicates positive cervical cancer.

So for this type of dataset multioutput regression was performed. The regression models which I tried are:

1. Linear Regression
2. Lasso Regression
3. K-nearest neighbour regression
4. Decision Tree regression
5. Random Forest regression
6. Wrapper Multioutput regression
    - Direct Multioutput Regression
    - Chaianed Multioutput Regression
  
## Model Evaluation

For evaluating all the model I calculated the mean absolute error as it is the easiest to understand.

The K-nearest neighbour regression model far outperformed the other approaches on the test and validation sets.

- Linear Regression: 0.138
- Lasso Regression: 0.132
- K nearest neighbour Regression: 0.118
- Decision Trees Regression: 0.152
- Random Forest Regression: 0.146
- Direct Multioutput Regression: 0.166
- Chained Multioutput Regression: 0.261
