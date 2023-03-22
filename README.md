Table of Contents

[Introduction](#introduction)

[Pollutants of interest](#pollutants-of-interest)

[Main List](#main-list)

[Commercial Devices](#commercial-devices)

[Ozone (O3)](#ozone-o3)

[Thresholds](#thresholds)

[Sensor Technologies](#sensor-technologies)

[Sensors (by working principle)](#sensors-by-working-principle)

[Sensor Selection Parameters](#sensor-selection-parameters)

[Sensing Problems](#sensing-problems)

[Data Acquisition & Broadcast](#data-acquisition--broadcast)

[Measurements](#measurements)

[Data Broadcast](#data-broadcast)

[Power Management](#power-management)

[Sensor Testing](#sensor-testing)

[MCU](#mcu)

[Cloud Platform](#cloud-platform)

[BME 680](#bme-680)

[MiCS 6814](#mics-6814)

[ENS160](#ens160)

[Grove Multichannel v2](#grove-multichannel-v2)

[Actions Ahead](#actions-ahead)

[Localization](#localization)

[References](#references)

# Introduction

This document is designed to record the course of work of University of Patras for the 6.4 part of the TwinAir project, from its start until its completion and document the creation and realization of the ongoing goals. It will also serve as a map for communicating the work of 6.4 outwards to the other partners and note the contributions of other partners towards 6.4.

The goal of 6.4 is the creation of a wearable wrist device capable of measuring indoor air pollution.

The main themes of the document are the pollutants that are going to be targeted and the sensors that will accomplish that. Both of them need analysis of their requirements, limitations and actions to effectively conduct our research and development process.

That means the first step is to list the indoor pollutants that we want to monitor and the reasons why those specific gases are selected.

The second step is to list the sensors that cover those gases and to explain why those sensors' specifications cover the necessary requirements.

# Pollutants of interest

### Main List

The pollutants of interest in the general sense of the project are various and many of them only detectable by expensive and/or big equipment. The list of pollutants is narrower concerning the wearable device, because of the size limitation of the sensors.

The reasoning that there is such freedom in addressing Indoor Air Quality so freely is mainly based on the lack of regulations concerning how the Index is derived. The Indoor Air Quality Index is yet a suggestive Index and not a regulatory measure as the Outdoor Air Quality Index. Therefore, the process with which we decided which gases are going to be monitored by our wearable device is based on the existing regulations and research concerning the Outdoor Air Quality and the research concerning what are the major hazardous pollutants indoors

The initial list of the pollutants of interest is the following :

-   Particulate Matter
-   CO2
-   VOC
-   CO
-   NO2
-   NO
-   O3
-   SO2

To find the pollutants that matter for indoor air pollution, the first step was studying the outdoor air quality indexes, which state clearly which pollutants matter and which are monitored. The outdoor indexes are set by regulations and therefore are strict and consistent among different regulatory bodies.

**E.P.A**

The E.P.A (U.S Environmental Protection Agency) establishes the **outdoor** air quality index based on five pollutants [1]

-   Ozone
-   Particulate Matter
-   CO
-   SO2
-   NO2

It should be highlighted that these pollutants are for outdoor air quality. Later on the document it will be explained why Ozone and SO2 will not be monitored.

**W.H.O**

The **W.H.O** (World Health Organization) outlines a number of potentially hazardous organic and non-organic substances that can have adverse health effects in **indoor** spaces [2]. These substances are displayed below. Out of those substances, the ones that are both determined that are hazardous and can also be monitored by a wearable device are :

-   Particulate Matter
-   CO
-   SO2
-   VOC
-   NO2

![](media/475598c9bd281a379f0150fa0ef364c9.png)

Group 1 included pollutants for which WHO guidelines for indoor air were needed and that the WHO requested to plan their development. Group 2 included pollutants of potential interest, but the group concluded that further investigation would be needed before it was clear whether there was sufficient evidence to warrant their inclusion in the guidelines at present.

**Australian Health Agency**

The Australian Health Agency monitors the listed pollutants **outdoors** :

-   Particulate Matter
-   CO
-   VOC
-   NO2

According to the Australian Health Agency, SO2 is not monitored because of the lack of Heavy Industry. [3]

**European Environment Agency**

The European Environment Agency states that the key pollutants with which the Air Quality Index **outdoors** is determined are the following [4] :

-   Particulate Matter
-   CO
-   SO2
-   VOC
-   NO2

### Commercial Devices

It should be noted that most commercial devices marketed as Indoor Air Quality Monitors usually base their calculations on VOC and Particulate Matter. These devices offer CO2 detection, but most of the time the CO2 is calculated based on the equivalent CO2 equation, meaning that CO2 is not directly measured with a sensor, but inferred from VOC levels. Commercial devices that also measure CO, NO2 and SO2 levels are firstly less common and secondly more expensive.

### Ozone (O3)

Concerning Ozone, the decision not to include it onto the wearable device was based on the absence of major indoor ozone sources and ozone sinks. Ozone is monitored for Outdoor Air Quality because its formation and its sources are outdoors, whereas Ozone indoors mainly exists because of outdoor ozone penetrating into the indoor environment.

Citing directly from the source [5]:

Ozone at ground level – not to be confused with the ozone layer in the upper atmosphere – is one of the major constituents of photochemical smog. It is formed by the reaction with sunlight (photochemical reaction) of pollutants such as nitrogen oxides (NOx) from vehicle and industry emissions and volatile organic compounds (VOCs) emitted by vehicles, solvents and industry. As a result, the highest levels of ozone pollution occur during periods of sunny weather.

### tVOC

![](media/6a7b94dbbb863abe575ceaba1216aca2.png)![](media/a98adfe3720d8dc560aaca700f80a740.png)![](media/f08e652dfaa06f1d159bdf3bd5a76b4c.png)

# Thresholds

The W.H.O guidelines apply worldwide to both outdoor and indoor environments and are based on expert evaluation of current scientific evidence for:

-   particulate matter (PM)
-   ozone (O3)
-   nitrogen dioxide (NO2)
-   sulfur dioxide (SO2).

| Substance                        | Annual Mean   | 24 Hour Mean     |
|----------------------------------|---------------|------------------|
| PM2.5 (Fine particulate matter)  | 5 μg/m3       | 15 μg/m3         |
| PM10 (Coarse particulate matter) | 15 μg/m3      | 45 μg/m3         |
| NO2                              | 10 μg/m3      | 25 μg/m3         |
| SO2                              | -             | 40 μg/m3         |
| O3 (Ozone)                       |               |                  |
| CO                               |  8 ppm        |  8 ppm - 10mg/m3 |
| VOC                              | 300-500 μg/m3 |                  |
| CO2                              |               | 400 – 2500 ppm   |

Source of the table [6]

Sources for the CO [7], [8]

TO BE ENRICHED FROM INFORMATION FROM OTHER PARTNERS AND MORE PAPER SOURCES

*IF WE NEED TO PROVIDE THEM*

# Sensor Technologies

### Sensors (by working principle)

The working principles of the sensors are the following :

-   **MOX**

    MOX sensors (metal oxide sensors) are sensors that are used to measure the concentration of certain gases in the air. They work by using a metal oxide semiconductor material that changes resistance when it comes into contact with certain gases. The change in resistance can then be measured and used to calculate the concentration of the gas. MOX sensors have several advantages over other types of gas sensors. They are relatively inexpensive, easy to manufacture, and have a long lifespan. They are also resistant to interference from other gases and can operate over a wide range of temperatures. However, they can be sensitive to humidity and may require temperature compensation in order to maintain accuracy.

    Some common MOX sensors are

-   CCS811
-   ENS160
-   CCS811

    ![](media/014495348d23ceac5d1cc798254a569d.jpeg) ![](media/4647b13002a416ce3b1ddd1af705f1b7.jpeg) ![](media/44f4f4c79becc67213777616b6d30131.jpeg)

    Digital MOX (metal oxide) sensors are sensors that use a metal oxide semiconductor material to measure the concentration of certain gases in the air and output a digital signal. These sensors work by using a microcontroller to interpret the analog output of the sensor and convert it into a digital signal.

    Digital MOX sensors have several advantages over analog MOX sensors. They are more accurate and precise, as they are not affected by noise or other interference in the analog signal. They are also easier to interface with other electronic devices, as they can output a digital signal that can be easily read by a microcontroller or computer.

    Biggest manufacturers of MOX sensors are :

-   AlphaSense
-   SGX Sensortech
-   Honeywell (US)
-   ScioScience
-   Sensirion
-   **MEMS**

    MEMS (microelectromechanical systems) sensors are tiny sensors that are made using microfabrication techniques. They are typically less than a millimeter in size and are used to measure a variety of physical quantities such as acceleration, pressure, temperature, and humidity.

    There are many different types of MEMS sensors, including accelerometers, gyroscopes, pressure sensors, and temperature sensors. These sensors are often used in devices such as smartphones, tablets, and wearable devices to detect movement and orientation, measure pressure and temperature, and provide other types of sensor data.

    Some common MEMS sensors are :

-   BME680
-   LSM303AGR
-   LIS3DH

    ![](media/776f7df6cc04665f5365bc2422ab6758.jpeg) ![](media/5388687a36a453e771af306051f2630f.jpeg) ![Angled shot of a Adafruit LSM303AGR Accelerometer Magnetometer.](media/6b6ef3e961687bb4f5710c8bacc5b56b.jpeg)

    Biggest manufacturers of MEMS sensors are :

-   ST Microelectronics
-   Bosch Sensortec
-   Analog Devices
-   InveSense
-   Sensirion
-   **MOX vs MEMS**

    The main difference between MOX sensors and MEMS sensors is the type of quantity they are used to measure. MOX sensors are used to measure gases, while MEMS sensors are used to measure physical quantities such as acceleration, pressure, and temperature.

    MEMS sensors are a combination of MOX sensor techniques and MEMS techniques.

    Source : [https://www.fierceelectronics.com/components/metal-oxide-gas-sensing-material-and-mems-process\#:\~:text=MOS%20sensors%20detect%20concentration%20of,of%20the%20metal%20oxide%20material.](https://www.fierceelectronics.com/components/metal-oxide-gas-sensing-material-and-mems-process#:~:text=MOS%20sensors%20detect%20concentration%20of,of%20the%20metal%20oxide%20material.)

-   **Light** **Scattering**

    Light scattering sensors are sensors that use light scattering to measure the concentration of particles in a sample. These sensors work by shining a light source on the sample and measuring the amount of light that is scattered by the particles. The amount of light scattered is directly proportional to the concentration of particles in the sample.

    Light scattering sensors are commonly used in applications such as air quality monitoring, water quality monitoring, and industrial process control. They are often used to measure the concentration of particles such as dust, smoke, and pollen.

    There are several different types of light scattering sensors, including Mie scattering sensors and nephelometric sensors. Mie scattering sensors measure the scattering of light by particles that are larger than the wavelength of light, while nephelometric sensors measure the scattering of light by particles that are smaller than the wavelength of light.

    Light scattering sensors have several advantages over other types of particle sensors. They are non-invasive, do not require contact with the sample, and are able to measure a wide range of particle sizes. However, they may not be as accurate as other types of particle sensors and can be affected by factors such as humidity and temperature.

    ![Overview \| PM2.5 Air Quality Sensor \| Adafruit Learning System](media/f71245cb8b7235adb1fcff31a2b32419.jpeg)

-   **NDIR**

    NDIR (non-dispersive infrared) sensors are sensors that use infrared (IR) light to measure the concentration of certain gases in a sample. These sensors work by shining an IR light source on the sample and measuring the amount of light absorbed by the gas molecules. The amount of light absorbed is directly proportional to the concentration of the gas in the sample.

    NDIR sensors are commonly used to measure gases such as carbon dioxide (CO2), methane (CH4), and water vapor (H2O). They are often used in applications such as air quality monitoring, greenhouse gas monitoring, and industrial process control.

    NDIR sensors have several advantages over other types of gas sensors. They are highly accurate, have a long lifespan, and are able to measure a wide range of gas concentrations. However, they may be more expensive and may require regular calibration in order to maintain accuracy.

    ![Adafruit SCD-30 - NDIR CO2 Temperature and Humidity Sensor with tan STEMMA QT connectors next to a 6-pin header. ](media/54289e9bd30f1357b820ab11ef7445ac.jpeg)

-   **Light Scattering vs NDIR**

    NDIR sensors are used to measure gases, while light scattering sensors are used to measure particles.

    NDIR sensors use infrared (IR) light to measure the concentration of certain gases in a sample. The amount of light absorbed is directly proportional to the concentration of the gas in the sample.

    Light scattering sensors, on the other hand, use light scattering to measure the concentration of particles in a sample. The amount of light scattered is directly proportional to the concentration of particles in the sample.

-   **Electro** **Chemical**

    Electrochemical sensors are sensors that use an electrochemical reaction to measure the concentration of certain substances in a sample. These sensors work by applying a voltage to an electrode and measuring the current that flows through the electrode as a result of the electrochemical reaction. The current is directly proportional to the concentration of the substance being measured.

    Electrochemical sensors are commonly used to measure substances such as oxygen, hydrogen, and carbon monoxide. They are often used in applications such as air quality monitoring, water quality monitoring, and medical diagnostics.

    Electrochemical sensors have several advantages over other types of sensors. They are highly sensitive, have a fast response time, and are able to measure a wide range of concentrations. However, they may be prone to drift over time and may require regular calibration in order to maintain accuracy.

    ![](media/1b6ce82c18113c78fe574eae7c205a52.jpeg) ![9. 9.](media/c4488f4c379f14f8075c34cd55047e82.jpeg)

-   **PID   
    **

    PID (photoionization detector) sensors are sensors that use ultraviolet (UV) light to measure the concentration of certain gases in a sample. These sensors work by shining a UV light source on the sample and measuring the amount of light absorbed by the gas molecules. The amount of light absorbed is directly proportional to the concentration of the gas in the sample.

    PID sensors are commonly used to measure gases such as volatile organic compounds (VOCs), which are found in a variety of industrial and environmental applications. They are often used in air quality monitoring, hazardous materials detection, and industrial process control.

    PID sensors have several advantages over other types of gas sensors. They are highly sensitive, have a fast response time, and are able to measure a wide range of gas concentrations. However, they may be affected by the presence of other gases and may require regular calibration in order to maintain accuracy.

    ![](media/4add95e4450b33d0b4c0f0716395ec3d.jpeg)

### Sensor Selection Parameters

The parameters that are taken into account when considering the measurement capabilities of the chosen sensors are the following :

-   Sensitivity
-   Size
-   Power Consumption
-   Gas Selectivity

### Sensing Problems

Sensors can produce problems while measuring. The most common are :

-   **Drift**

    Sensor drift is a phenomenon that occurs when the output of a sensor changes over time, even when the quantity being measured remains constant. This can result in errors in the sensor readings and can affect the accuracy and reliability of the sensor.

    There are several reasons why sensor drift can occur. It can be caused by changes in the physical properties of the sensor, such as changes in temperature or humidity, or by changes in the chemical properties of the sensor, such as corrosion or contamination. Sensor drift can also be caused by electrical or mechanical issues, such as changes in the power supply or wear and tear on the sensor components.

    To minimize sensor drift, it is important to use sensors that are designed to be stable and accurate over time, and to properly maintain and calibrate the sensors according to the manufacturer's recommendations. In some cases, it may be necessary to regularly recalibrate the sensors to ensure that they are providing accurate readings.

-   **Cross Sensitivity**

    Sensor cross sensitivity is the phenomenon in which a sensor responds to more than one type of stimulus. For example, a gas sensor may be sensitive to more than one type of gas, or a temperature sensor may be sensitive to changes in humidity as well as temperature.

    Cross sensitivity can affect the accuracy and reliability of a sensor, as it may produce inaccurate readings if the sensor is exposed to stimuli other than the one it was designed to measure. For example, a gas sensor that is sensitive to multiple gases may produce inaccurate readings if it is exposed to a mixture of gases rather than a single gas.

    To minimize cross sensitivity, it is important to use sensors that are designed to be specific to the stimulus they are intended to measure. In some cases, it may be necessary to use multiple sensors or to use sensors in combination with other types of measurement equipment in order to accurately measure the desired quantity.

    ![](media/d1f42df6fb7fc9dc95d2c1e5e3fb91b9.png)

-   **Humidity & Temperature**

    The effect of humidity & temperature on a sensor's readings depends on the specific type of sensor and the specific application. In general, humidity & temperature can affect the accuracy and reliability of a sensor in several ways:

    Humidity & temperature can affect the physical properties of a sensor, such as the electrical resistance, which can result in changes in the sensor's output.

    Humidity & temperature can cause corrosion or other types of damage to the sensor, which can affect its accuracy and lifespan.

    Humidity & temperature can affect the transmission of electromagnetic waves, such as light or radio waves, which can affect the accuracy of sensors that use these waves to measure quantities.

    Humidity & temperature can affect the concentration of gases in the air, which can affect the accuracy of gas sensors.

    To minimize the effect of humidity & temperature on a sensor's readings, it is important to use sensors that are designed to be resistant to humidity & temperature and to properly maintain and calibrate the sensors according to the manufacturer's recommendations. In some cases, it may be necessary to use humidity & temperature compensation techniques to adjust for the effects of humidity & temperature on the sensor's readings.

-   **Aging**

    Sensor aging is the phenomenon in which a sensor's accuracy and reliability degrade over time. This can be caused by a variety of factors, including physical wear and tear on the sensor components, changes in the physical and chemical properties of the sensor, and exposure to environmental factors such as temperature, humidity, and contamination.

    Sensor aging can affect the accuracy and reliability of the sensor readings, and it can result in errors in the measurement of the quantity being measured. To minimize the effects of sensor aging, it is important to use sensors that are designed to be stable and accurate over time, and to properly maintain and calibrate the sensors according to the manufacturer's recommendations. In some cases, it may be necessary to regularly recalibrate the sensors or to replace them when they reach the end of their useful lifespan.

# Data Acquisition & Broadcast

In this section the method of measuring the gases and the technique of sending the data to the server are discussed.

### Measurements

List :

-   **Location**

    After research, the conclusion is that there is no ability to perform human location in indoor spaces especially when in non-line-of-sight conditions. Therefore, alternatives need to be discussed, such as survey completion, active monitoring with mobile apps, etc.

-   **Activity**

    The need of activity logging to be correlated with the personal exposure levels has not been discussed yet.

    If needed, a possible solution is to be log the activity status with the location status, something that can be done actively by the user with a mobile phone for example.

-   **Metrics ( μg, mg, volume ) Pilots?**

    The unit of measurement of each parameter needs to be specified. Different sensors measure in either PPM ( parts per million ) or in μg/m3 . The conversion between the two can be performed, but it is good practice that one unit is used by everyone.

    Source : [https://cfpub.epa.gov/ncer_abstracts/index.cfm/fuseaction/display.files/fileid/14285\#:\~:text=as%20grams%20per%201%2C000%20liters,mg%2FL%20%3D%201%20ppm](https://cfpub.epa.gov/ncer_abstracts/index.cfm/fuseaction/display.files/fileid/14285#:~:text=as%20grams%20per%201%2C000%20liters,mg%2FL%20%3D%201%20ppm).

-   **Frequency / Sampling Rate**

    We can base the method of sampling based on bibliography. But if there are specific needs based on the particular project, then this needs to be addressed.

    For example, bibliography suggest that for particulate matter measurements, it is good to measure each minute and then aggregate that to a 5 minute average. *(numbers may differ)*

    Different gases probably will need different periods.

-   **Missed readings management**

### Data Broadcast

List :

-   Sum of readings
-   Packets of x minutes
-   Timestamps
-   Message Information and type (JSON)
-   Method (MQTT,HTTP, cloud, Bluetooth, Wi-Fi)

**Here, the knowledge and ideas from the previous project that the lab participated are going to be utilized.**

**Need to note the above characteristics once they become of importance.**

# Power Management

The ideas of reducing the power requirements of the sensors and the management of the battery resources

-   **Sampling Rate**

    Here, there are two parameters that need to be investigated. The first is the oversampling rate, meaning the actual rate that the sensor is aggregating the measurements. The second is the sampling rate that will be demanded by the sensor.

    Each sensor has different current specifications and needs to be analyzed separately. Also, it is not yet clear if all the sensors have oversampling capabilities.

    Explanation : <https://www.phidgets.com/docs/Oversampling>

-   **Broadcast Rate**

    The broadcast rate of the data is a very important parameter. Since LoRaWAN has been selected as the preferred method of communication protocol, the broadcast techniques of it need to be analyzed.

    ![IoTECH Telecommunications \| LoRaWAN™ Network Provider \| LoRaWAN LPWAN  connectivity in Greece \| Internet of things \| Smart cities \| IoT  connectivity](media/0846d22c5dab2764c2b57c509b24d778.png)

-   **Solar Cell**

    At the moment, the use of a solar cell on top of the wearable device is been tested, to extend the battery life of the device and also extend the possibilities of sensor integration.

-   **Number of Sensors**

    The number of sensors on the wearable device is yet to be finalized. The current decision is to have the ENS160 for measuring VOC & eCO2, MiCS6814 or GM102 or GM702 for measuring CO & NO2.

    The sensors need to be tested for accuracy, repeatability in ambient conditions and current consumption and then they will be integrated on the wearable device.

# Sensor Testing

### MCU

The microcontroller being used for the testing is an ESP8266 HUZZAH Feather by Adafruit.

![](media/a52e25cf0f06d94721a8ab0ded4fc73b.png)

### Cloud Platform

For the time being, the Thingspeak platform is used. This platform is used until the setting up of all the sensors and the measurement techniques is finished. After that, other options for storing and visualizing the data will be researched.

![Blog Search Result:](media/99ecf05f26fbfce5743b35a351e5f6e5.png)

![](media/87f5aaad943b49eefcda5708222c0b44.png)

For Local hosting :

-   Node Red (connectivity)
-   InfluxDB (storage)
-   Grafana (visualization)

For cloud hosting :

-   Firebase
-   InfluxDB cloud

### BME 680

The BME 680 is a MEMS sensor manufactured by Bosch Sensortec.

We are using the BME680 Breakout Platform from Adafruit.

![](media/161e95fe79bbda1cbc944df5260554bd.png)

##### Pollutants

-   Temperature

    After cross referencing with ambient thermometers in the house, the readings seem to be consistent and accurate.

-   Humidity
-   Pressure\*

    Even after the break in period of the sensor, the measurements are off. Maybe, calibration is needed.

-   VOC\*

    There is no VOC measurement provided, only a resistance. Need to check further how to infer VOC concentration and not only an Air Quality index that can be calculated from the Bosch Sensortec Library (that has not been yet tested).

##### Sensor Specifics

-   **Oversampling**

    Oversampling refers to the process of taking multiple measurements of the same quantity and combining them in order to improve the accuracy and resolution of the measurement. In the context of sensors, oversampling is often used to improve the accuracy of measurements made by sensors that have a limited resolution or that are affected by noise or other sources of error.

    For example, a temperature sensor that has a resolution of 0.1 degree C may not be accurate enough to measure small temperature changes or to provide a detailed temperature profile. By oversampling the sensor and taking multiple measurements, it is possible to improve the accuracy and resolution of the measurement. The multiple measurements can be combined using techniques such as averaging or filtering in order to reduce the impact of noise or other sources of error on the final measurement.

    Oversampling can be useful in a variety of applications, including weather forecasting, industrial process control, and scientific research. It is important to carefully consider the trade-offs between the improved accuracy and resolution provided by oversampling and the additional time and resources required to take multiple measurements.

    The measurements at the moment are taken with oversampling rates of :

| **Temperature oversampling rate** | **Pressure oversampling rate** | **Humidity oversampling rate** | **Current consumption** | **Measurement period** |
|-----------------------------------|--------------------------------|--------------------------------|-------------------------|------------------------|
| x8                                | x4                             | x2                             | 3.3 mA                  | 420 ms                 |

-   **Heating Procedure**

    Heating the gas sensor hot plate to a target temperature (typically between 200 °C and 400 °C) and keep that temperature for a certain duration of time. *Source : Datasheet 3.3.5*

##### Software

At the moment, the library provided by Adafruit (*\<Adafruit_BME680.h\>*) is used for testing.

### MiCS 6814

Info

![](media/f8fe226498d465986010cd5fc1a9899f.png)

### ENS160

Info

![](media/4d51c97771536efe8910bb78120d6a89.png)

### Grove Multichannel v2

Info

![](media/d8e737b8aef735bc84381c1f8a6e52c8.png)

# Actions Ahead

List :

-   Find metrics of measurement from pilots
-   Range metrics of measurement from pilots
-   Sensitivity
-   Drift
-   Calibration Meaning and Capability ( how to calibrate when wearable is going through many different environments , not the same as stationary ?)
-   Aging
-   Selectivity

    Create a timeline for addressing the above actions..

### Localization

There are several factors to consider when choosing a method for indoor localization using wearable devices based on the ESP32, including the required accuracy, the cost of the system, and the available resources (e.g., hardware, software, and infrastructure). Some common methods that can be used for indoor localization with the ESP32 include:

**Radio frequency (RF) signal strength**: This method uses the strength of the RF signal from a wireless access point (WAP) or other transmitter to determine the location of a device. The ESP32 can be equipped with an RF antenna and programmed to measure the signal strength of nearby WAPs. This method is relatively low-cost and easy to implement, but it may not provide the highest accuracy.

**Bluetooth beacon triangulation:** This method uses the signal strength and timing of Bluetooth beacons to determine the location of a device. The ESP32 can be equipped with a Bluetooth antenna and programmed to scan for nearby beacons. This method can provide good accuracy, but it requires the deployment of multiple beacons and may be more expensive than the RF signal strength method.

**Wi-Fi fingerprinting:** This method involves creating a map of the wireless signal strength and other characteristics of the Wi-Fi environment, and using this map to determine the location of a device based on the current signal characteristics.

**NFC** : it is possible to use near field communication (NFC) for indoor localization. NFC is a wireless communication technology that allows devices to exchange data over short distances (typically less than 4 inches). It is commonly used in mobile phones and other devices for applications such as contactless payments and access control.

To use NFC for indoor localization, you can equip your devices with NFC tags or NFC readers and program them to exchange location data when they are brought into close proximity. For example, an NFC-enabled device could read the location data stored on an NFC tag attached to a wall or other surface, or it could exchange location data with another NFC-enabled device.

There are several factors to consider when using NFC for indoor localization, including the accuracy of the location data, the cost and complexity of the system, and the availability of NFC tags or readers.

**Ultrasonic** **ranging**: This method uses ultrasonic waves to determine the distance between a device and a fixed reference point. By measuring the distance to multiple reference points, it is possible to determine the location of the device using trilateration.

**Visual** **odometry**: This method uses computer vision techniques to analyze the movement of a device based on the visual information it receives. It can be used to determine the location of the device by comparing the current visual information to a map of the environment.

**Magnetic** **field** **mapping**: This method uses the Earth's magnetic field to determine the location of a device. It requires a map of the magnetic field strength and direction at different locations in the environment, and can be used to determine the location of the device by comparing the current magnetic field measurements to the map.

**RFID**: This method uses radio frequency identification (RFID) tags and readers to determine the location of a device. RFID tags can be attached to devices or people, and RFID readers can be placed throughout the environment to detect the presence of the tags.

**GPS**: Global positioning system (GPS) is a satellite-based navigation system that can be used to determine the location of a device outdoors. GPS signals may not be reliable indoors, but there are techniques (e.g., assisted GPS, indoor GPS) that can be used to improve the accuracy of GPS-based indoor localization.

**User surveys** can be a useful method for collecting data about the location of individuals or devices. For example, you could ask users to provide their current location as part of a survey, or you could use a survey to gather data about the locations that people visit or the devices they use.

However, user surveys are not typically used as a primary method for indoor localization, as they rely on self-reported data that may not be accurate or reliable. Surveys can be a useful supplement to other methods of indoor localization, but they should not be relied upon as the sole source of location data.

Power Requirements

The power requirements for indoor localization methods can vary significantly depending on the specific technique and the hardware and software used to implement it. Some methods, such as user surveys and NFC, may have relatively low power requirements because they rely on simple hardware and do not require continuous operation. Other methods, such as Wi-Fi fingerprinting and SLAM, may have higher power requirements because they involve more complex hardware and software and may require continuous operation.

In general, methods that use passive sensors (e.g., RFID, NFC) tend to have lower power requirements than methods that use active sensors (e.g., ultrasonic ranging, GPS). Similarly, methods that rely on external reference points (e.g., Wi-Fi access points, Bluetooth beacons) may have lower power requirements than methods that use self-contained sensors (e.g., inertial measurement units, computer vision systems).

It is difficult to identify a single "lowest power" solution for indoor localization, as the power requirements will depend on the specific requirements and constraints of the application.

##### Lorawan

It is possible to use LoRaWAN for indoor localization. LoRaWAN is a wireless communication technology that is designed for long-range, low-power, and low-bandwidth applications. It is commonly used in Internet of Things (IoT) systems to connect sensors and other devices to the internet.

To use LoRaWAN for indoor localization, you can equip your wearable devices with LoRaWAN radios and program them to transmit their location data to a LoRaWAN gateway or network server. The gateway or server can then use this data to determine the location of the devices.

There are several methods that can be used to determine the location of a device using LoRaWAN, including:

**Time of arrival (TOA):** This method uses the time it takes for a signal to travel from the device to the gateway to determine the distance between them. By measuring the distance to multiple gateways, it is possible to determine the location of the device using trilateration.

**Time difference of arrival (TDOA):** This method uses the difference in the time it takes for a signal to travel from the device to multiple gateways to determine the location of the device.

**Angle of arrival (AOA):** This method uses the angle at which a signal arrives at the gateway to determine the location of the device.

Paper sources for LoRaWAN

<https://www.mdpi.com/2078-2489/13/6/303>

<https://sci-hub.mksa.top/10.1109/COMST.2019.2911558>

[https://www.hindawi.com/journals/js/2018/3715372/\#conclusion](https://www.hindawi.com/journals/js/2018/3715372/#conclusion)

<https://ieeexplore.ieee.org/document/9834216>

https://blaauw.engin.umich.edu/wp-content/uploads/sites/342/2019/12/RF-Echo-A-Non-Line-of-Sight-Indoor-Localization-System-Using-a-Low-Power-Active-RF-Reflector-ASIC-Tag.pdf

# References

[1] <https://www.epa.gov/outdoor-air-quality-data/about-air-data-reports>

[2] <https://www.euro.who.int/__data/assets/pdf_file/0009/128169/e94535.pdf>

[3] [https://www.health.act.gov.au/about-our-health-system/population-health/environmental-monitoring/air-quality/measuring-air\#:\~:text=Calculating%20the%20AQI,the%20AQI%20for%20the%20pollutant](https://www.health.act.gov.au/about-our-health-system/population-health/environmental-monitoring/air-quality/measuring-air#:~:text=Calculating%20the%20AQI,the%20AQI%20for%20the%20pollutant).

[4] <https://www.eea.europa.eu/themes/air/air-pollution-sources-1>

[5] <https://www.sciencedirect.com/science/article/pii/S0160412018309966>

[6] <https://www.who.int/news-room/fact-sheets/detail/ambient-(outdoor)-air-quality-and-health>

[7] <https://www.osha.gov/sites/default/files/publications/carbonmonoxide-factsheet.pdf>

[8] [https://gaslab.com/blogs/articles/carbon-monoxide-levels-chart\#:\~:text=The%20WHO%20recommended%20limits%20are,no%20more%20than%2015%20minutes](https://gaslab.com/blogs/articles/carbon-monoxide-levels-chart#:~:text=The%20WHO%20recommended%20limits%20are,no%20more%20than%2015%20minutes)
