### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 19/09/2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
#### Program 1:
```
import pandas as pd
df=pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")
df
```
#### Output:
<img width="872" height="763" alt="image" src="https://github.com/user-attachments/assets/0c9418e6-5a24-4200-849f-425378650517" />

```
cluster = {
    'Young': df['Age'] <= 30,
    'Middle-aged': (df['Age'] > 30) & (df['Age'] <= 50),
    'Elderly': df['Age'] > 50
}
cluster

```

#### Output:
<img width="904" height="794" alt="image" src="https://github.com/user-attachments/assets/9379e73a-04d3-4467-84ef-e9fb4fd5cb6c" />

```
count=[]
for group, condition in cluster.items():  
    visitors_in_group = df[condition]
    count.append(len(visitors_in_group))
    print(f"Visitors in {group} age group:")
    print(visitors_in_group)
    print(count)
```
#### Output:
<img width="939" height="847" alt="image" src="https://github.com/user-attachments/assets/569a3e3a-f46d-4585-a046-dafc02ffd7e3" />


```
import matplotlib.pyplot as plt
plt.bar(cluster.keys(),count,data=df)
plt.xlabel('Age Group')
plt.ylabel('Number visitors')
plt.show()
```
#### Output:
<img width="851" height="605" alt="image" src="https://github.com/user-attachments/assets/a09533bc-9114-495f-95a7-8e884f6b6c3e" />

#### Program 2:
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

sc=StandardScaler()
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
newdf=sc.fit_transform(df3)
newdf
```
#### Output:
<img width="785" height="731" alt="image" src="https://github.com/user-attachments/assets/93788ef0-68b3-4822-a9b9-5f17074bee29" />


```
kmean=KMeans(n_clusters=4,random_state=42)
df3['cluster']=kmean.fit_predict(newdf)
df3
```
#### Output:
<img width="700" height="852" alt="image" src="https://github.com/user-attachments/assets/9212639f-2b11-4449-acb0-a7d3f81d0f79" />


```
plt.scatter(df3['Age'],df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income in thousands')
plt.show()
```
#### Output:
<img width="927" height="606" alt="image" src="https://github.com/user-attachments/assets/8c6b7236-cd7e-4b2c-ac16-b46493d8002a" />




### Result:
Thus , The implement of Cluster and Visitor Segmentation for Navigation patterns in Python executed Successfully.
