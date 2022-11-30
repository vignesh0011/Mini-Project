# Mini-Project
## Aim: 
To implement data science techniques in weight-height dataset
## Methodologies:
![image](https://user-images.githubusercontent.com/53014593/204821149-4a41b6b8-5dfa-4f21-8601-4e3e5df75137.png)
## Program:
~~~
import numpy as np
import pandas as pd
import io
from scipy import stats

from google.colab import files
uploaded = files.upload()

df = pd.read_csv(io.BytesIO(uploaded['weight-height.csv']))
print(df)

df.head()
df.isnull().sum()
df.drop("Gender",axis=1,inplace=True)
df.head()
df1=df.copy()
df.boxplot()
df.shape

z=np.abs(stats.zscore(df))
z

df1=df1[(z<3).all(axis=1)]
df1

df2=df.copy()
df2.head()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
q1
q3
iqr=q3-q1
iqr
df2_new=df2[((df2>=(q1-1.5*iqr))&(df2<=(q3+1.5*iqr))).all(axis=1)]
df2_new.shape
df2_new.boxplot()
df2
~~~
## Output:
![1](https://user-images.githubusercontent.com/53014593/204822712-ce726fdd-f13e-4ae8-8d8f-9eb75797e287.png)

![2](https://user-images.githubusercontent.com/53014593/204822792-af60c31d-7f48-4981-ab8c-48d220bc0af9.png)

![3](https://user-images.githubusercontent.com/53014593/204822837-6b834cb9-143b-40b4-ab50-09fc2710f1bb.png)

![4](https://user-images.githubusercontent.com/53014593/204822893-833d04e7-3335-4dff-b711-309021181516.png)

![5](https://user-images.githubusercontent.com/53014593/204822909-00481f75-4531-4a27-bb56-8d357b4a1a96.png)

![6](https://user-images.githubusercontent.com/53014593/204822921-44e215d2-ca62-4066-9067-09de2ac91076.png)

![7](https://user-images.githubusercontent.com/53014593/204822942-47624127-351c-4d6d-b15d-70fd3309e4af.png)

![8](https://user-images.githubusercontent.com/53014593/204822948-7adcc515-4fda-4194-ac49-ad5fa9802cfc.png)



