# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

AIM:

TO detect and remove the outliers in the given data set and save the final data.

Algorithm:

Step 1
Import the required packages(pandas,numpy,scipy)

Step 2
Read the given csv file

Step 3
Convert the file into a dataframe and get information of the data.

Step 4
Remove the non numerical data columns using drop() method.

Step 5
Detect the outliers in the data set using z scores method.

Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7
Check if the outliersare removed from data set using graphical methods.

Step 8
Save the final data set into the file.

Program:

(1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

```
import pandas as pd
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
sns.boxplot(data=df)
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.35)
q3 = df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
high = q3+1.5*IQR
low = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df1
sns.boxplot(x="price_per_sqft",data=df1)
df1.shape
```

(1) & (2) Examine price_per_sqft column and use zscore of 3 to remove outliers.

```
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(x="price_per_sqft",data=df2)
```

(4) (i)For the data set height_weight.csv detect weight outliers using IQR method

```
df3 = pd.read_csv("/content/height_weight.csv")
df3
sns.boxplot(x="weight",data=df3)
q1 = df3["weight"].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df3[((df3['weight']>=low)&(df3['weight']<=high))]
df4
df4.shape
sns.boxplot(x="weight",data=df4)
```

(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

```
sns.boxplot(x="height",data=df3)
q1 = df3["height"].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df5 =df3[((df3['height']>=low)&(df3['height']<=high))]
df5
df5.shape
sns.boxplot(x="height",data=df5)
```

OUTPUT:

DATASET FOR bhp.csv

![1](https://user-images.githubusercontent.com/118626456/229697882-3bea708f-6b04-4f60-ab0a-441770b59c62.png)

bhp Boxplot

![2](https://user-images.githubusercontent.com/118626456/229697991-1868b9cf-b8c9-45d8-9487-6599a3c8d9eb.png)


DATASET BOXPLOT WITH OUTLIERS(BHP)

![3](https://user-images.githubusercontent.com/118626456/229698077-cac64e21-804a-4ecb-ad3e-ff7ba2b0e5b2.png)


DATASET WITHOUT OUTLIERS(BHP)

![4](https://user-images.githubusercontent.com/118626456/229698144-c3177a1b-2cd2-4951-9322-97f2402b355f.png)

![5](https://user-images.githubusercontent.com/118626456/229698167-6f6ff750-bf9c-4db9-83d2-7a3f5ae870c9.png)

DATASET BOXPLOT WITHOUT OUTLIERS(BHP)

![6](https://user-images.githubusercontent.com/118626456/229698254-7caf6586-0431-4940-addc-cd65a0e534a8.png)


Shape

![7](https://user-images.githubusercontent.com/118626456/229698310-a2ef2eb5-64e0-4340-a2bb-22110bc347cf.png)


DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![image](https://user-images.githubusercontent.com/118626456/229698370-163c784d-287e-4f60-816d-401299193b17.png)


Shape

![image](https://user-images.githubusercontent.com/118626456/229698412-1116be50-184a-48a2-be45-3a5f3e822bf4.png)


DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![image](https://user-images.githubusercontent.com/118626456/229698466-02de6fc0-811e-4e6f-bf7e-20e4ac30a874.png)


DATASET FOR WEIGHT_HEIGHT_CSV

![image](https://user-images.githubusercontent.com/118626456/229698506-da65791b-275b-440b-9bb0-9327b31c4a4d.png)


DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)

![image](https://user-images.githubusercontent.com/118626456/229698656-8679a004-4ac2-4238-8ea9-ed2114e75fee.png)


DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![image](https://user-images.githubusercontent.com/118626456/229698703-b724c1c9-7278-4de5-9560-e42bb2f98603.png)

![image](https://user-images.githubusercontent.com/118626456/229698718-4641ab42-4db5-4d40-b3bc-3d1fbe5bcf09.png)


SHAPE

![image](https://user-images.githubusercontent.com/118626456/229698755-5292aa97-1722-44ff-88cf-2275f0cff068.png)


DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![image](https://user-images.githubusercontent.com/118626456/229698902-2af3ebae-b7b1-489f-ad02-052d12e46c18.png)


FOR HEIGHT COLUMN WITH OUTLIERS

![image](https://user-images.githubusercontent.com/118626456/229698944-bf4564ad-1076-48ca-ace6-03a25613f3c6.png)

![image](https://user-images.githubusercontent.com/118626456/229698975-256c4c19-507b-4593-92d7-6bc79121002c.png)

![image](https://user-images.githubusercontent.com/118626456/229699003-ce98eb1e-a219-40f7-a3a9-fbf8bd903034.png)


Shape

![image](https://user-images.githubusercontent.com/118626456/229699055-8ff2bd76-b707-425c-b060-cf7070145bc3.png)


AFTER REMOVING OUTLIERS BOXPLOT FOR HEIGHT

![image](https://user-images.githubusercontent.com/118626456/229699084-2a8e56f9-e3cb-40b4-b7a9-a567531554ff.png)


Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
