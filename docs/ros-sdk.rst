ros-sdk target
==============

The ``ros-sdk`` cim target builds a Docker container for ROS 2 development, containing 

Configuration options:

.. list-table::
    :header-rows: 1

    - * Variable
      * Value
      * Description

    - * ``ROS_DISTRO``
      * one of ``humble``, ``jazzy``, ``lyrical``, ``rolling``
      * ROS distribution to use as the underlying layer
    
    - * ``BUILD_PACKAGES``
      * Empty
      * Space-separated list of packages to build from source. If empty, will build all ADI ROS 2 packages from source.

    - * ``IMU_MODEL``
      * One of ``adis16...``, ``adis16...``, ...
      * IMU device name to connect to in IMU-related commands

    - * ``IMU_URI``
      * ``ip:12.34.56.78``, ``local:``, ...
      * URI of libiio context to use in IMU-related commands

Makefile targets:

.. list-table::
    :header-rows: 1

    - * Makefile target
      * Description

    - * ``ros-sdk-build``
      * Build docker image
    
    - * ``ros-sdk-shell``
      * Spawn a docker container to use as an interactive shell in the ROS 2 environment

    - * ``ros-sdk-imu-node``
      * Start IMU acquisition with ``adi_imu_node``.

    - * ``ros-sdk-imu-visualize``
      * Start IMU acquisition and 3D visualization in Rviz.
