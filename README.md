# EXNO2DS
# AIM:
  To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
```
df = pd.read_csv("titanic_dataset.csv")
df
```
![image](https://github.com/user-attachments/assets/c8f56706-4ae0-4839-8c02-f91476839749)


```
df.info()
```
![image](https://github.com/user-attachments/assets/4bb18165-1a81-474b-a8da-4f7fe2d9d379)


```
df.shape
```
![image](https://github.com/user-attachments/assets/1158038f-61e3-4c1f-8b44-ecbbced92202)


```
df.set_index("PassengerId", inplace=True)
```
```
df.describe()
```
![image](https://github.com/user-attachments/assets/4a51de78-0af9-4867-9e22-a827cf9bcdc1)


```
df.nunique()
```
![image](https://github.com/user-attachments/assets/2b4e63cc-df69-459a-bdd8-994b0f5768e5)


```
df["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/0b7787f6-2b4d-4418-8e14-ee653216fe1e)


```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/1f9c94c7-338a-4c89-920f-79005deb1cf7)


```
sns.countplot(data = df, x = "Survived")
```
![image](https://github.com/user-attachments/assets/0eb1870c-4c5f-40eb-ab72-a90b669ffb49)


```
df
```
![image](https://github.com/user-attachments/assets/a53bfcdc-137d-468a-bf0f-b002c571c21e)


```
df.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/fb2a19cb-4a0b-4d1b-8d69-46d437c99f70)


```
df.rename(columns={'Sex':'Gender'}, inplace = True)
df
```
![image](https://github.com/user-attachments/assets/8a5abe4f-da16-4a8c-98fb-5c4ae2ad818a)


```
sns.catplot(x = 'Gender', col = 'Survived', kind = 'count', data = df, height = 5, aspect = .7)
```
![image](https://github.com/user-attachments/assets/96e37385-b484-4163-b1d3-855843363e08)

```
sns.catplot(x = 'Survived', hue = 'Gender', kind = 'count', data = df)
```
![image](https://github.com/user-attachments/assets/1ee8e2d3-0310-4333-9a0f-ea3d0ad98115)

```
df.boxplot(column = 'Age', by = 'Survived')
```
![image](https://github.com/user-attachments/assets/8cb8b905-7a03-4d97-b170-c49850eeddf6)

```
sns.scatterplot(x = df['Age'], y = df['Fare'])
```
![image](https://github.com/user-attachments/assets/259a826f-c28c-4b92-a2ad-70a3314e3938)

```
sns.jointplot(x = 'Age', y = 'Fare', data = df)
```
![image](https://github.com/user-attachments/assets/65800d1b-5d48-470c-89bb-df87dcb1bb48)

```
fig, ax1= plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1, x = 'Pclass', y= 'Age',hue = 'Gender', data = df)
```
![image](https://github.com/user-attachments/assets/3666531f-918b-4fb8-a6e2-628a39e27665)

```
sns.catplot(data = df, col = 'Survived', x = 'Gender', hue = 'Pclass', kind = 'count')
```
![image](https://github.com/user-attachments/assets/2db22244-1487-46b8-b826-4ae69432ef3e)

```
sns.pairplot(df)
```
![image](https://github.com/user-attachments/assets/5a6dc0dc-1ba6-4f1f-9515-7abece7152fb)

```
numerical_df = df.select_dtypes(include=['number'])
corr = numerical_df.corr()
sns.heatmap(corr, annot=True)
```
![image](https://github.com/user-attachments/assets/e9928a4d-c6d5-4cbb-bf5f-32966012c8fb)

# RESULT
Hence performing Exploratory Data Analysis on the given data set is successfully.
