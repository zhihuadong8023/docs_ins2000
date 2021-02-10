Python Driver
==============

Python driver for OpenIMU, OpenRTK and INS2000

Working Environment
-------------------

-  Windows10: python2.7 and python 3.7
-  Mac OS: python2.7 and python 3.7

Steps
-----

1. Start the tool
~~~~~~~~~~~~~~~~~

There are 2 ways to run the tool

Prepare
^^^^^^^

Install the dependency library. It is better to create a virtual
environments before to do it.

python 3.x

::

    pip install -r requirements.txt

python 2.x

::

    pip install -r requirements-2.x.txt

A. From source code
^^^^^^^^^^^^^^^^^^^

Run
'''

Please use this way if you want to develop the project.

::

    python main.py

B. Work as execution file
^^^^^^^^^^^^^^^^^^^^^^^^^

Build
'''''

It will be generated in ``dist`` folder.

::

    pyinstaller build.spec

Run it
''''''

::

    ./ans-devices

Startup Arguments
'''''''''''''''''

You can specify some arguments while run the tool

parameters:

+-----------------------+-----------+-----------+---------------------------------------------+
| Name                  | Type      | Default   | Description                                 |
+=======================+===========+===========+=============================================+
| -p, --port            | Number    | '8000'    | Value should be an available port           |
+-----------------------+-----------+-----------+---------------------------------------------+
| --device-type         | String    | 'auto'    | Value should be ``IMU``, ``RTK``            |
+-----------------------+-----------+-----------+---------------------------------------------+
| -b, --baudrate        | String    | None      | Value should be baudrate                    |
+-----------------------+-----------+-----------+---------------------------------------------+
| -c, --com-port        | String    | 'auto'    | Value should be a COM port                  |
+-----------------------+-----------+-----------+---------------------------------------------+
| --console-log         | Boolean   | False     | Output log on console                       |
+-----------------------+-----------+-----------+---------------------------------------------+
| --debug               | Boolean   | False     | Log debug information                       |
+-----------------------+-----------+-----------+---------------------------------------------+
| --with-data-log       | Boolean   | False     | Contains internal data log (OpenIMU only)   |
+-----------------------+-----------+-----------+---------------------------------------------+
| -r, --with-raw-log    | Boolean   | False     | Contains raw data log (OpenRTK only)        |
+-----------------------+-----------+-----------+---------------------------------------------+
| -s, --set-user-para   | Boolean   | False     | Set uesr parameters (OpenRTK only)          |
+-----------------------+-----------+-----------+---------------------------------------------+
| -n, --ntrip-client    | Boolean   | False     | Enable ntrip client (OpenRTK only)          |
+-----------------------+-----------+-----------+---------------------------------------------+
| --cli                 | Boolean   | False     | Work as command line mode                   |
+-----------------------+-----------+-----------+---------------------------------------------+

2. Connect Aceinna device
~~~~~~~~~~~~~~~~~~~~~~~~~

Link device to your pc or mac. And the tool will auto detect the linked
device.

.. `More Usage <usage.rst>`__

Work Mode
---------

Normally, python-openimu works as Web mode. It will auto start a
websocket server after device is detected. And it can works with `aceinna
developers site <https://developers.aceinna.com>`__ to do monitor and
set configuration of connected device.

You can specify the startup parameter ``--cli`` to switch to Command
Line Mode. Command Line Mode helps you to interact with device without
open the brower.

Commnad List: 

+-------------+-----------------------------------------------------------+
| Name        |   Description                                             |
+-------------+-----------------------------------------------------------+
| help        | CLI help menu                                             |
+-------------+-----------------------------------------------------------+
| exit        | Exit Command Line Mode                                    |
+-------------+-----------------------------------------------------------+
| run         | Operationsdefined by users                                |
+-------------+-----------------------------------------------------------+
| save        | Save thee configuration into EEPROM                       |
+-------------+-----------------------------------------------------------+
| connect     | Show information of connected device                      |
+-------------+-----------------------------------------------------------+
| upgrade     | Upgrade firmware                                          |
+-------------+-----------------------------------------------------------+
| record      | Record output data of device                              |
+-------------+-----------------------------------------------------------+
| stop        | Stop recording outputs                                    |
+-------------+-----------------------------------------------------------+
| server_start| Start server thread and must use ``exit`` command to quit |
+-------------+-----------------------------------------------------------+
| get         | Read the current configuration and output data            |
+-------------+-----------------------------------------------------------+
| set         | Write parameters to device                                |
+-------------+-----------------------------------------------------------+


Decoding tool
-------------

Decoding INS2000
~~~~~~~~~~~~~~~~

1. Run the decoding program

   ::

       python tools/ins2000_parser.py -f /your/ins2000/data/path

2. More command prompts

   ::

       python tools/ins2000_parser.py

   ::

       usage: ins2000_parser.py [-h] [-f F] [-c C]

       Aceinna INS2000 parse input args command:

       optional arguments:
         -h, --help  show this help message and exit
         -f F        The file to be decoded
         -c C        Decoding configuration file

Changelogs and Release Notes
----------------------------

.. `HISTORY <history.rst>`__

**2.2.4 / 2020-12-18**

-  [OpenRTK] Remove console print and add print.log to save these
   infomation.
-  [OpenRTK] Update openrtk parse to make kml files

**2.2.3 / 2020-12-01**

-  [OpenRTK] Update Configuration read size
-  [Framework] Fix cannot parse 'sC', 'uB' command

**2.2.2 / 2020-11-26**

-  [OpenIMU] Add exception handler when log data, although file is
   closed
-  [OpenIMU] Add uC,uA,gA command response
-  [OpenRTK] Fix upgrade issue through web

**2.2.1 / 2020-11-17**

-  [OpenIMU] Fix the mag align command cannot correctly response.
-  [Framework] Update the usage of asyncio.
-  [Framework] Fix cannot connect the websocket server on some versions
   of windows.
-  [Framework] Support to start executor as a cli tool with startup
   parameter ``--cli``.
-  [Framework] Fix data log will auto start after firmware upgrade
   without setting auto start.

**2.2.0 / 2020-11-9**

-  [OpenRTK] Important update for INS App v23.00, can't suitable for
   v2.0.0 or v20.00.
-  [OpenRTK] Modify user data packets.
-  [OpenRTK] Log base rtcm data on debug port.
-  [DMU] Add A1,A2 packet response for DUM device.
-  [Framework] Add Unit test cases.

**2.1.7 / 2020-08-26**

-  [OpenRTK] Print 'NMEA' and #INSPVA.
-  [Framework] Improved the ping perform on devices.

**2.1.6 / 2020-08-19**

-  [OpenRTK] Modify INS json: suitable for INS\_APP v2.0.0.
-  [Framework] Improve the output of console.

**2.1.5 / 2020-08-11**

-  [Framework] Support download combined GNSS\_RTK\_SDK and INS\_APP
   Firmware.
-  [Framework] Display python driver version.
-  [Framework] Remove upgrade file when upgrade firmware.

**2.1.4 / 2020-07-23**

-  [OpenRTK] Add 'rD' command to restore OpenRTK330 default
   configuration. User can find 'RESTORE DEFAULTS' button in
   OpenRTK->SETTINGS.
-  [OpenRTK] Add 'gB' command to get configuration according to range of
   parameterID.
-  [OpenRTK] Support update GNSS\_RTK\_SDK in App Center.
-  [Framework] Enhance the message parser from device.

