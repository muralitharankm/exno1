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
import numpy as np

import pandas as pd

data=pd.read_csv("/content/SAMPLEIDS.csv")

data
<img width="1821" height="861" alt="image" src="https://github.com/user-attachments/assets/56d22fed-5151-4f6c-a517-d364cb18befd" />
data.head(5)
<img width="1829" height="317" alt="image" src="https://github.com/user-attachments/assets/9c04122f-e997-49d5-851d-6b32ad26cf83" />
data.tail(8)
<img width="1829" height="361" alt="image" src="https://github.com/user-attachments/assets/ca3e3efa-be80-4c25-98e6-0c0e6663ca3b" />
data.isnull()
<img width="1824" height="761" alt="image" src="https://github.com/user-attachments/assets/e0df20f5-5fba-4ac2-b0a2-a5d97ba18ba1" />
data.notnull()
<img width="1831" height="768" alt="image" src="https://github.com/user-attachments/assets/7060a25d-bcff-42c3-9a08-6041c8f91812" />
data.isnull().sum()
<img width="1828" height="512" alt="image" src="https://github.com/user-attachments/assets/105dca17-e0b7-426a-a3fd-c80cd4eea372" />
data.isnull().any()
<img width="1828" height="510" alt="image" src="https://github.com/user-attachments/assets/5d84137d-4c3d-469c-91be-898b195050d9" />
data.dropna(axis=1)
<img width="1831" height="768" alt="image" src="https://github.com/user-attachments/assets/47acbb19-e8ac-4e30-bf6b-46473aae1758" />
data.dropna(axis=0)
<img width="1836" height="510" alt="image" src="https://github.com/user-attachments/assets/a954093d-29fe-4f64-80df-f8d6f83dc5ae" />
data.fillna(0)
<img width="1830" height="761" alt="image" src="https://github.com/user-attachments/assets/8a1a5275-8842-4e3a-9a07-7a39899baf2d" />
data.fillna(method="ffill")
<img width="1810" height="820" alt="image" src="https://github.com/user-attachments/assets/a7543641-c254-4fa9-a461-d3cd86327ae6" />
data.bfill()
<img width="1831" height="762" alt="image" src="https://github.com/user-attachments/assets/27916daf-ab9e-4acb-88f5-104fe889a049" />
data.fillna({'REGNO':0, 'NAME':'MURALITHARAN'})
<img width="1548" height="713" alt="image" src="https://github.com/user-attachments/assets/ff1f18dc-093b-4be6-a315-16185e94254a" />

ir =pd.read_csv("/content/iris.csv")

ir
<img width="1828" height="550" alt="image" src="https://github.com/user-attachments/assets/aa40ccbe-3307-4446-9fbd-e102291830fd" />
ir.describe()
<img width="1827" height="355" alt="image" src="https://github.com/user-attachments/assets/e77887be-c0f5-4905-95cc-fc30111b883b" />
import seaborn as sns

sns.boxplot(x="sepal_width",data=ir)
<img width="1829" height="543" alt="image" src="https://github.com/user-attachments/assets/d5694601-8e19-44c5-a629-48318a9ac468" />
q1=ir.sepal_width.quantile(0.25)

q3=ir.sepal_width.quantile(0.75)

iqr=q3-q1

print(iqr)
<img width="1831" height="143" alt="image" src="https://github.com/user-attachments/assets/19834df4-f2bb-461e-beed-dea70d583036" />
rid =ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]

rid['sepal_width']
<img width="1831" height="296" alt="image" src="https://github.com/user-attachments/assets/97b030cb-df29-4921-8014-00dfe1807f4b" />
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]

rid
<img width="1831" height="545" alt="image" src="https://github.com/user-attachments/assets/8c88601b-7ff8-45f4-8f14-794e6fe95ca1" />
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]

rid['sepal_width']
<img width="1827" height="538" alt="image" src="https://github.com/user-attachments/assets/91279cf5-a45a-42b6-9cba-a55d1f7b5741" />
import numpy as np

import scipy.stats as stats

z=np.abs(stats.zscore(ir.sepal_width))

z
<img width="1829" height="674" alt="image" src="https://github.com/user-attachments/assets/a85a8d19-0828-45f5-b4c8-68172e1e9eb6" />

# Result
Thus the programs are executed successfully.
