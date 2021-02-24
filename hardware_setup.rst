Hardware Setup
~~~~~~~~~~~~~~

.. figure:: media/connection.png
    :align: center

Prerequisites
^^^^^^^^^^^^^

+--------------------------+----------+----------------------------------------------+
| Name                     | Quantity | Remarks                                      |
+--------------------------+----------+----------------------------------------------+
| Aceinna INS2000 receiver |    1     |                                              |
+--------------------------+----------+----------------------------------------------+
| 4G antenna               |    1     |                                              |
+--------------------------+----------+----------------------------------------------+
| GNSS antenna             |    2     |                                              |
+--------------------------+----------+----------------------------------------------+
| SIM card                 |    1     |                                              |
+--------------------------+----------+----------------------------------------------+
| 10-pin MGG connector     |    1     | USB, CAN, serial port 3                      |
+--------------------------+----------+----------------------------------------------+
| 12-pin MGG connector     |    1     | Network port, PPS, serial port 2, power port |
+--------------------------+----------+----------------------------------------------+
| GNSS antenna feeder      |    2     |                                              |
+--------------------------+----------+----------------------------------------------+
| Ethernet cable           |    1     | prepared by customer                         |
+--------------------------+----------+----------------------------------------------+
| Serial line              |    1     | prepared by customer                         |
+--------------------------+----------+----------------------------------------------+
| computer                 |    1     | prepared by customer                         |
+--------------------------+----------+----------------------------------------------+

Setup Procedure
^^^^^^^^^^^^^^^

* 1: Install the Aceinna INS2000 on the carrier (the advancing direction of the carrier is consistent with the direction of the receiver Y axis);
* 2: Install the Aceinna INS2000 receiver with a 4G antenna;
* 3: Install the Aceinna INS2000 receiver into the SIM card;
.. note:: When installing the SIM card, as shown in the figure, the notch is to the right and the chip is upward.
* 4: Connect theAceinna INS2000 receiver to the GNSS antenna through the GNSS feeder (note that the antenna should be installed in an open and unobstructed place);
.. note:: When the dual antenna board is built-in, ANT1 is the master antenna and ANT2 is the slave antenna.
* 5: Install the Aceinna INS2000 data cable to the Aceinna INS2000;
* 6: Connect the network port or serial port to the laptop;
* 7: Power supply 9-36V (12V recommended);
.. note:: Power on after all hardware is successfully connected.
* 8: Perform integrated navigation configuration.

PC Requirement and Network Port Connection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Serial connection. Connect the computer with a serial cable and install the serial cable driver. After the driver is installed, the 
successful serial port recognition will be displayed in the computer's device manager. As the figure shows:

 .. figure:: media/serial_1.png
     :align: center

2. Internet connection. Connect the computer with a network cable or ensure that the receiver and the computer are in the same local 
area network (connect to the same router). After the physical connection is normal, the receiver will automatically 
try to obtain an available IP.

3. Obtain IP information. Using the serial port tool, select the corresponding serial port, and select **460800** for the serial port baud rate. 
Send the **netconfig** command line in the command window to get the board IP information.

 .. figure:: media/ip_info.png
     :align: center

 If you need to set a static IP, you can set it through NETCONFIG. The detailed steps are as follows (assuming the receiver IP address 
 is 192.168.20.173):
  * Enter the following commands to set the receiver IP address, subnet mask and gateway:

    **NETCONFIG STATIC 192.168.20.173 255.255.0.0 192.168.1.1**

  * Save the current configuration:

    **SAVECONFIG**

4. Enter the IP address in the browser (Chrome is recommended), quickly enter the built-in network interface of the board, and 
experience the full graphical, zero-handed interaction mode.

.. figure:: media/web_page.png
    :align: center

.. note:: The webpage will automatically switch to the local language according to the current computer system language,
 and now supports English, Chinese, Japanese and Norwegian. Other languages can be customized, please contact Aceinna sales team if you need.

Enter the username and password by default:

**username: admin**

**password: password**

*The password can be modified after entering the webpage. If you forget the password, please contact Aceinna technical team.*

Firmware Update
~~~~~~~~~~~~~~~

Enter the IP address in the browser (Chrome is recommended), then enter the user name and password, and select 
the firmware upgrade to enter the following page.

.. figure:: media/firmware_update1.png
    :align: center

Select the firmware to be upgraded, as shown in the figure below.

.. figure:: media/firmware_update2.png
    :align: center

Click [Install] to upgrade the firmware, and click Reboot to restart after the upgrade.

.. figure:: media/firmware_update3.png
    :align: center
