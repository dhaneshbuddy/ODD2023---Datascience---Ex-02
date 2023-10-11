# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

### Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set.
An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out).
Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.
### Algorithm:
- Step1: Read the given Data.
- Step2: Get the information about the data.
- Step3: Detect the Outliers using IQR method and Z score.
- Step4: Remove the outliers.
- Step5: Plot the datas using Box Plot.
```
212222110001
AAKASH P
```
### Code:
##### bhp.csv:
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
##### height_weight.csv:
```Python
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
### Output:
##### bhp.csv:
![1](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/49a1b730-bfd9-402c-9241-5dee338ed628)
![2](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/0e8cfed7-7abb-4419-b3b8-9124c52e2efa)
![3](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/8160f2e0-a8c0-4635-bae8-7634517df687)
![4](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/6f4cb465-c465-4b77-80cb-ed4b5962eca0)
![5](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/3ec077fc-0f3d-4fcb-a1b6-b48082da8580)
##### weight_height.csv:
![1 1](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/15ec0ae8-3637-4867-9af4-4cac41341940)
![1 2](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/99b894dd-f3b4-46a1-ac8e-0925f53f4ea6)
![1 3](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/776f5e96-0f50-42e2-9d5c-28b9acba97c3)
![1 4](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/e2bb8dca-8ca8-4fc8-a787-d00dd9ff5963)
![1 5](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/dd6d59f6-22b4-423c-b0b4-9babc5c63c3e)
![1 6](https://github.com/Aakash0407/ODD2023---Datascience---Ex-02/assets/118799103/0d824957-98a8-4062-abc7-5cd84057ec15)
### Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.

