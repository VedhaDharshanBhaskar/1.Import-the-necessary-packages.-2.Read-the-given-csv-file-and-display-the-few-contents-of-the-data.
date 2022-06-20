# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1.Import the necessary packages.
2.Read the given csv file and display the few contents of the data.
3.Import K Means and use for loop to calculate the within cluster sum of squares the data.
4.Plot the wcss for each iteration, also known as the elbow method plot.
5.Predict the clusters and plot them.

## Program:
```

Program to implement the K Means Clustering for Customer Segmentation.
Developed by: REETHIKA.R
RegisterNumber:  212219220042

import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("Mall_Customers.csv")
df.head()

df.info()
df.isnull().sum()

from sklearn.cluster import KMeans
wcss = []  
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()

km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="yellow",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="cyan",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="skyblue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="violet",label="cluster4")
plt.legend()
plt.title("Customer Segments")
plt.show()
```

## Output:

##intial data set:

![image](https://user-images.githubusercontent.com/98681990/174661679-729d7633-7309-4e58-9b09-f4d7f0ceb4ae.png)

##data information:

![image](https://user-images.githubusercontent.com/98681990/174661709-c3c92854-9675-43b3-8d1c-9bca843c8691.png)

##Elbow graph:

![image](https://user-images.githubusercontent.com/98681990/174661769-a24aad62-9109-4bdc-9aa7-c481f0aa1012.png)

##Cluster graph:

![image](https://user-images.githubusercontent.com/98681990/174661802-8b294213-8870-46fd-8dc9-954ac63b2ecc.png)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
