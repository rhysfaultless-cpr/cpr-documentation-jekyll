---
title: Boxer, User Manual
parent: Boxer
grand_parent: Robots
has_children: false
nav_order: 1
---

# Boxer, User Manual

{% include components/introduction_boxer.md %}

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
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_9.png" width="600"/>
    </center>
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_10.png" width="600"/>
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
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_11.png" width="600"/>
    </center>
9.  Adjust the volume to an appropriate level for your facility by selecting the _Vehicle_ option from the top-left menu and adjusting the volume as appropriate.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_12.png" width="600"/>
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

### Connecting to the backpack computer

You can connect to the backpack computer on Boxer over a wired or Wi-Fi connection. 

To connect to the backpack computer over a wired connection:

1.  Configure a network port on your laptop with the IP address <192.168.131.100>
2.  Connect a network cable from your laptop to an open network port on the backpack computer.
3.	Test the connection between the user computer and backpack computer by opening a terminal and entering: `ping 192.168.131.1 `
4.	From your laptop's terminal, you can access the backpack computer by entering: `ssh administrator@192.168.131.1`

To connect to the backpack computer over a Wi-Fi connection:

1.	Connect your laptop to the same Wi-Fi network as the backpack computer. 
2.	Note the IP address of the backpack computer’s wireless interface by running this command the backpack computer's terminal: `ip a`
3.	To test the connection between your laptop and backpack computer, enter this command in a terminal from your laptop: `ping <wireless_ip_address>` (eg. `ping 192.168.0.11`)
4.	From your laptop's terminal, you can access the backpack computer by entering: `ssh administrator@<wireless_ip_address>` (eg. `ssh administrator@192.168.0.11`) 

### 4.4.2	Connecting the backpack computer to a Wi-Fi network

To connect the backpack computer to a wireless network follow these steps:

1.  Access the backpack computer over an SSH connection. 
    Since the backpack computer is presumably not connected to a Wi-Fi network yet, you will need to access the backpack computer over a wired connection. 
    The previous section details how to connect to the backpack computer over a wired connection.
2.  Once you have accessed the backpack computer, create a netplan configuration by running the following command.
 
        sudo touch /etc/netplan/60-wifi.yaml
 
    This will create a file called _60-wifi.yaml_ inside of the _/etc/netplan/_ directory.
3.	Open _/etc/netplan/60-wifi.yaml_ with your favourite text editor and populate it. 
    Use this example configuration file as reference:

        network:
          wifis:
            # change wlp2s0 to exactly match your wireless interface
            # common values are wlp2s0, wlp3s0, wlan0, etc...
            # if you aren't sure, use the `iwconfig` or `ip a` command
            wlp2s0:
              optional: true
              access-points:
                # replace "my-ssid" with the SSID of your wireless network
                my-ssid:
                  # put your wireless password here
                  password: wifi_password_goes_here
              # DHCP4 should be enabled for most wireless routers
              # alternatively you can use a static IP address.
              # e.g, uncomment the following
              #addresses: [192.168.1.100/24]
              #gateway: 192.168.1.1
              #dhcp4: false
              dhcp4: true
              dhcp4-overrides:
                send-hostname: true

4.  Connect the backpack computer to the wireless network by running the command below. 
    Note that this may take a moment to complete:
		
        sudo netplan apply

5.  To verify that the backpack computer is connected to the wireless network, check that the backpack computer has an IP address assigned to its wireless interface by running:

    		ip a

---

## Operation

This section outlines how to use the basic functions of the Boxer platform in order to get started quickly. 
There are three methods of operating the robot with varying degrees of control. 

### Getting started with the OTTO user interface

This section details how to get the Robot driving around using the OTTO user interface. 

1.  Power on the system.
2.  Ensure that the E-stop is released by pulling out the red button at the rear of the unit, and then pressing the blue Reset button.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_13.jpg" width="200"/>
    </center>
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_14.png" width="200"/>
    </center>
3.	Using the base Boxer's hostname or static IP, open the OTTO App by entering the following in your laptop's web-browser: 

        http://<hostname>:5000
    
4.  You are now ready to start driving your system.

### Driving manually

To drive the robot manually, follow the steps below. 

