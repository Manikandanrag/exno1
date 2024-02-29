# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/99e1b97d-1a0c-48e6-97f4-ca4d65200ed5)
```data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/2e9be758-cec2-4e86-903b-4ec023e770da)
```columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/554d7349-6ca8-4445-ba4b-c5237f3dff5b)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
## IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/82b6a109-7de5-4d45-9421-04d89c8f1fb0)
```
ir.describe()
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/41fd9d4c-db3d-41b5-ae49-0ca5d7e786e4)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/043b71bb-b45e-411a-880f-5de3e39097a5)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/c92e6261-8fd3-4df1-9e73-1377511f25ec)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/eccbc091-ddbf-4425-acc9-f232120a074a)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/893c6af3-a30d-499c-a909-82162b68ff3b)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/e710a7e8-15bd-4aca-a152-bc3a01d8a8eb)
## Z SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Manikandanrag/exno1/assets/138849491/3d405559-7aaa-4671-b8ad-1b00f7d8b058)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
# Result
                ``` Thus the given data is read,cleansed and the cleaned data is saved into the file.```
