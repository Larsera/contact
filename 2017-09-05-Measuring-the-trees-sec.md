---
title: Measuring the trees
layout: post
author: larsera
permalink: /measuring-the-trees/
source-id: 1Gi1c5Qzk9eB_DwZUoCCjMOB2NbCie0cV1NTes66PfDw
published: true
---
Measuring the trees sec. 2

# Project goal

* Find a cheap measurement system for plant observation

* Communicate the sensor data from sensors to backend

    * Define a protocol

* Create a storage system for the data	

    * Web backend 

    * Database

* Measure one full month worth of data 

* Condition the data 

    * Self-organizing map

    * Splunk/Max

* Present the data

    * Web frontend w/WebGL

    * Actuators

    * Physical light / Arduino experiment

# Measuring the trees 

The understanding of how trees and plants communicate with each other have come a long way in the recent years. As scientists always strive to reach new levels of data quality and quantity, the methods become very expensive. With the progression in smart phones with required sensory equipment, the sensors have had a revolution in pricing. Makers and makerspaces all over the globe have contributed to the rising availability of what was considered unattainable equipment only a few years back. Sensors available in smartphones can now be bought on the cheap from consumer electronic stores, and this means that we can build a sensor rig of good quality for less money than ever.

## Arduino

The Arduino platform has proven to be one of the easiest to work with. We have experimented extensively with data gathering using this platform and different ways to collect the data.

![image alt text]({{ site.url }}/public/Y0laHSjSAyrEmrgOeFAw_img_0.png)

We started out with an Arduino Uno and the DHT11 temperature/humidity sensor. The sensor was placed on the household test plant, and the Arduino was running on stable power from a wall-wart. To store the data, we used an SD card mounted on the Arduino using a SD card shield. The data was logged periodically once every five minutes for 24 hours. After 24 hours, we examined the stability of the measurements and concluded that the Arduino platform is ideal for static logging, but that the collection has to be automated. 

* SMS

* GSM

## ESP8266

The ESP8266 is essentially a Wi-Fi controller running on a 80 Mhz RISC CPU. The device is capable of transmitting data over a built-in Wi-Fi antenna, and can be programmed to do I/O on the 16 GPIO (General Purpose Input Output) pins. 

The ESP8266 package is mounted on a breakout PCB with voltage regulators, pull-up resistors and input-protection. Our test board is the NodeMCU which is FCC approved. The programming is similar to the Arduino and the chip can be flashed using the Arduino IDE. 

![image alt text]({{ site.url }}/public/Y0laHSjSAyrEmrgOeFAw_img_1.png)

Using the same DHT11 sensor as we used on the Arduino, but this time collecting the data over Wi-Fi. To assure a good connection considering the small antenna on the ESP8266, some measurements of the Wi-Fi strength and quality had to be done manually before permanent placement of the equipment. The signal strength/quality measurements was taken using a Sony Xperia Z2 Android smartphone and the "Wifi Analyzer" ([https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer](https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer)) app. We checked the signal strength, bandwidth, and that no other channels was overlapping our transmission channel. After the setup was complete, we checked the signal again from the ESP8266, and enabled auto-connection in case the connection was unstable. We have not accounted for external EMI (electromagnetic interference) or weather conditions. 

We have evaluated three ways of collecting the data automatically. Wi-Fi, SMS, and data transmission over 4G LTE using a websocket. 

## Power efficiency measurements

The equipment has to be run off of a battery, and this sets some requirements for the power efficiency of the circuit. We cannot trust that the standby and peak power usage can give more than a rough estimate, end since this operation will be running for months, we need to be certain of the longevity. 

First off, we measured the power usage of the implementation candidates using a separate Raspberry Pi and a INA219 ([http://www.ti.com/lit/ds/symlink/ina219.pdf](http://www.ti.com/lit/ds/symlink/ina219.pdf)) power monitor. The INA219 measures the voltage drop over a very small shunt resistance of 0.1Ohm. This makes the sensor capable of up to ±3.2A current measurement, with ±0.8mA resolution. 

The shunt resistor is placed in series with the load, and calibrated with the load turned off. 

![image alt text]({{ site.url }}/public/Y0laHSjSAyrEmrgOeFAw_img_2.jpg)

INA219 power monitor

Some of the proposed sensors are active components that also draws power and need to be included in the calculations. For better comparison between platforms rather than sensors, we have limited the measurements to temperature and humidity data provided by the DHT11.

Variance in power efficiency must be accounted for, and some of the components provide reported efficiency variances in the documentation. Our goal is one month of uninterrupted operation, which leads to 730 hours operating on battery. Running on a 3200 mAh lithium polymer battery []

* Effect importance

* Sensor power usage choices

## Weather conditions

The sensor platform should be able to handle tough weather conditions. The weather predictions for a whole month forward in time is pretty uncertain and we cannot expect it to be stable. As we are doing the tests in Norway, the local weather is what we expect to do the measurements in. We do have good historical data on the expected max/min temperatures, and the amount of rain. We are not designing a commercial product, so bear that in mind.

## Ease of use

As referred to in section [], the platform should be easy to use for the researcher. We can split the operation up in the following steps:

1. Deployment on tree / in plant bed

2. Connecting the sensors

3. Adding data collection methods

    1. Connecting to server

    2. Adding memory card

4. Run test suite 

5. Check test results

### A note on the SD card option

We have chosen to support memory cards because data connection over mobile networks can be expensive and unreliable in some countries. This is not something we will be using ourself, but the implementation is provided. The SD card reader software is well documented and tested throughout the Arduino ecosystem, so community support is readily available.

After the deployment and testing phase is over, the data flow needs to be checked. 

## Data formats

Data from the sensors is provided as either raw data for creating custom data formats, or as JSON (JavaScript Object Notation) for easy parsing by web applications and servers.

* Formats

* Fields

* Header(s)

* System data (in header)

    * Battery level

    * System time and timezone

    * Connected devices 

    * Provided methods for testing levels

    * Self-test status

    * Measurement intervals

    * Data formats

### Raw sensor data 

### Formatted sensor data

## Receiving data on the back-end

### Web server 

We have set up Node.js server on a light Ubuntu server instance. This is where we run the Node application that receives the data from the sensor system and saves it in a data base.

To make it easy for beginners, the software is very hardware-agnostic and light-weight, and can be run on any platform that supports Node.js (Linux, Windows, Mac OS). Though, Linux is the only platform we did the full testing and development on. 

# Conditioning the sensor data

On the back end of the data pipeline, something needs to happen before we can present it to the user. 

The data alone is in a raw condition and we can plot it on graphs to show how the plant* behaves over time. The interesting parts lies in the understanding of relations and correlations between different types of data. We will come up with a hypothesis based on well-known facts about the growth of plants under certain conditions, and test them on our model based on the collected data. 

We strive to find useful pieces of information hidden in the data...

## Hypothesis

# Presenting the data

