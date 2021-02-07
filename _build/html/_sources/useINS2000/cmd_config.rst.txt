Command line configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~

Integrated Navigation Configuration
===================================

1: Install hardware devices. Please refer to ` Quick Start`_.

  .. figure:: ../media/vehicle_installation.png
      :align: center

2: Enter the serial port configuration command.

**INSCOMMAND ENABLE**  //*Turn on inertial navigation mode*

**SETINSROTATION RBV 0 0 0** //*Set the mounting angle (At this time, the INS2000 receiver antenna port is configured 
when the forward direction of the car body is the same. If there are other installation methods, please contact Aceinna 
technical staff)*

**NTRIPCONFIG DTU1 client v1 ServerIP:PortNum Mountpoint username password** //*Turn on 4G*

**SETINSTRANSLATION ANT1 0 0 0 0.0 0.0 0.0** //*Refer to 5.2 Setting the lever arm*

**SETINSTRANSLATION DUALANT 0 1 0** //*Only dual-antenna receiver configuration, refer to 5.2 Setting the lever arm*

**LOG COM2 BESTPOSA ONTIME 1** //*Output from serial port 2*

**SAVECONFIG** //*Save configuration*

An example of the relevant configuration of the lever arm from the IMU to the main antenna.

.. image:: ../media/lever_arm.png
   :align: center

It can be seen from the figure that the main antenna is 0.3 meters to the left of the board (X-axis -0.3m), 1 meter to the 
rear (Y-axis -1.0m), and 0.3 meters above (Z-axis +0.3m), the configuration is:

**SETINSTRANSLATION ANT1 -0.3 -1.0 0.3**

The slave antenna is 1m directly in front of the main antenna, the configuration is:

**SETINSTRANSLATION DUALANT 0 1 0**

3: Configuration command example (*you can copy and paste directly, pay attention to change ntrip account information, 
antenna lever arm information*).

Aceinna INS2000  Dual antenna configuration

``SETINSROTATION RBV 0 0 -90`` 


``NTRIPCONFIG DTU1 CLIENT V1 *60.205.8.49:8002 RTCM32_GGB admin password*``
**SETINSTRANSLATION ANT1 \*0 0 0\***
**SETINSTRANSLATION DUALANT *0 1.0 0***
**LOG COM2 HEADINGA ONTIME 1**
**LOG COM2 BESTPOSA ONTIME 1**
**LOG COM2 INSPVAXA ONTIME 1**
**SAVEOCNIFG**