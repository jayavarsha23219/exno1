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

# Coding:
## DEVELOPED BY: JAYAVARSHA T
## REGISTER NO: 212223040075
## Data Cleaning: 
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/af33a3be-4062-43d6-8e21-e30564b751c6)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/f54803c0-41d4-4ae2-ab3b-ac66a0108521)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/44888638-a843-4568-b05c-da37e88c3a55)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/854a9777-4236-4b45-bbfb-00f80a535483)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/0e5048c3-7f71-4641-a093-f0da75601b65)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/9dc9237a-96b7-4e6f-8022-0ea12ec24e66)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/d29b9b4d-da50-45a2-bdca-51dc40fc3374)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/118c01b5-0b92-4ec3-99a9-d27e7b6ba7ca)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/ad8df2c3-0669-43a9-a448-59394c7878e4)
```
import pandas as pd
```
```
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/71236c70-a7d7-4623-acd2-5d8d28461fc1)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/68ebc5a5-39b9-4b19-bd61-e9215e970f94)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/90556baa-0257-4784-b8a1-28590bff558d)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/6ff8aa8f-131b-4056-945b-632e7b015882)
```

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/aa5ce985-032f-47f6-9695-b68a2a96b4bc)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/641bd66f-596b-452f-9502-1d9458743988)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/1fe42bd6-c5ad-4751-8dac-b97cfe80c036)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/407f8654-b53e-4602-8c83-79bd6e0132af)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/5892ce45-325c-464b-b0c0-3f139a925957)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/9072f63a-01d0-493b-849e-73a2844c4b9c)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/0956460c-3d56-406c-b830-0146a613adef)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/9fe0e945-525d-41e5-b0dc-ce37fd3a5789)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/a7506d61-483d-428f-9c67-d437fb2e4912)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/1935fe23-41bc-4e73-95a7-515879e4cd01)

# Result
    Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.      
