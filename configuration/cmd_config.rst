Command line configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~

Integrated Navigation Configuration
===================================

1: Install hardware devices.

  .. figure:: ../media/vehicle_installation.png
      :align: center

2: Enter the serial port configuration command.

**INSCOMMAND ENABLE**  //*Turn on inertial navigation mode*

**SETINSROTATION RBV 0 0 0** //*Set the mounting angle (At this time, the INS2000 receiver antenna port is configured 
when the forward direction of the car body is the same. If there are other installation methods, please contact Aceinna 
technical staff)*

**NTRIPCONFIG DTU1 client v1 ServerIP:PortNum Mountpoint username password** //*Turn on 4G*

**SETINSTRANSLATION ANT1 0 0 0 0.0 0.0 0.0** //*Set the lever arm*

**SETINSTRANSLATION DUALANT 0 1 0** //*Only dual-antenna receiver configuration. Set the lever arm*

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

**SETINSROTATION RBV 0 0 -90**

**NTRIPCONFIG DTU1 CLIENT V1 60.205.8.49:8002 RTCM32_GGB admin password** //*60.205.8.49:8002 RTCM32_GGB admin password* needs to be modified

**SETINSTRANSLATION ANT1 0 0 0** //*0 0 0* needs to be modified

**SETINSTRANSLATION DUALANT 0 1.0 0** //*0 1.0 0* needs to be modified

**LOG COM2 HEADINGA ONTIME 1**

**LOG COM2 BESTPOSA ONTIME 1**

**LOG COM2 INSPVAXA ONTIME 1**

**SAVEOCNIFG**

RTK Configuration
=================

When the INS2000 is configured as a rover station, it can receive RTCM data through multiple ports such as Ethernet, serial port, 
USB, etc., and can input multiple sets of RTCM data at the same time, and the receiver is connected to the built-in distribution.

At the same time, customers can configure the message information to obtain the best positioning information:

 * BESTPOS best location
 * BESTVEL best available speed
 * BESTXYZ best position and speed
 * GPGGA GNSS positioning data output sentence

Ntrip Rover Station Configuration
=================================

Let's now configure the commonly used CORS station technology, taking Aceinna's Ntrip as an example.

This RTK mobile station configuration requires that the INS2000 receiver can be connected to the Internet.

There are two ways for this product to connect to the Internet:

1 Connect the product to a network device such as a mobile router with a network cable.

The configuration command is as follows:

**NTRIPCONFIG NCOM1 client V1 60.205.8.49:8002 RTCM32_GGB user password**

2 Connect the 4G antenna and insert the 4G card to configure as follows.

The configuration command is as follows:

**NTRIPCONFIG DTU1 client V1 60.205.8.49:8002 RTCM32_GGB user password**

Simple Output Configuration
===========================

The Y-axis direction of the FRII-D-Plus-INS receiver coordinate system is the same as the forward direction of the carrier. 
Then configure the combined navigation command can be divided into 3 aspects are

a) Set the board mounting angle and lever arm. They are:

* SETINSROTATION set inertial navigation mounting angle
* SETINSTRANSLATION Set the inertial guidance lever arm

b) Enable INS integrated navigation engine (enabled by default)

* INSCOMMAND

c) Set the type and port of positioning result output

   Support integrated navigation information:

* INSATT inertial navigation attitude
* INSPOS inertial navigation position
* INSPVA inertial navigation position speed and attitude
* INSPVAX extended inertial navigation position speed and attitude
* INSSPD inertial navigation horizontal and vertical speed
* INSVEL inertial navigation northeast sky speed

Also reflected in the following information

* BESTPOS best location
* BESTVEL best available speed
* BESTXYZ best position and speed
* GPGGA GNSS positioning data output sentence
* KSXT positioning and orientation data

Examples of inertial navigation configuration are as follows:

**SETINSROTATION RBV 0 0 90 0.0 0.0 0.0**

**SETINSTRANSLATION ANT1 0.1 -0.3 1.5 0.1 0.1 0.1**

**INSCOMMAND ENABLE**

**LOG COM1 GPGGA ONTIME 1**

**LOG COM1 INSPVAA ONTIME 1**

**SAVECONFIG**