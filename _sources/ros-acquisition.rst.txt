Getting ADIS IMU data in ROS 2
==============================

In this step, we already have a properly configured raspberry pi and a working ROS 2 container.

To get IMU samples, launch the ADI IMU node by running:

.. shell::

    $ make ros-sdk-run-imu IMU_URI=ip:12.34.56.78 IMU_MODEL=adis16607-3
    # or
    $ docker compose run -e IMU_URI=ip:12.34.56.78 -e IMU_MODEL=adis16607-3 -d imu_node
    # or start ROS shell and run this inside:
    $ ros2 run adi_imu imu_node --ros-args \
                -p "iio_context_string:='ip:12.34.56.78'" \
                -p imu_device_name:=adis16607-3 &

In the commands above, replace ``12.34.56.78`` with the IP address of the Raspberry Pi (TODO instructions for doing that).

This will start the IMU node in the background, which will continuously publish data to the ROS 2 ``/imu`` topic.

Check the status and logs of the IMU node to verify no errors:

.. shell::

    $ docker compose ps
    $ docker compose logs imu_node

Finally, while this is running in the background, we can spawn a ROS shell to see the contents of the IMU messages:

.. shell::

    # Inside a ROS shell
    $ ros2 topic echo /imu
    header:
        stamp:
                sec: 1698746841
                nanosec: 951239970
    frame_id: imu
    orientation:
            x: 0.0
            y: 0.0
            z: 0.0
            w: 1.0
    orientation_covariance:
            -1.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
    angular_velocity:
            x: -0.0021626880000000003
            y: -0.005046272
            z: -0.0015728640000000002
    angular_velocity_covariance:
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
    linear_acceleration:
            x: -0.073531392
            y: 0.0
            z: 9.98801408
    linear_acceleration_covariance:
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0
            0.0

In the end, you can stop the node running in the background with the following command:

.. shell::

    $ make ros-sdk-stop # ?????? do we want sth like this ??????
    # or
    $ docker compose down
