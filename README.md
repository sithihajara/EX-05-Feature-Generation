# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 ## FEATURE ENCODING:
1.Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.

2.Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.

3.Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.

4.One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.
## FEATURE SCALING:
1.Standard Scaler
It is also called Z-score normalization. It calculates the z-score of each value and replaces the value with the calculated Z-score. The features are then rescaled with x̄ =0 and σ=1

2.MinMaxScaler
It is also referred to as Normalization. The features are scaled between 0 and 1. Here, the mean value remains same as in Standardization, that is, 0.

3.Maximum absolute scaling
Maximum absolute scaling scales the data to its maximum value; that is, it divides every observation by the maximum value of the variable.The result of the preceding transformation is a distribution in which the values vary approximately within the range of -1 to 1.

4.RobustScaler
RobustScaler transforms the feature vector by subtracting the median and then dividing by the interquartile range (75% value — 25% value).

## ALGORITHM
STEP 1
Read the given Data.

STEP 2
Clean the Data Set using Data Cleaning Process.

STEP 3
Apply Feature Generation techniques to all the feature of the data set.

STEP 4
Save the data to the file.
# CODE
## 1.FEATURE GENERATION FOR Data.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot","Very Hot"]
enc=OrdinalEncoder(categories=[temp])
df["Ord_1"]=enc.fit_transform(df[["Ord_1"]])
df
education=["High School","Diploma","Bachelors","Masters","PhD"]
ed=OrdinalEncoder(categories=[education])
df["Ord_2"]=ed.fit_transform(df[["Ord_2"]])
df
pip install category_encoders
from category_encoders import BinaryEncoder
be=BinaryEncoder()
be.fit_transform(df["bin_1"])
df["bin_1"]=be.fit_transform(df[["bin_1"]])
df
be1=BinaryEncoder()
be1.fit_transform(df["bin_2"])
df["bin_2"]=be1.fit_transform(df[["bin_2"]])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["City"]])
from category_encoders import TargetEncoder
te=TargetEncoder()
te.fit_transform(X=df['Ord_1'],y=df["Target"])
le=LabelEncoder()
df["City"]=le.fit_transform(df[["City"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df1

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df2=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df3=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df4
```
# OUPUT
## Given DataFrame
![data1](https://user-images.githubusercontent.com/94219582/167534363-80929d31-29cf-4d7b-8289-1010e58612ea.png)
## Feature encoding using Ordinal Encoder
![data2](https://user-images.githubusercontent.com/94219582/167534666-9e795285-858e-4620-a546-77017cbb408a.png)
![data3](https://user-images.githubusercontent.com/94219582/167534743-0ec792dc-beca-4dd8-9134-1e5a5511dbe8.png)

## Feature encoding using Binary Encoder
![data4](https://user-images.githubusercontent.com/94219582/167534767-1b7222ed-896b-485d-961c-9eafcb9799ff.png)
![data5](https://user-images.githubusercontent.com/94219582/167534808-060fdbb0-e5c6-406c-b04d-b263937e64b5.png)
![data6](https://user-images.githubusercontent.com/94219582/167534821-7f8a7bf1-f517-4ab3-a269-605dd89d5fa5.png)
![data7](https://user-images.githubusercontent.com/94219582/167534922-4a7c6d3e-15e0-4997-82f0-6e97795cd0d1.png)

## Feature encoding using One Hot Encoder
![data8](https://user-images.githubusercontent.com/94219582/167534840-40baf2ff-f7cf-467a-b71d-18bc0c0039f0.png)

## Feature encoding using Target Encoder
![data9](https://user-images.githubusercontent.com/94219582/167534961-aab842e6-5acd-4c98-91f1-c4f1d962159a.png)

## Feature encoding using Label Encoder
![data10](https://user-images.githubusercontent.com/94219582/167534990-a35ec03e-7e60-4bb0-8656-535c6e3c335f.png)

## Feature scaling using Standard Scaler
![data11](https://user-images.githubusercontent.com/94219582/167535016-4fb4972a-8d00-4bc7-a0c7-a0da859547fc.png)

## Feature scaling using MaxAbs Scaler
![data12](https://user-images.githubusercontent.com/94219582/167535040-3530f7f6-a3a0-4059-8d7c-cf97dfea8e57.png)

## Feature scaling using MinMax Scaler
![data13](https://user-images.githubusercontent.com/94219582/167535060-8c6d84be-ba1f-41a6-a9ee-62f1b1d2f948.png)

## Feature scaling using Robust Scaler
![data14](https://user-images.githubusercontent.com/94219582/167535121-47d54e60-af71-4ac1-8945-06d85bcad93d.png)

# 1.FEATURE GENERATION FOR Encoding.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot"]
enc=OrdinalEncoder(categories=[temp])
df["ord_2"]=enc.fit_transform(df[["ord_2"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df['bin_1']=be.fit_transform(df[['bin_1']])
df
be1=BinaryEncoder()
df['bin_2']=be1.fit_transform(df[['bin_2']])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["nom_0"]])
le=LabelEncoder()
df["nom_0"]=le.fit_transform(df[["nom_0"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df4
```
# OUTPUT:
## Given DataFrame
![enc1](https://user-images.githubusercontent.com/94219582/167535218-b2804f41-c0d3-4e83-9a87-54a7575b42d8.png)

## Feature encoding using Ordinal Encoder
![enc2](https://user-images.githubusercontent.com/94219582/167535255-df1d614a-7a1e-4513-ae6b-254e9a57576b.png)

## Feature encoding using Binary Encoder
![enc3](https://user-images.githubusercontent.com/94219582/167535299-ded60825-13a2-4f26-ac39-f3968d0a12f8.png)
![enc4](https://user-images.githubusercontent.com/94219582/167535308-eef0d040-a71a-4e52-b621-2cb8eaa88898.png)

## Feature encoding using One Hot Encoder
![enc5](https://user-images.githubusercontent.com/94219582/167535501-a03c247d-0e83-49da-8053-a2cb18cf3452.png)

## Feature encoding using Label Encoder
![166867596-54d033ac-cd02-4c29-954c-7176732484cf](https://user-images.githubusercontent.com/94219582/167535581-5f76fce8-f23a-4133-892e-a1e26462c5b6.png)
![166867603-52ef9b02-9f21-497a-b9ef-a137dfcdafe8](https://user-images.githubusercontent.com/94219582/167535598-ecf13db6-f1e0-4fbe-a17a-25cccf688b19.png)

## Feature scaling using Standard Scaler
![enc7](https://user-images.githubusercontent.com/94219582/167535646-f229a681-c110-4a8c-a494-596520d605bb.png)

## Feature scaling using MinMax Scaler
![enc8](https://user-images.githubusercontent.com/94219582/167535675-e0eaf101-d27f-4c68-ac01-fdf3c68629ba.png)

## Feature scaling using MaxAbs Scaler
![enc9](https://user-images.githubusercontent.com/94219582/167535697-156bd10a-2b29-4da5-b7d6-ebfa51859a22.png)

## Feature scaling using Robust Scaler
![enc10](https://user-images.githubusercontent.com/94219582/167535728-5e670875-8265-4314-bbfc-1f2a65101932.png)

# 3.FEATURE GENERATION FOR titanic_dataset.csv
## CODE FOR FEATURE ENCODING AND FEATURE SCALING:
```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df
df.drop("Cabin",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Name",axis=1,inplace=True)
df.isnull().sum()
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
embark=["C","S","Q"]
emb=OrdinalEncoder(categories=[embark])
df["Embarked"]=emb.fit_transform(df[["Embarked"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
df

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df1=pd.DataFrame(ss.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df2

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df3

from sklearn.preprocessing import RobustScaler
rs = RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df4
```
# OUTPUT:
## Given DataFrame
![tit1](https://user-images.githubusercontent.com/94219582/167535781-648506bd-72f4-41e9-a10e-74ce2aa7ffb9.png)

## Resolving null value data
![tit2](https://user-images.githubusercontent.com/94219582/167535801-b039de74-92e3-43e9-af5d-c73ecf5a97c7.png)
![tit3](https://user-images.githubusercontent.com/94219582/167535809-34b69cb4-ca19-4ccf-8b3e-7f554fd8126c.png)

## Dropping unnecessary columns
![tit4](https://user-images.githubusercontent.com/94219582/167535817-2de01e79-d875-4205-a502-aa3dd01813e0.png)

## Feature encoding using Ordinal Encoder
![tit5](https://user-images.githubusercontent.com/94219582/167535902-2429497d-2772-4ee1-9049-3a4160d2bbe0.png)

## Feature encoding using Binary Encoder
![tit6](https://user-images.githubusercontent.com/94219582/167535921-576ffaa0-d07f-4276-9c4b-bf78d9d48323.png)

## Feature scaling using Standard Scaler
![tit7](https://user-images.githubusercontent.com/94219582/167535961-57b1559d-415c-4d35-9906-50074637f713.png)

## Feature scaling using MinMax Scaler
![tit8](https://user-images.githubusercontent.com/94219582/167535991-88182d72-9a8e-4ee9-badd-62c140bdfcac.png)

## Feature scaling using MaxAbs Scaler
![tit9](https://user-images.githubusercontent.com/94219582/167536029-e620d443-933e-4ea1-b111-d3b15bcb7198.png)

## Feature scaling using Robust Scaler
![tit10](https://user-images.githubusercontent.com/94219582/167536060-0384379e-c9e6-4acc-b602-f7707f6addd8.png)

# RESULT:
Feature Encoding process and Feature Scaling process is applied to the given data frame sucessfully.
