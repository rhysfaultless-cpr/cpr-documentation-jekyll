---
title: Boxer
parent: Robots
has_children: false
nav_order: 1
---

# Boxer

<center>
  <img src="{{ site.url }}{{ site.baseurl }}//assets/images/robot_boxer_1.png" width="400"/>
</center>


---
## Introduction

Boxer is a large indoor robotic platform for prototyping and development of industrial and research applications. 
Adapted from the OTTO Motors _OTTO 100 V2.4 autonomous mobile robot (AMR)_, 
Boxer is an industrial-grade mobile robot that is programmable and easily extensible with additional hardware.
The following sections provide key information on safety, setup, operation, and maintenance.

### What's included

Contained in your shipment are the following items:

-   Clearpath Robotics Boxer
-   OTTO 100 Manual Charger
-   Handheld Joystick Controller
-   Optional: OTTO 100 Fast Charger

If you elected to purchase standard payload modules or custom integration services with Boxer, 
then additional equipment will be included per your specific configuration, plus further documentation as required.

The back of Boxer has the Human-Machine-Interface panel _(HMI)_.
The HMI has 5 elements: 

1.  ethernet port
2.  power button
3.  E-stop reset button
4.  chargeport
5.  E-stop button

<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_2.png" width="400"/>
</center>

### Hardware overview

Below is an overview of the Boxer robot hardware that outlines the key components that you should be aware of in order to get started with using your robot. 

<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_3.png" width="400"/>
</center>

<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_4.png" width="400"/>
</center>

### Software overview

Your Boxer can be controller through ROS, either through a ROS2 API on the base platform or through a ROS1 API on the optional backpack computer. 
Some key topics that comprise the Boxer’s ROS1 API are listed below. For details on the ROS2 API, please contact our Support department.

| Topic                             | Message Type            | Purpose                                                                          |
| :-------------------------------- | :---------------------- | :------------------------------------------------------------------------------- |
| `/cmd_vel`                        | `geometry_msgs/Twist`   | Input to Boxer’s kinematic controller. Publish here to make Boxer go.            |
| `/odom`                           | `nav_msgs/Odometry`     | Publishes the internal odometry from Boxer’s base platform, a filtered localization estimate based on wheel odometry (encoders), an integrated IMU, a camera, and a laser. |
| `/imu/module0/data`               | `sensor_msgs/IMU`       | Publishes the internal IMU data from Boxer’s base platform.                      |
| `/front/scan`                     | `sensor_msgs/LaserScan` | Publishes the laser scan data from the base platform’s front localization laser. |
| `/rear/scan`                      | `/rear/scan`            | Publishes the laser scan data from the base platform’s rear safety laser.        |
| `/realsense/depth/image_rect_raw` | `sensor_msgs/Image`     | Publishes depth data from the base platform’s camera.                            |

---

## Safety

The Boxer robot contains several features to protect the safety of users and the integrity of the vehicle.

### General warnings

Use of an autonomous robot is inherently dangerous. 
Please take time to locate the red Emergency Stop _(E-stop)_ button on the rear-right of the system. 
When the E-stop button pressed, it provides a secure way to stop the robot movement, but does not control power attached by the attachment panel. 
Ensure the E-stop button is accessible at all times.

When starting out, favor slower wheel speeds. 
Operating at such speeds will allow for more reaction time in the case of unexpected behaviour. 

When the robot is operating, keep clear of the wheels. 

