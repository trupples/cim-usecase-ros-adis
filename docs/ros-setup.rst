ROS 2 runtime environment setup
===============================

In this step, we use the ``ros-sdk`` target to prepare a Docker container with a ready-to-use ROS 2 environment with ADI ROS 2 tools and examples already installed.

Building the container
----------------------

On your computer, open a terminal and run:

.. shell::

   $ cim init ...
   $ ...
   $ make ros-sdk-build BUILD_PACKAGES=adi_imu

This builds a container image with ROS 2 in which the ``adi_imu`` package is built from source.

Getting ADI packages
--------------------

The previous step already builds the ADI ROS packages we need into the Docker container.

In other applications, ADI ROS packages can be installed like any other from the ROS package index:

.. shell::

   # replace DISTRO with humble, jazzy, kilted, ...
   $ sudo apt-get install ros-DISTRO-adi-imu
   $ sudo apt-get install ros-DISTRO-adi-iio
   $ sudo apt-get install ros-DISTRO-adi-tmcl
   $ sudo apt-get install ros-DISTRO-adi-tmc-coe
   ...

Or by including them as dependencies of your packages, defined in their respecitve ``package.xml`` files:

.. code-block:: xml

   <exec_depends>adi_imu</exec_depends>
   <exec_depends>adi_iio</exec_depends>
   <exec_depends>adi_tmcl</exec_depends>
   <exec_depends>adi_tmc_coe</exec_depends>
   ...

Verify
------

To verify that we have a functioning container, start up a ROS 2 shell with:

.. shell::

   $ make ros-sdk-shell
   # or
   $ docker compose run ros-sdk-shell
   # or
   $ docker run --net=host --ipc=host --pid=host -it adi-ros-sdk:jazzy ....a long-ish list of options for sanity...

Inside this shell, run the following commands to check that the ``adi_imu`` package is present:

.. shell::

    $ source /opt/ros/jazzy-adi/setup.bash
    $ ros2 pkg executables adi_imu
    adi_imu adi_imu_node
    # ^^^ expect this output line

To exit this ROS shell and go back to your terminal, run ``exit`` or press :kbd:`Ctrl-D`.
