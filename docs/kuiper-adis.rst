kuiper-adis target
==================

The ``kuiper-adis`` cim target configures a Kuiper Linux image to communicate with an ADIS IMU.

* Enables device tree overlay for selected IMU
* Enables libiio daemon

Configuration options:

.. list-table::
    :header-rows: 1

    - * Variable
      * Value
      * Description

    - * ``IMU_MODEL``
      * ``adis16607-1``
      * ADIS IMU model and variant, used to select proper device tree overlay
    
    - * ``BOOT_PARTITION``
      * ``/boot`` (default)
      * Path to the boot partition:
      
        ``/boot`` on a live Kuiper image

        ``path/to/kuiper/boot`` in a staging environment

    - * ``ENABLE_IIOD``
      * ``y`` (default),
        ``n``
      * 