Refer to the [OTTO 100 V2.4 Operation and Maintenance Manual](https://help.ottomotors.com/docs/robots/otto-100-v2-4?preview=/53683025/99909709/OMM-000094-Operation%20and%20Maintenance%20Manual%20OTTO%20100%20V2.4_A.pdf) for further safety precautions when using self-driving vehicles.

---

## System specifications

| Dimensions, Length                 | 740 mm  |
| Dimensions, Width                  | 550 mm  |
| Dimensions, Height                 | 320 mm  |
| Mass                               | 114 kg  |
| Velocity, Max                      | 2.0 m/s |
| Obstacle, Max Step Height          | 6 mm    |
| Obstacle, Floor Gap                | 13 mm   |
| Operating Relative Humidity, Min   | 0 %     |
| Operating Relative Humidity, Max   | 85 %    |
| Operating Temperature, Min         | 20 °C   |
| Operating Temperature, Max         | 30 °C   |
| Storage Temperature, Min           | -20 °C  |
| Storage Temperature, Max           | 35 ° C  |
| Operating Time, Standby            | 8 hours |
| Operating Time, Continuous Driving | 3 hours |

---

## Setup and assembly

### Unboxing

Boxer ships fully assembled and no assembly is required. 
To unbox, remove the screws holding the top wood panel and the front wood panel. 
Remove the screws holding the cross bracing. 
An electric driver should be used to aid in the removal of the screws. 
Lay the top wood panel down with one end on the edge of the crate and the other end on the ground to create a ramp as shown below. 
Pull the robot out of the crate by hand, and then roll the robot down the wood ramp. 

<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_5.png" width="400"/>
</center>

### Powering on

1.  Turn the 2 circuit breakers to the on position. 
    You will need to lift the metal bar to do this. 
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_6.jpg" width="400"/>
    </center>
2.	Press the Power Button.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_7.png" width="400"/>
    </center>
3.  Wait for the system to boot. 
    The Boxer's lights will go through a sequence of colors during this process: 
    - all white for approximately 30 seconds
    - all red for approximately 30 seconds
    - flashing white for less than 5 seconds
    - then flashing red
    The Boxer will be sounding an alarm which will be adjusted during the base unit configuration below. 

### Base unit configuration

Connect the Boxer to the Wi-Fi network using the steps below. 
Refer to [Connecting a Vehicle to Your Network](https://help.ottomotors.com/sw220/commissioning/connecting-a-vehicle-to-your-network) and [Connecting to an OTTO 100](https://help.ottomotors.com/sw220/commissioning/connecting-to-a-vehicle/connecting-to-an-otto-100) for more details.

1.  Configure a network port on your laptop with the IP address <10.255.255.200>.
2.  Connect a network cable from the port on your laptop to the network port on the rear of the Base Unit. 
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_8.png" width="400"/>
    </center>
3.	On your laptop, open a web-browser like Google Chrome, and go to the address <http://10.255.255.1:8090>
4.  Enter the required information to connect to your network. 
    See your IT administrator for proper settings for your network.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_9.png" width="400"/>
    </center>
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_10.png" width="400"/>
    </center>
5.  Take note of the hostname. 
    It will be used in future steps for accessing the robot.
    You can also find this hostname engraved on the HMI panel, at the rear of the Boxer.
6.  Click _Save and Restart Network_.
7.  Power cycle the Boxer.
8.  Using the hostname or static IP set in the Wi-Fi setup above, load the _OTTO App_ user interface by opening a web-browser, and going to the address _http://<hostname>:5000_. 
    (e.g. <http://A31-002124076:5000>) 
    The _OTTO App_ should load, and look similar to the image below.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_11.png" width="400"/>
    </center>
9.  Adjust the volume to an appropriate level for your facility by selecting the _Vehicle_ option from the top-left menu and adjusting the volume as appropriate.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_12.png" width="400"/>
    </center>
10. You have finished onfiguring the Boxer base robot, and it's ready for use.

### Backpack computer configuration

This section outlines how to configure the backpack computer attached to the base Boxer robot. 
You can omit this section if your Boxer is not equipped with a backpack computer.

The backpack computer is an add-on computer that is networked with the base platform's computer, located inside then Boxer.
This backpack computer can be used to integrate peripherals, like sensors and manipulators. 
A ROS bridge automatically runs upon booting the backpack computer, and transmits the base platform computer’s ROS data to the backpack computer.
This ROS bridge allows you to leverage the base robot for your own application. 
The backpack computer uses Netplan as its network configuration tool, and has a static IP address of <192.168.131.1>.

