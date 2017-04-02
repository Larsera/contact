# Project status
| Task | Status         | Description             |
| ---- |:--------------:| -----------------------:|
| 1 | Finished    | Get real test data from a tree
| 2 | In progress | Research and survey what data is interesting
| 3 | Not started | Deploy more sensors
| 4 | Not started | Evaluate data quality
| 5 | Not started | Process the data in accordance to the findings in 2

# Project description
As climate change and nature conservation becomes a larger part of our everyday life, we are in need of a better understanding of the processes in the nature. Sensor equipment and data communication has become both cheaper and more available in the recent years. We are in a Internet of Things revolution, and data gathering has never been easier.

On the other end of the data stream from the sensors, the data needs conditioning and analysis. The multi-dimensional data can be processed by machine learning algorithms and displayed in a more understandable format. We can also create a web-experience based on real-time data from the sensors.

This thesis will start the collection of data in a small scale, by using a set of basic sensors and an Arduino.  

# Data gathering 
Let's start in a small scale with a single plant.
The plant of choice will be the culinary herb Basil.
It's easy to get hold on from a grocery store, it's easy to work with, and it's a very active and thirsty plant.

## Sensory equipment (at the moment)
* Air temperature
* Air moisture
* Soil moisture
* Water temperature
* Light intensity

# Sensors in a tree
As the experiments are in the start phase, we need to gather basic data from the field. We choose a pine tree to get information from because we also want to measure swaying. It's cold outside at this time of year, and the tree might be less active.

Before we strap the sensors high up in the air, its important to test the system to get measures of the accuracy, resolution and stability. This is especially important considering this is Norway, and the winters here get really cold at night. All he equipment must be operatble in -20 centigrade, and it has to survive effective -30 C, taking humidity and airflow in to account. 

## Hey, why not give the tree a microphone?
So, if the goal is to get some data on the well-being of the tree, why not go the easy way? Just give the tree a microphone and listen to what it says! 

## Swaying data in the wind
Harry Nyquist once told us that we need to sample at least twice the frequency of the input. As the tree is swaying with some frequency, we need to double that for our data sampeling. 

## We got power! (Maybe)
To power the system, we need a battery. The battery need to work at the aforementioned temperature, and it needs to be small enough to fit inside the package. We bought a lithium-polymer cell with a capacity of 2200 mAh at 3.7 V.

# What does the biologists say? 
So, we are informaticians dealing with nature. We measure and gather data. We read up on what we can expect to find. And we try to find interesting things. But what about the biology in this? 


