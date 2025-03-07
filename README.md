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
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![exp1](https://github.com/user-attachments/assets/3f624601-0a03-482a-83be-a02fd9dc4d49)
```
df.isnull()
```
![exp1](https://github.com/user-attachments/assets/882b1a29-584f-4b53-9d80-64de934248ac)
```
df.isnull().sum()
```
![exp1](https://github.com/user-attachments/assets/4ada8619-a013-4c4f-bddb-ba51755fc331)
```
df.isnull().any()
```
![exp1](https://github.com/user-attachments/assets/840a21ef-6093-4062-b350-bbf148601d82)
```
df.fillna(0)
```
![exp1](https://github.com/user-attachments/assets/02c59f50-1da0-4829-9db3-b69e8d9345fe)
```
df.fillna(method='ffill')
```
![exp1](https://github.com/user-attachments/assets/935c35aa-e071-4a3a-a312-966c30efad17)
```
df.fillna(method='bfill')
```
![exp1](https://github.com/user-attachments/assets/4b772042-b0a7-455a-8ac9-0859dbcea56c)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'HYDERABAD','M1':'24','M2':'28','M3':'8','M4':'143','TOTAL':'1432','AVG':'4'})
```
![exp1](https://github.com/user-attachments/assets/c8103ae3-d600-434e-b76a-39c4b77fd71c)
```
df=pd.read_csv("iris.csv")
df
```
![exp1](https://github.com/user-attachments/assets/c103f330-d0c3-4668-ba76-451fce524366)
```
df.describe()
```
![exp1](https://github.com/user-attachments/assets/e46c6205-af22-4240-8105-0801ce358793)
```
df.info()
```
![exp1](https://github.com/user-attachments/assets/7603e72e-2f8d-484d-85d9-595436c513f6)
```
df.shape
```
![exp1](https://github.com/user-attachments/assets/df42f706-89a6-4765-85af-fdc310c1760c)
```
import matplotlib.pyplot as plt
import seaborn as sns
sns.boxplot(x='sepal_width',data=df)
```
![exp1](https://github.com/user-attachments/assets/149e939e-a807-48a9-8d59-47983420cd98)
```
sns.boxplot(x='sepal_length',data=df)
```
![exp1](https://github.com/user-attachments/assets/403a5f55-b5fc-4de5-b57e-d8d31436b03d)
```
Q1=df.sepal_width.quantile(0.25)
Q3=df.sepal_width.quantile(0.75)
iqr=Q3-Q1
print(iqr)
```
![exp1](https://github.com/user-attachments/assets/2a05a12f-7441-4c66-8b93-b7690d33abdc)
```
rid=df[((df.sepal_width<(Q1-1.5*iqr))|(df.sepal_width>(Q3+1.5*iqr)))]
rid['sepal_width']
```
![exp1](https://github.com/user-attachments/assets/19e34623-b4ee-4cd1-a417-b29caf8f0c71)
```
delid=[~((df.sepal_width<(Q1-1.5*iqr))|(df.sepal_width>(Q3+1.5*iqr)))]
delid
```
![exp1](https://github.com/user-attachments/assets/4bb4eb96-928b-4619-a305-c91bdfc8a861)
```
import pandas as pd
import scipy.stats as stats
df=pd.read_csv("heights.csv")
df
```
![exp1](https://github.com/user-attachments/assets/ba7ab7a6-baf1-4769-880f-45df24fcf89b)
```
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)
iqr=q3-q1
iqr
```
![exp1](https://github.com/user-attachments/assets/d9aa7d52-da32-4b0e-a4b9-7befe44027df)
```
low=q1-1.5*iqr
low
```
![exp1](https://github.com/user-attachments/assets/63f1f85b-9400-4c40-a9e8-2d2cd2549117)
```
high=q3+1.5*iqr
high
```
![exp1](https://github.com/user-attachments/assets/31d6596c-658f-411f-ac2a-f07458a9499f)
```
df1=df[((df['height']>=low)&(df['height']<=high))]
df1
```
![exp1](https://github.com/user-attachments/assets/44f053d8-8f88-454e-9985-d6a23040a46c)
```
import numpy as np
z=np.abs(stats.zscore(df['height']))
z
```
![exp1](https://github.com/user-attachments/assets/14794e81-c169-4a62-8f61-91492d6a25b4)
```
df1=df[z>3]
df
```
![exp1](https://github.com/user-attachments/assets/556c607a-7ef5-43a5-bc73-0bd35315aef9)
```
```
# Result
Hence the data was cleaned , outliers were detected and removed.
