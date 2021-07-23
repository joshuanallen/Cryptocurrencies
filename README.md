# Classification of cryptocurrencies using unsupervised ML models based on coin supply and mining
Analyzing crypto using unsupervised ML

## Purpose
The purpose of this repository is to create a report that incldes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for investing.

## Resources
Data: crypto_data.csv

## Analyis

The dataset provided includes the coin name and abbreviated name, algorithm used, active trading status, proof type, total coins mined, and total coin supply.

**Picture 1.1: Data overview**

![Data overview](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.1_Data_Overview.png)

After cleaning the data to only include cryptocurrencies actively trading and have been mined, we convert the data to numeric variables using `get_dummies()` method to allow for the modeling.

**Picture 1.2: get_dummies() method**

![get_dummies() method](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.2_get_dummies.png)

Next, we standardize the data using the `StandardScaler().fit_transform()` method.

**Picture 1.3: Standardizing data using StandardScaler()**

![Standardizing data](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.3_StandardScaler.png)

Then, we reduce the data dimensions to three principal components using Principal Component Analysis (PCA) algorithm.

**Picture 1.4: PCA**

![PCA](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.4_PCA123.png)

Next, we identify the K-Means cluster value by creating an elbow curve of the PCA model.

**Picture 1.5: Elbow curve**

![Elbow curve](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.5_Elbow_curve.png)

Using the elbow curve, we determined the optimal k-value for running K-Means cluster model was four *(k=4)*, which resulted in a cluster predictions output for four groups ("0", "1", "2", "3").

**Picture 1.6: K-Means cluster model**

![K-means cluster model](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.6_KMeans.png)

Finally, we plot the clustering model in 3D.

**Picture 1.7: Cluster model for PCA in 3D plot**

![Cluster model for PCA in 3D plot](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.7_3D_PCA_plot.png)

Additionally, we add a filterable table of all tradable crypto currencies and their data.

**Picture 1.8: Active trading table**

![Active trading table](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.8_active_trading_table.png)

To understand the coin supply and mining for each coin we normalize the mining and supply numbers using `MinMaxScaler()` and plot them in 2D colored by class.

**Picture 1.9: MinMaxScaler() 2D plot**

![MinMaxScaler() 2D plot](https://github.com/joshuanallen/Cryptocurrencies/blob/d5adb81559823e3d82e4b6ab5e20444706aa8502/images/1.9_minmax_2D_plot.png)


### Conclusions
- By generating an elbow curve from the resulting PCA components, the optimal clusters for K-Means modeling is four. This k-value may stem from there being an extreme outlier in the data set, which generated it's own cluster (cluster 2) of one data point.

- We were able to generate four clusters from the data.
    - Cluster 0 = 286 data points
    - Cluster 1 = 6 data points
    - Cluster 2 = 1 data point
    - Cluster 3 = 239 data points

- Two data points identified in models as outliers based on the PCA 3D plot and the normalized supply and mining 2D plot.
    - BitTorrent
    - TurtleCoin

### Limitations of dataset
Analysis only includes data on cryptocurrency mining and supply limiting the classification model.

### Improvements
Cryptocurrency trading volume, price, mining rate, accessibility, and market share could add data points that further define the clusters.

Additionally, eliminating outliers like BitTorrent and TurtleCoin may help define the clusters more accurately as the plot in Picture 1.9 shows their data points as significant outliers. Would allow for reducing number of clusters to 3.

