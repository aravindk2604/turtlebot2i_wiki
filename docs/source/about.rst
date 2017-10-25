.. _chapter_about:

About
=====
This documentation describes the setup of Trossen Robotics' TurtleBot2i with ROS.
It was tested on ``Ubuntu 16.04`` and ``ROS Kinetic``.
The content is adapted from the original documentation from Trossen Robotics.

You can find the official documentation `here <https://github.com/Interbotix/turtlebot2i/wiki/01:-Getting-Started>`_.

TurtleBot 2i the Mobile Research Robot - a modular ROS-based robotics platform.

The 2i improves upon previous iterations of the TurtleBot with a completely redesigned modular chassis and for the first time, native support of robotic arms. The TurtleBot 2i offers the Pincher MK3 4 DOF Robotic Arm as a fully supported standard option allowing the robot to interact with small objects in the real world, effectively transforming the TurtleBot into an extremely capable mobile manipulator.

This new version is also accompanied by hands on tutorials and demos that showcase the robot's capabilities - enabling students, educators, researchers and developers to hit the ground running with a versatile open source ROS development platform.

Our goal is to bring previously daunting technologies and fields of study such as autonomous navigation and robotic manipulation into the hands of innovators and developers in a much more approachable format.

The demos and tutorials created for the 2i provide a hands-on tools for demonstrating how robots perceive and interact in the real world, focusing on real-world autonomous mobile robotics, automation technologies and object/environment manipulation. 

TurtleBot 2i ROS Software/Demo Features
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Autonomous Navigation & Point Cloud Mapping
- Map Zone Identification & Waypoints
- Robotic Arm Object Manipulation & Sorting
- Obstacle Avoidance & Path Planning
- Teleoperation Examples
- Self-Charging w/ Dock

.. raw:: html

  <iframe src="https://www.youtube.com/embed/xzSNXq6xNjs" style="border: 0; height: 345px; width: 560px"></iframe>


Use Cases
~~~~~~~~~

**Autonomous Sorting**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/6mtsNkpCuIU" style="border: 0; height: 345px; width: 560px"></iframe>


**Map Zone Identification and Waypoints**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/tucON6jPqU4" style="border: 0; height: 345px; width: 560px"></iframe>


**Path Planning**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/tYPvYLXrcdY" style="border: 0; height: 345px; width: 560px"></iframe>


**Obstacle Avoidance**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/aMU2Lw8khZw" style="border: 0; height: 345px; width: 560px"></iframe>


**Autonomous Navigation**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/rJ3ITsHJoW4" style="border: 0; height: 345px; width: 560px"></iframe>


**RVIZ Direct Manipulation of ARM**

.. raw:: html

  <iframe src="https://www.youtube.com/embed/wT0BMt0Uh8k" style="border: 0; height: 345px; width: 560px"></iframe>


Technical features
~~~~~~~~~~~~~~~~~~

The TurtleBot 2i is powered by an Intel NUC BOXNUC6CAYH and features dual 3D camera configurations, using a dedicated long range Orbbec Astra for Navigation & Mapping, and the short range Intel RealSense camera SR300-Series as a dedicated Manipulation work space sensor.

The TurtleBot 2i offers the Pincher MK3 Robotic Arm as a fully supported standard, allowing the robot to interact with small objects, buttons, and tools in the real world. The Arbotix-M Robocontroller provides an interface for the Pincher Mk3 arm, which is implemented using MoveIt, an open source inverse kinematics solution, allowing users to control the arm using only high-level commands.

Hardware Specifications
***********************

CPU
~~~

- INTEL NUC - BOXNUC6CAYH
- 8GB Ram
- 120GB or better SSD
- 802.11AC WiFi / Bluetooth 4.0
- Ubuntu 16.04 / ROS Kinetic

Sensors
~~~~~~~

- Intel RealSense 3D Camera SR300-Series
- Orbbec Astra Cam
- Accelerometer/Gyro/Compass
- Edge Detection & Bumper Sensors

Mobile Robot
~~~~~~~~~~~~

- Kobuki Mobile Base
- Modular & Interchangeable Decks
- Pincher MK3 Robo Arm
- Arbotix-M Robocontroller
- Maximum translational velocity: 70 cm/s 13
- Maximum rotational velocity: 180 deg/s (>110 deg/s gyro performance will degrade)
- Payload: 2kg (without arm), 1kg (with arm)
- Cliff: will not drive off a cliff with a depth greater than 5cm
- Threshold Climbing: climbs thresholds of 12 mm or lower
- Rug Climbing: climbs rugs of 12 mm or lower
- Expected Operating Time: 4-6 hours (operating time varies depending on loadout)
- Expected Charging Time: 2-3 hours (charge time varies depending on loadout)
- Docking/Charging Station: automatic within a 2mx5m area in front of the docking station


