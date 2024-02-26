# Exno:1 Data Cleaning Process

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
![image](https://github.com/Lokhnath10/exno1/assets/138969918/98a7dd6a-b960-4099-88e5-35930eb9690a)

```
data = pd.get_dummies(data)
data.isnull().sum()
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/e4f43762-dff7-4c83-8e8c-ef959ed98696)
```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/81cb1f74-30eb-4a17-897d-b56e37d2a840)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/312f5f58-7a38-47c1-9510-0a19bbcff37a)
## IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/b23cba58-5533-4a49-b347-1607c4484550)
```
ir.describe()
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/8f12bb16-bd91-4f6e-82b2-938df4392ab8)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/d617d165-aa7a-4e92-a06d-98d46589a645)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/1a49638b-a5a2-44bb-a23b-54ef29d093f3)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/a76dfddd-d6d5-4cd8-a079-4a920abf5f21)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/6a5582ad-b434-45a0-aedc-91934839bf7a)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/59053bd9-167e-46fc-b1dc-586a00e6b41b)
## Z Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Lokhnath10/exno1/assets/138969918/3aa6e127-78ff-4cb6-88e1-2919c1f1def6)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

# Result
            Thus the given data is read,cleansed and the cleaned data is saved into the file.
