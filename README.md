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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-04 205446](https://github.com/user-attachments/assets/98ac9420-d334-46fc-91af-2bd0df00729e)
```
df.isnull().sum()
```
![Screenshot 2025-03-04 210028](https://github.com/user-attachments/assets/56422d77-1b6f-42a4-aa99-4f02a6da47a1)
```
df.isnull().any()<br>
```
![Screenshot 2025-03-04 210304](https://github.com/user-attachments/assets/2cd982fb-15f0-4510-b09b-cbf665fac6c0)
```
df.dropna()
```
![Screenshot 2025-03-04 210432](https://github.com/user-attachments/assets/c8989206-c474-4bb0-a326-7ada03b748f5)
```
df.fillna(0)
```
![Screenshot 2025-03-04 210508](https://github.com/user-attachments/assets/bbb96bc8-aae9-4f1c-89a5-6a65dc3dfe8b)
```
df.fillna(method='ffill')
```
![Screenshot 2025-03-04 210609](https://github.com/user-attachments/assets/6adfa1ee-f7ba-4c2c-a34c-acc37ed5903e)
```
df.fillna(method='bfill')
```
![Screenshot 2025-03-04 210652](https://github.com/user-attachments/assets/94a0fd61-837e-448c-b31e-112a687191c1)
```
df_dropped = df.dropna()
df_dropped
```
![Screenshot 2025-03-04 210916](https://github.com/user-attachments/assets/0a58678e-0fa2-4f7f-bba9-545302fc91c6)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-04 211031](https://github.com/user-attachments/assets/c1b98abb-19f2-4486-b02a-49cbb49ec5d2)
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![Screenshot 2025-03-04 211107](https://github.com/user-attachments/assets/a6b7f662-eb6b-46f2-86bf-c159dd3226b8)
```
ir.describe()
```
![Screenshot 2025-03-04 211143](https://github.com/user-attachments/assets/99162c39-9677-410f-a78a-b9bb84ef48de)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-04 211230](https://github.com/user-attachments/assets/b398f218-921e-4045-8983-c79c7467cdb7)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![Screenshot 2025-03-04 211316](https://github.com/user-attachments/assets/02dcc8a6-d6c2-40d0-9fd5-398bf06ed3b2)
```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2025-03-04 211414](https://github.com/user-attachments/assets/0cd26dc2-8d9d-4133-ab65-1266ffef2720)
``
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid

![Screenshot 2025-03-04 211553](https://github.com/user-attachments/assets/bfad9299-0cf2-421d-9ad7-86a4490a83ad)
``
sns.boxplot(x='sepal_width',data=delid)

![Screenshot 2025-03-04 211636](https://github.com/user-attachments/assets/ef94f0f4-783b-45a1-bf55-049bc8451398)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
``

dataset=pd.read_csv("heights.csv")
dataset
```
![Screenshot 2025-03-04 211730](https://github.com/user-attachments/assets/ca58957c-4608-4f6d-917b-80d8edd4c297)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
``

iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/398577f5-8d9d-4a38-8e72-65ee3bea7bb0)
```
low = q1- 1.5*iqr
low
```
![Screenshot 2025-03-04 211841](https://github.com/user-attachments/assets/47447697-93ba-4d31-92d8-ed459fc816ee)
```
high = q3 + 1.5*iqr
high
```
![Screenshot 2025-03-04 211910](https://github.com/user-attachments/assets/2fcb4843-2760-4a0d-b7d4-e6d1ca432bc2)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![Screenshot 2025-03-04 211947](https://github.com/user-attachments/assets/378d4ceb-f673-42fd-a4a0-0fc4c510cd7e)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/40d8c650-7ee8-4e3a-a752-16b8e32f666b)
```
df1 = df[z<3]
df1
```
![Screenshot 2025-03-04 212127](https://github.com/user-attachments/assets/39a061e1-ef2a-4b5e-934e-f3ca0e18e37b)
# Result
          <<include your Result here>>
