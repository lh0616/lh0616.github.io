---
layout:     post
title:      Lidar based Landcover classification
subtitle:   Paper Reading
date:       2020-3-3
author:     Hohoo
header-img: img/desk2.jpg
catalog: true
tags:
    - Paper Reading
    - lidar mapping
---


> Personal Paper Reading

### Supervised Parametric Classification of Aerial LiDAR Data
#### Abstract
+ Since the terrain is highly undulating, we subtract the terrain elevations using digital elevation models (DEMs, easily 
available from the United States Geological Survey (USGS)) to obtain the height of objects from a flat level. 
+ use height texture (variation in height), intensity (amplitude of lidar response), multiple (two) returns from lidar 
 and luminance (measured in the visible spectrum) from aerial imagery to classify the data into four disjoint classes 
 - trees, grass, roads and building roofs.
+ used mixture of Gaussian models for modeling the training data. Model parameters and the posterior probabilities are 
estimated using Expectation-Maximization (EM) algorithm. 
#### Related Works
##### classification of aerial lidar data into terrain and non-terrain points ---> generating digital terrain models.
+ "Slope based filtering of laser altimetry data" used gradient-based techniques to separate building points from terrain points.
##### classification of aerial lidar data into features such as trees/buildings
+ "The potential of height texture measures for the segmentation of airborne laserscanner data" used height texture for segmentation of lidar data.
+ "Surface clustering from airborne laser scanning data" propose a surface clustering technique for identifying regions in LiDAR data that exhibit 
homogeneity in a certain feature space consisting of position, tangent plane and relative height difference attributes for every point. The surfaces 
are categorized as high vegetation (that exhibit rapid variations in slopes and height jumps), low vegetation, smooth surfaces and planar surfaces.  

+ "A study on using lidar intensity data for land cover classification" assessing separation of different materi- als such as trees, grass, asphalt (roads), 
and roofs based on intensity data that has been interpolated using three different techniques – inverse distance weighting, median filtering and Kriging. 
+ "Evaluation and comparison of terrain classification techniques from ladar data for autonomous navigation" presented an outline of some classification approaches
##### approaches use mixture models for parametric classification
+ "Pattern Classification"
#### Proposed Method
##### classification problem
C classes, d-dim feature x.  The posterior probability of a data sample x belonging to a particular class i can be computed using Bayes rule as:
   
    <p>P(i|x) = p(x|i) * P(i) / p(x)<p>
    <p>p(x) = sum<p(x|i)P(i)>, P(i) is the prior probability of class<p>
it is usualy safe to set P(i) equal to 1/C for all class i, so next is determine the class-density probablity p(x|i). 

That's what Mixture Model do!
A mixture model consists of linear combinations of M basis functions. For example a Gaus- sian mixture can be expressed as:

![image](https://github.com/lh0616/lh0616.github.io/blob/master/_posts/_post_imgs/lidar_based_landcover_classification/img1.png)

##### used feature
+ Normalized Height (H): The LiDAR data is normalized by subtracting the USGS DEM elevation
+ Height Variation (hvar): include standard deviation, absolute deviation from the mean, and the difference between the 
maximum and mini- mum height values, select the last one.
+ Multiple Returns (diff): If the transmitted laser signal hits a hard surface such as terrain or the middle of a building roof,
there is only one return. However, if the laser pulse hits the leaves or branches of trees or even the boundaries of roofs, 
there are at least two recorded returns, one from the top of the tree or roof and the other from the ground.
+ Luminance (L) from the gray-scale aerial image. 
+ Intensity (I):

##### results

![image](https://github.com/lh0616/lh0616.github.io/blob/master/_posts/_post_imgs/lidar_based_landcover_classification/result.png)

considering our own conditions, Intensity + H + hvar may be an option.


--------------------------------------------------------------------------------------------------------------------------------------

###Aerial Lidar Data Classification using Expectation-Maximization
####Abstract
+ based the Expectation-Maximization (EM) algorithm, used  five features (height, height variation, normal variation, 
lidar return intensity, and image intensity) to classify 3D aerial lidar scattered height data into four categories: 
road, grass, buildings, and trees. if lidar only, merge road and grass.
+ we use EM to find maximum-likelihood estimates (MLEs) of the parameters in a Mixture of Gaussians (MoG) model for each class.



