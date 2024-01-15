# CryptoClustering

In this project, we are using our knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

Following steps have been performed to create an Unsupervised Machine Learning model :

1. Prepare the Data
   Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.

   Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

2. Find the Best Value for k Using the Original Scaled DataFrame
   Use the elbow method to find the best value for k using the following steps:

   Create a list with the number of k values from 1 to 11.
   Create an empty list to store the inertia values.
   Create a for loop to compute the inertia with each possible value of k.
   Create a dictionary with the data to plot the elbow curve.
   Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

   ** The value of k found by this method is : 4 and corresponding value of inertia is : 79.022435**

3. Cluster Cryptocurrencies with K-means Using the Original Scaled Data
   Use the following steps to cluster the cryptocurrencies for the best value for k on the original scaled data:

   Initialize the K-means model with the best value for k.
   Fit the K-means model using the original scaled DataFrame.
   Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
   Create a copy of the original data and add a new column with the predicted clusters.
   Create a scatter plot using hvPlot as follows:
   Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
   Color the graph points with the labels found using K-means.
   Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

   ** Clusters formed using Original Scaled Data are overlapping and not well-defined **

4. Optimize Clusters with Principal Component Analysis
   Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.

   Retrieve the explained variance to determine how much information can be attributed to each principal component.

   ** The total explained variance of the three principal components is : 0.8950316570309841 **

   Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

5. Find the Best Value for k Using the PCA Data
   Similar to step 2 but using PCA data instead of Original Scaled Data

   ** The value of k found by this method is : 4 (same as found using Original Scaled Data) and corresponding value of inertia is : 49.665497**

6. Cluster Cryptocurrencies with K-means Using the PCA Data
   Similar to step 3 but using PCA data instead of original scaled data
   Scatter plot with x-axis as "PC1" and the y-axis as "PC2"

   ** Clusters formed using PCA are tighter and well-defined **

Conclusion: The impact of using fewer features to cluster visually shows the following :

     **1. Elbow Curves:** Lower value of inertia using PCA than original features, indicating the sum of squared distances within clusters is smaller. This will result in overall tighter clustering and better performance of the model

     **2. Cluster Graphs:** The clusters formed using PCA are not overlapping and are well-defined, while the clusters formed using original features have no clear separation. Having reduced the features using PCA has helped decrease the impact of less important features hence creating a model that can derive more meaningful information.

References:
https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
https://medium.com/analytics-vidhya/unsupervised-learning-principal-component-analysis-pca-dc94fecef09b
https://www.markdownguide.org/cheat-sheet/
