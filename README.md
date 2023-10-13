# Ex:05 Feature Generation
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

## RESULT:
Thus the Feature Generation and Feature Scaling process is applied to the given data set.

