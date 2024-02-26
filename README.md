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
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![ds1](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/588056fd-924a-48bc-b594-41b151eba4d8)
```
data = pd.get_dummies(data)
data.isnull().sum()
```
![ds2](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/2b28b5f7-64c3-42bd-bd6c-266cc69588da)


```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![ds3](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/70075fe7-1e05-452a-9a4a-fb903f4fbb6a)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```

![ds4](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/74367693-0ad2-43d2-bf1c-f8511dc61b9a)

# IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![ds5](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/da7f0b02-2b60-47f7-8a98-47ac41ee965c)
```
ir.describe()
```
![ds6](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/cde401b8-75c3-4307-8df1-0ac2a12f495e)
```
sns.boxplot(x='sepal_width',data=ir)
```
![ds7](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/64d1abcf-3075-4562-ba4f-a1482d008efc)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![ds8](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/e52e93b5-6d54-44d1-adee-1bcbe214b708)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![ds9](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/5d36a7d6-6273-437d-8dff-8ee54e6769e0)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![ds10](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/f76fc0b3-5afb-4714-979f-f1fe69658f6a)
```
sns.boxplot(x='sepal_width',data=delid)
```
![ds11](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/f92a2ad2-2b92-4ec6-96b3-233841e4751a)

# Z Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![ds12](https://github.com/HemadharshiniMurugan/exno1/assets/119404809/52f30d41-8009-414f-9ca6-27601385600c)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```


# Result
Thus the given data is read,cleansed and the cleaned data is saved into the file.

