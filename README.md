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
REF NO 212224230144
DATE   12-03-25
```
```
import pandas as pd
lk = pd.read_csv('/content/SAMPLEIDS.csv')
lk
```
![ds s1](https://github.com/user-attachments/assets/c5e924ae-b937-4473-9ad8-912c866eb565)

```
lk.isnull().sum()
```
![ds s2](https://github.com/user-attachments/assets/13eca942-4f78-4260-b7e6-5db2264838de)

```
lk.isnull().any()
```
![ds s3](https://github.com/user-attachments/assets/c88e29f3-e54a-44a3-b79e-65e714e3dedd)

```
lk.dropna()
```
![ds s4](https://github.com/user-attachments/assets/7b3bfdf2-ef16-4a1b-b8a6-b1e115f9f1bf)

```
lk.fillna(0)
```
![ds s5](https://github.com/user-attachments/assets/dd867e0f-5942-46ce-b7d9-03f7c65d16ba)

```
lk.fillna(method = 'ffill')
```
![ds s6](https://github.com/user-attachments/assets/8ce95f3f-8399-475c-83de-75dd3577bb58)

```
lk.fillna(method='bfill')
```
![ds s7](https://github.com/user-attachments/assets/692b4eec-b56d-427a-ab2e-47c683947cba)

```
lk.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![ds s8](https://github.com/user-attachments/assets/02f5dede-ba8c-4d85-956c-9a3edeeb8998)

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
ir= pd.read_csv('/content/iris.csv')
ir
```
![ds s9](https://github.com/user-attachments/assets/93101310-6852-4e7a-94b6-a207f4098313)

```
ir.describe()
```
![ds s10](https://github.com/user-attachments/assets/04dc4c49-2c64-43ae-ba6e-2de13dca4447)

```
sns.boxplot(x = 'sepal_width',data=ir)
```
![ds s12](https://github.com/user-attachments/assets/a07697d9-08c9-44d8-bf5b-fee8da3df07e)

```
q1 = ir.sepal_width.quantile(0.25)
q3 = ir.sepal_width.quantile(0.75)
iqr = q3-q1
print(iqr)
```
![ds s13](https://github.com/user-attachments/assets/f9318558-cb8d-499b-a5bc-ad5ce171d0e5)

```
rid=ir[(ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr))]
rid['sepal_width']
```
![ds s14](https://github.com/user-attachments/assets/77d8f292-90aa-49b7-be8d-69adf5f5c41d)

```
delid=ir[~(ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr))]
delid
```
![ds s15](https://github.com/user-attachments/assets/2ee3acab-877b-47bb-84ad-7e2ebdbcd233)

```
sns.boxplot(x='sepal_width',data=delid)
```
![ds s16](https://github.com/user-attachments/assets/0d2b596b-9f0e-44f2-8c87-63e9442247d6)

```
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![ds s17](https://github.com/user-attachments/assets/3ee48f5f-73f7-4344-9a32-c0909cdcc209)

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

lk = pd.read_csv('/content/heights.csv')
q1 = lk.height.quantile(0.25)
q2 = lk.height.quantile(0.50)
q3 = lk.height.quantile(0.75)
iqr = q3-q1
print(iqr)
```
![ds s18](https://github.com/user-attachments/assets/8d655ba5-acf0-4ca0-ac94-e665a623329d)

```
low = q1-1.5*iqr
high = q3+1.5*iqr
print(low)
print(high)
```
![ds s19](https://github.com/user-attachments/assets/d9848df0-c8bd-4b01-be5d-a537e7bd9fc4)

```
lk1 = lk[((lk['height']>=low) & (lk['height']<=high))]
lk1
```
![ds s20](https://github.com/user-attachments/assets/65235185-41d1-4557-a5a7-ccd33fcacf47)

```
import scipy.stats as stats
z = np.abs(stats.zscore(lk['height']))
print(z)
```
![ds s21](https://github.com/user-attachments/assets/9cf19cc0-4703-457f-b309-004d23bc3e9b)

```
lk1 = lk[z<3]
lk1
```
![ds s22](https://github.com/user-attachments/assets/5149194a-b03c-4c16-bdb8-056be8d68dff)

# Result

```
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
```