1.  Power up the robot and connect to the OTTO App at `http://<hostname>:5000`
2.	The first time after power-up, it is necessary to take the system out of neutral by clicking on the joystick icon at the bottom right of the interface.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_15.png" width="600"/>
    </center>
3.  Ensure that the system is in manual mode and use the _thumbstick_ at the bottom right of the interface to drive the robot in the desired direction. 
    Note that the maximum speed can be adjusted using the slider _Tortoise-Hare_ at the bottom of the interface.
    We recommended you begin at slow speeds until you become comfortable with how to control the robot.
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_16.png" width="600"/>
    </center>    

### 5.1.2	Mapping

Prior to navigating autonomously, a map of the facility must be created. 
The details of creating a map are beyond the scope of this document. 
Detailed instructions for mapping can be found here:

-	[OTTO App training](https://otto.talentlms.com/)

### Joystick control

If your Boxer unit is equipped with a backpack computer, the simplest method for controlling the Boxer robot is using the supplied Playstation 4 Bluetooth Controller. 
This controller is already pre-paired to the robot. 
To use the controller: 

1.  Power up the robot and connect to the OTTO App at `http://<hostname>:5000`
2.  The system will boot up into a neutral state. 
    Take the robot out of _Neutral_ by clicking the _Joystick_ icon at the bottom right of the interface.
3.	Press the PS button on the controller to sync with the robot. 
    Once the blue LED on the top of the controller is solid, the Robot is paired and ready to move. 
    Hold the L1 trigger button to engage the deadman switch. 
    Push the left thumbstick in the direction you wish to move the Boxer. 
4.  For full speed mode, hold the R1 trigger. 
    Note that it is recommended that you use full speed mode only when comfortable with the operation of the Boxer. 
    <center>
      <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_17.png" width="600"/>
    </center>     

###	Operation using ROS

As with every Clearpath Robotics Robot, the Boxer can be operated using ROS topics. 
For general ROS tutorials, visit <https://clearpathrobotics.com/assets/guides/noetic/ros/index.html>. 
To quickly get started running your Boxer with ROS follow the instructions below. 

Upon booting the Boxer, ROS will begin running on both the base platform computer and the backpack computer. 
The Boxer can be operated using ROS over its ROS topics, and there are two ways of interfacing with Boxer’s ROS topics: 

1.  SSH into Boxer’s backpack computer, or 
2.  Setting the Boxer’s backpack PC as the ROS Master on a local computer.

You can SSH into the Boxer's backpack computer by connecting a network cable directly between your PC and an open network port on the backpack PC.  
Configure your computer to have a static IP address on the `192.168.131.0/24` subnet, for example `192.168.131.100`>`.  
Once this is done you can log into the robot by running:

    ssh administrator@192.168.131.1

If your laptop is connected to the same Wi-Fi network as the Boxer, you can SSH into the backpack computer using the robot’s IP address on the Wi-Fi network (e.g. `192.168.1.11`)
You may need to SSH over a wired connection and use the `ip a` command to determine what Wi-Fi address has been assigned to the backpack computer.

	  ssh administrator@<computer ip>

The ROS topics on Boxer can be seen by running:

	  rostopic list

Data from sensors such as the camera, internal IMU, front laser, and rear laser can be seen with:

  	rostopic echo /realsense/depth/image_rect_raw
	  rostopic echo /imu/module0/data
	  rostopic echo /front/scan
	  rostopic echo /rear/scan

Boxer can be driven using its kinematic controller by publishing drive commands to the `/cmd_vel` ROS topic. 
For example, to drive Boxer forward slowly:

	  rostopic pub /cmd_vel geometry_msgs/Twist "linear:
  	  	x: 0.1
  	  	y: 0.0
  	  	z: 0.0
    angular:
  	  	x: 0.0
  		  y: 0.0
  		  z: 0.0" 

Boxer can be visualized and controlled through rviz. 
On you laptop, set the Boxer’s backpack computer as the ROS Master, and run the following command to view Boxer in rviz. 

    roslaunch boxer_viz view_robot.launch

Rviz allows you to interactively drive Boxer around.
Note that the Boxer-specific packages must be installed and sourced on your laptop before to running the command, otherwise, Boxer will not load correctly in rviz.

To restart ROS without having to reboot the Boxer:

  	sudo systemctl restart ros
	  sudo systemctl restart ros-bridge

---

## Payload integration guide

If you would like to attach custom hardware to the Boxer, you will have to make modifications for mechanical mounting, electrical supply, and software integration. 
This section aims to help you with respect to these tasks.

### Mechanical Mounting

External payloads can be attached to the mounting plate of the Boxer by using the predrilled Ø4.2 mm thru holes, using the Ø8 mm countersunk through holes on the underside, or adding new holes. 
Whichever method you choose, the method for removing the top plate is the same and outlined below. 

1.	Ensure the Robot is shut off, and the curcuit breaker is turned to the _off_ position.
2.	Disconnect and remove all existing payloads on the top plate. 
3.	Using a 2 mm hex key, remove the twelve M3 round head screws holding the connection covers in place. 
    Remove the panels. 
    Take care to disconnect the network cable and attachment cable from the robot when removing the connection covers. 
4.	Using a 4 mm hex key, remove the eleven M5 socket head screws holding the plate down. 
5.	Remove the plate from the Boxer. 

The Boxer plate is made from 8 mm aluminum and can be easily machined according to your customization needs.
There are 19 premade Ø4.3 mm holes that can be used for mounting payloads to the Boxer. 
<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_18.png" width="600"/>
</center>     

The plate also has eight Ø8 mm holes in the corners which are countersunk from the underside of the plate, making them ideal for flathead screws installed to protrude from the plate. 
<center>
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/robot_boxer_19.png" width="600"/>
</center> 

### 6.2	Electrical Integration

For connecting with any external payloads, such as a backpack computer, refer to the product’s datasheet or manual. 
If your robot was equipped with these payloads by Clearpath Robotics this documentation is provided along with your Boxer. 
Contact our Support team if you need more information.

Ensure that the Boxer is shut off and the circuit breaker is turned to the _off_ position before performing any electrical work on the Boxer. 

The Boxer is equipped with an attachment interface that consists of a Power-over-Ethernet (PoE) RJ45 bulkhead connector, a USB Type-A bulkhead connector, and a 37-Position panel receptacle and mated plug. 
To connect with the Boxer attachment interface see Section 10 of the [OTTO 100 V2.4 Operation and Maintenance Manual](https://help.ottomotors.com/docs/files/53683025/99909709/1/1606232510624/OMM-000094-Operation+and+Maintenance+Manual+OTTO+100+V2.4_A.pdf). 

To add wires to the 37-Position connector for you application, follow the TE Connectivity documentation for [connector 206305-1](https://www.te.com/usa-en/product-206305-1.html) to use appropriate crimp pins. 
Note that the 37-Position connector will come pre-populated from Clearpath Robotics with 2 wires.
These 2 wires complete the base Boxer's E-stop loop, allowing the robot to move. 
Other positions of the connector may be pre-populated, well as the PoE and USB, if your robot was equipped with payloads according to your Clearpath Robotics customizations. 

{% include components/software_integration_ros_sensors.md %}

---

## Maintenance

The Boxer is built for rugged, long-term use. 
Here are some steps that can be taken to maintain and extend the life of Boxer further. 

### Battery care

To help extend the life of the batteries, follow the steps below. 

- Do not discharge the batteries lower than 10%. Batteries lower than 5% are permanently damaged and cannot be recharged.
- Recharge batteries to 100% after every use.
- Recharge batteries and turn the circuit breaker to ”OFF” before putting the system into long-term storage.
- Batteries that are in long-term storage will need to be recharged every 6 months.
- Charge batteries when the ambient temperature is between 20°C to 30°C. Consult Clearpath Robotics if you need to charge batteries outside these conditions.

### Battery charging

The system can be charged using an [OTTO 100 Manual Charger](https://help.ottomotors.com/docs/chargers/otto-100-manual-charger) or an [OTTO 100 Fast Charger](https://help.ottomotors.com/docs/chargers/otto-100-fast-charger). 
Details for use and installation are provided in the linked User Manuals.

Only use the OTTO 100 Manual Charger or OTTO 100 Fast Charger provided with your Boxer. 
Use of other chargers may cause damage or injury.

---

{% include components/support.md %}
