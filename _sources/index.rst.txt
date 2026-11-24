Using ADIS IMUs in ROS 2
========================

Analog Devices ADIS series IMUs can be used in ROS 2 applications using the ``adi_imu`` package. In brief, the communication stack for this looks like:

.. mermaid::

   flowchart LR
      imu[ADIS IMU] -- SPI --> linux[Linux driver<br>iio/imu/adis*] -- iio API --> libiio -- local:<br>or ip: --> ros[ROS 2 node<br>adi_imu] --> topic[ROS 2 topic<br>/imu]

The ``kuiper-adis`` and ``ros-sdk`` manifests can be used to prepare and run ROS 2 IMU data acquisition and visualization:

* ``kuiper-adis`` sets up a Raspberry Pi 4 or 5 to communicate with an ADIS series IMU
* ``ros-sdk`` sets up a batteries-included ROS 2 runtime with ADI ROS 2 packages, which can be run on either the Raspberry Pi directly, or on a separate machine.

The following instructions will set opinionated configurations for both of the two, as a starting point for learning and demonstration.

Step by step instructions
-------------------------

.. toctree::
   :caption: Step by step instructions
   :titlesonly:
   :numbered:

   hardware-setup
   linux-setup
   ros-setup
   ros-acquisition
   ros-visualization

Reference
---------

For a detailed reference of all available configuration options and functionalities of the two used targets, see:

.. toctree::
   :caption: Target reference

   kuiper-adis
   ros-sdk
