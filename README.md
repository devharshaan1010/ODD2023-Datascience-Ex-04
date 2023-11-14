# ODD2023-Datascience-Ex-04
# AIM
To perform Multivariate EDA on the given data set.

# EXPLANATION
Exploratory data analysis is used to understand the messages within a dataset.
This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
# ALGORITHM
### STEP 1
Import the built libraries required to perform EDA and outlier removal.

### STEP 2
Read the given csv file

### STEP 3
Convert the file into a dataframe and get information of the data.

### STEP 4
Plot the counts in the form of Histogram or Bar Graph.

### STEP 5
Use seaborn the bar graph comparison of data can be viewed.

### STEP 6
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 7
Save the final data set into the file
# CODE:
Name : Devharshaan s
Register number : 212221040035
# diabetes.csv
## Code:
```
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt

data=pd.read_csv("/content/diabetes (1).csv")
df=pd.DataFrame(data)

df
df.info()
sns.boxplot(data=df)
sns.scatterplot(data=df)

z = np.abs(stats.zscore(df['Glucose']))
dfc=df[(z<2)]
z = np.abs(stats.zscore(dfc['BloodPressure']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['SkinThickness']))
dfc=dfc[(z<3)]
z = np.abs(stats.zscore(dfc['BMI']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Insulin']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['DiabetesPedigreeFunction']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Age']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Outcome']))
dfc=dfc[(z<3)]

sns.barplot(x=df["Outcome"],y=df["Glucose"],data=df)
sns.scatterplot(x=df["Glucose"],y=df["BloodPressure"],data=df)

plt.figure(figsize=(17,7))
sns.scatterplot(x=df["Glucose"],y=df["BloodPressure"],hue=df['Outcome'])

glucose_new = df.loc[:, ["Glucose", "Outcome"]]
glucose_new = glucose_new.groupby(by=["Glucose"]).sum().sort_values(by="Outcome")
plt.figure(figsize=(17,7))
sns.barplot(x=glucose_new.index,y="Outcome",data=glucose_new)
plt.xticks(rotation = 90)
plt.xlabel=("Glucose")
plt.ylabel=("Outcome")
plt.show()

g_new=df.loc[:,["Age","BMI"]]
g_new=g_new.groupby(by=["Age"]).sum().sort_values(by="BMI")
#plt.figure(figsize=(10,7))
sns.barplot(x=g_new.index,y="BMI",data=g_new)
plt.xticks(rotation = 90)
plt.xlabel=("Age")
plt.ylabel=("BMI")
plt.show()

sns.barplot(x=df["SkinThickness"],y=df["Age"],hue=df['Outcome'])

df.corr()
sns.heatmap(df.corr(),annot=True)
```
## OUTPUT:
### Dataset:
![1](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/9f5a5023-73d5-4579-a89a-203cbc2b2aab)
![2](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/a4704e34-78be-47ef-831f-3926fd2407ba)
![3](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/2d7ee013-46ea-4aea-8a10-4f3b6f598784)
![4](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/74f98f37-afa0-4736-929b-9957d543ba86)
### After cleaning:
![5](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/1fbdf48b-dc0e-4869-954c-53007dd8ee55)
![6](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/5e80c802-4ff3-4551-b968-506266ff3653)
![7](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/ae12c785-3ce5-4bee-8dca-e8efa82b0605)
![8](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/9320e1cc-426b-4e0e-ba51-c910b19dc6f2)
![9](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/4ff2f867-585b-4c95-b2eb-2c31bdca8ea3)
![10](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/3c9f1508-a3f5-42ff-84b7-b4fccacb0430)
![11](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/1435dcc4-eb2a-4ea2-adb3-e4f66142e980)
![12](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/89d86121-a25e-451b-809a-1e73941d4d9d)
# RESULT:
Thus we have read the given data of diabetes.csv and performed the multivariate analysis with different types of plots.
# SuperStore.cvs
## Code:
```
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt

data=pd.read_csv("/content/SuperStore (2).csv")
df=pd.DataFrame(data)
df
df.info
sns.boxplot(data=df)
sns.scatterplot(data=df)

z = np.abs(stats.zscore(df['Postal Code']))
dfc=df[(z<2)]
z = np.abs(stats.zscore(dfc['Sales']))
dfc=dfc[(z<3)]

sns.scatterplot(x=df["Postal Code"],y=df["Sales"],data=df)
sns.barplot(x=df["Ship Mode"],y=df["Sales"],data=df)

plt.figure(figsize=(17,7))
sns.scatterplot(x=df["Postal Code"],y=df["Sales"],hue=df['Ship Mode'])

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(17,7))
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("SALES")
plt.show()

states=df.loc[:,["Segment","Sales"]]
states=states.groupby(by=["Segment"]).sum().sort_values(by="Sales")
#plt.figure(figsize=(10,7))
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("Sales")
plt.show()

sns.barplot(x=df["Segment"],y=df["Postal Code"],hue=df['Region'])

df.corr()
sns.heatmap(df.corr(),annot=True)
```
## OUTPUT:
### Dataset:
![2 1](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/1d8983d7-e040-439c-a574-50b9f6ab65ea)
![2 2](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/446b4174-7f7b-4539-be44-cb479722a7c3)
![2 3](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/6dad1459-768f-4988-9b08-7a89781f11c0)
![2 4](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/02286cda-ffd4-4754-95a5-6b48f137865b)
### After cleaning:
![2 5](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/e61c0a40-4270-4177-8c06-38d4a87bdc9b)
![2 6](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/767a60cb-3ea2-4522-9d36-f33fd51bc75b)
![2 7](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/9dd64e16-96e0-40d9-82fc-79299476e209)
![2 8](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/32e1f2dc-f4c8-4177-89fc-183f9e4ca3e5)
![2 9](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/2a88511a-6150-4c40-95bc-d6688d8bdecf)
![2 10](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/d2f50739-c4b6-4379-8634-461cf8a08ac3)
![2 11](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/96c97d87-e6d8-49ca-821d-41a76beeec5e)
![2 12](https://github.com/Aakash0407/ODD2023-Datascience-Ex-04/assets/118799103/f8fa8d70-fe13-4568-b971-85b7ad4aaa61)
# RESULT:
Thus we have read the given data of SuperStore.csv and performed the multivariate analysis with different types of plots.
