# Ex:05 Feature Generation:
### Date:
## AIM:
To read the given data and perform Feature Encoding & Scaling process and save the data to a file.

## Explanation:
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.

## ALGORITHM:

### STEP 1:
Read the given Data

### STEP 2:
Clean the Data Set using Data Cleaning Process

### STEP 3:
Apply Feature Generation techniques to all the feature of the data set

### STEP 4:
Save the data to the file

## Program:
### Feature Encoding
```python
import pandas as pd
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder
from category_encoders import TargetEncoder
from category_encoders import BinaryEncoder

df=pd.read_csv("/content/Encoding Data.csv")
df

pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

df['bo2']=e1.fit_transform(df[["ord_2"]])
df
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))

df2=pd.concat([df2,enc],axis=1)
df2
pd.get_dummies(df2,columns=["nom_0"])

pip install --upgrade category_encoders

df=pd.read_csv("/content/data.csv")
df

be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb

te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc

```
### Feature Scaling
```python
import pandas as pd
from scipy import stats
import numpy as np
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import MinMaxScaler
from sklearn.preprocessing import Normalizer
from sklearn.preprocessing import MaxAbsScaler
from sklearn.preprocessing import RobustScaler

df=pd.read_csv("/content/bmi.csv")
df
df.head()
df.dropna()

max_vals=np.max(np.abs(df[["Height","Weight"]]))
max_vals

sc=StandardScaler()
df[["Height","Weight"]]=sc.fit_transform(df[["Height","Weight"]])
df.head(10)

scaler = MinMaxScaler()
df1=df.copy()
df1[["Height","Weight"]]=scaler.fit_transform(df1[["Height","Weight"]])
df1.head(10)

scaler=Normalizer()
df2=df.copy()
df2[["Height","Weight"]]=scaler.fit_transform(df2[["Height","Weight"]])
df2.head(10)

scaler=MaxAbsScaler()
df3=df.copy()
df3[['Height','Weight']]=scaler.fit_transform(df3[['Height','Weight']])
df3.head(10)

scaler = RobustScaler()
df4=df.copy()
df4[["Height","Weight"]]=scaler.fit_transform(df4[["Height","Weight"]])
df4.head(10)
```
## OUPUT:
### Feature Encoding Output:
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/2c04cc99-2508-4492-97db-41d8d4b721dd)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/6aeb175e-f2b9-4bd0-bd12-f2523b1c6f97)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/da127fd8-4499-4a0b-9ba3-faebf4f7fdf6)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/3ce20415-92cf-4e37-9e84-59b1ce7367c8)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/3f46faa8-4385-49d0-99dd-f8fad0728ee4)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/13282fe3-898c-4429-b632-6acb64c804ef)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/b994c7bb-7b7d-4f04-947f-26e5229cb965)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/0be9151c-a71d-4775-a442-3e0efd2fa484)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/66d75111-2799-4737-a749-469604edc4b9)
### Feature Scaling Output:
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/c38d98be-6f03-4bbe-b9f0-728cfeb9a7f3)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/6155f6eb-da0a-4294-a9ca-40c891fee7cd)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/546766ce-611c-4def-ad75-8bbaa3a2bdc4)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/1d22778d-8b7c-45b3-9c7e-76ebc1b43755)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/7292802f-5d1c-42a9-a688-a0d8560fd772)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/e59865e4-0a9c-4406-bac9-92163426b5f7)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/20c5054c-7f3d-447f-98db-2faf1f4b2712)
![image](https://github.com/NITHISH74/ODD2023-Datascience-Ex-05/assets/94164665/0d4ee70a-981b-457b-9950-1adf9af302b6)


## RESULT:
Thus the Feature Generation and Feature Scaling process is applied to the given data set.

