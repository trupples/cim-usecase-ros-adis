Linux setup
===========

In this step, we use the ``kuiper-adis`` target to configure a Raspberry Pi to communicate with the ADIS IMU and expose the IMU as a libiio device.

Variant 1: kuiper-adis runs on live Kuiper image
------------------------------------------------

On the Raspberry Pi, open a terminal and run:

.. shell::

    $ cim init ...
    $ cim ...
    $ make kuiper-adis-setup BOOT_PARTITION=/boot IMU_MODEL=adis16607-3

Reboot to load the new changes.


Variant 2: kuiper-adis preconfigures SD card image
--------------------------------------------------

On your computer, open a terminal and run:

.. shell::

    $ cim init ...
    $ cim ...
    $ make kuiper-adis-build-sd-image IMU_MODEL=adis16607-3

This creates an SD card image located at ``build/kuiper-adis.img``. Flash that to the microSD card and load it into the Pi.

Verifying the setup
-------------------

To verify the IMU is correctly connected and visible as a libiio device, run:

.. shell::

    $ iio_info | grep adis

Troubleshooting
---------------

If the verification above failed, we recommend you check:

* dmesg
* do you have the right imu?
* did you reboot?
* is the wiring ok?
* TODO etc
