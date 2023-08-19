# Visualising-Geo-location-clusters

# This code is for an interactive map with clustered markers, where each cluster represents a group of customers  with similar latitude and longitude values. The map can be opened   in a web browser, and users can explore the clusters and individual customer markers.

# Data Loading and Exploration:

- The code starts by loading data from a CSV file named "Customers_lat_long.csv" into a Pandas DataFrame called dCust.
- The .head(10) method is used to display the first 10 rows of the DataFrame, giving you a glimpse of the data's structure.
- The .describe() method provides basic statistical information about the DataFrame, such as mean, standard deviation, minimum, maximum, etc.

# Folium Map Initialization:

- The code imports the folium library, which is used for visualizing geographic data on interactive maps.
- It calculates the median latitude and longitude from the data and initializes a Folium map centered at these median coordinates with a zoom level of 10.
- A red globe icon marker is added to the map, representing the "My Central Retail Location."

# Adding Individual Markers:

- A loop iterates through each row of the DataFrame dCust and adds individual markers for each customer's latitude and longitude.
- The customer's shipment ID is set as a tooltip to display when hovering over the marker.

# KMeans Clustering:

- The code uses the scikit-learn library to perform KMeans clustering on the latitude and longitude data of the customers.
- The Elbow method is used to determine the optimal number of clusters for KMeans. It calculates the sum of squared distances between data points and their assigned cluster centroids for a range of cluster numbers (kBegin to kEnd) and plots the results.
- The Silhouette Score is also calculated for the same range of cluster numbers and plotted to provide an additional measure of cluster quality.

# Creating Cluster Centers DataFrame:

- After determining the optimal number of clusters (12 in this case), KMeans is run again with that number of clusters.
- The coordinates of the cluster centers are extracted and stored in a DataFrame called dClusters.

# Assigning Clusters to Customers:

- The cluster labels assigned by KMeans are added as a new column 'cluster' to the original dCust DataFrame, representing the cluster to which each customer belongs.

# Creating Marker Clusters for Each Cluster:

- A list MCList is created to collect the MarkerCluster objects allocated to the map. These MarkerCluster objects will group customer markers based on their assigned clusters.
- The code iterates through each row of the dClusters DataFrame and creates a new MarkerCluster for each cluster center.
- The MarkerCluster objects are added to MCList.

# Adding Customers to Respective Marker Clusters:

- Another loop iterates through each row of the dCust DataFrame to add the individual customer markers to their respective MarkerCluster based on their assigned cluster index.
- The cluster_index is extracted from the DataFrame, and the customer marker is added to the corresponding MarkerCluster in MCList.

# Layer Control and Saving the Map:

- A LayerControl is added to the map, enabling users to toggle the visibility of different marker clusters.
- The map is then saved to an HTML file named "clusters.html" using the .save() method.

