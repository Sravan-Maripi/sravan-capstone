## Description:

Our main Aim is to predict wether earthquake will happen or not at a given day and place. So we definitely would not like the model with higher False Neagtive values , since its more dangerous to predict as no earthquake while in reality earthquake happend than predicting earthquake will happen given in reality it did not. We can allow False positive more than False negative

Input to model from dataset has many important features to consider as time,latitude & longitude,depth of quake,magnitude,place, rest other features are error and non supporting features for classification.RandomForestCLassifer
Same parameters were used for randomforest as well to compare the algorithms used with gridsearchCV along with another hyperparamter max_features= ['auto','sqrt','log2'] that will let select features based on log(featues), sqrt(features) etc.


![aws glue capstone](https://user-images.githubusercontent.com/100826424/219316381-f8addf08-3bf7-4405-831a-c8c6e4fd53eb.JPG)


## USGS Dataset:
----------------------------------------
root
         |-- time: timestamp (nullable = true)
         |-- latitude: double (nullable = true)
         |-- longitude: double (nullable = true)
         |-- depth: double (nullable = true)
         |-- mag: double (nullable = true)
         |-- magType: string (nullable = true)
         |-- nst: double (nullable = true)
         |-- gap: double (nullable = true)
         |-- dmin: double (nullable = true)
         |-- rms: double (nullable = true)
         |-- net: string (nullable = true)
         |-- id: string (nullable = true)
         |-- updated: timestamp (nullable = true)
         |-- place: string (nullable = true)
         |-- type: string (nullable = true)
         |-- horizontalError: double (nullable = true)
         |-- depthError: double (nullable = true)
         |-- magError: double (nullable = true)
         |-- magNst: double (nullable = true)
         |-- status: string (nullable = true)
         |-- locationSource: string (nullable = true)
         |-- magSource: string (nullable = true)    
         
