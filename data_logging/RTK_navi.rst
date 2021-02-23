RTKlib tool RTKNAVI
-------------------

rtknavi.exe download: https://github.com/Aceinna/rtklib_aceinna/releases

**Using rtknavi to save INS2000 data and decode at the same time**

1. Click the [i] button in the upper right corner to open the [input
streams] dialog box.

.. figure:: ../media/rtknavi_1.png
   :alt: center

2. Check [(1) Rover], select [serial] for [type], select [ins2000] for
[format], and click [Opt] to open the [serial options] dialog box.

.. figure:: ../media/rtknavi_2.png
   :alt: center

3. [port] select the serial port of ins2000, and [bitrate] select
460800. Click [OK] to close the dialog box.

.. figure:: ../media/rtknavi_3.png
   :alt: center

4. Click the [CMD] button to open the [serial / TCP commands] dialog box.

.. figure:: ../media/rtknavi_4.png
   :alt: center

5. Check [commands at startup] in the [serial / TCP commands] dialog box and output configuration parameters 
in the text box.

::

    unlogall
    NTRIPCONFIG NCOM1 client V1 47.116.1.17:2201 WX02 AceinnaRTK SIGEMZOOMQ1JDJI3
    SETINSTRANSLATION ANT1 -0.28 1.43 1.0 0.20 0.20 0.20
    SETINSTRANSLATION DUALANT 0.7 0.0 0.0 0.20 0.20 0.20
    SETINSROTATION RBV 0.0 0.0 0.0 0.5 0.5 1.0
    SETINSTRANSLATION USER -0.28 1.43 1.0 0.20 0.20 0.20
    INSCOMMAND ENABLE
    LOG RANGECMPB ONTIME 1
    LOG RAWEPHEMB ONCHANGED
    LOG GLOEPHEMERISB ONCHANGED
    LOG GALEPHEMERISB ONCHANGED
    LOG BDSEPHEMERISB ONCHANGED
    LOG QZSSEPHEMERISB ONCHANGED
    LOG INSCONFIGB ONCHANGED
    LOG versionb once
    LOG rxstatusb once
    LOG inspvaxb ontime 0.1
    LOG bestgnssposb ontime 0.1
    LOG bestgnssvelb ontime 0.1
    LOG headingb ontime 0.1
    LOG heading2b ontime 1
    LOG RAWIMUSXB ONNEW
    LOG gpgga ontime 0.1
    LOG NCOM1 gpgga ontime 1
    SAVECONFIG

.. figure:: ../media/rtknavi_5.png
   :alt: center

6. Click the [l] button in the upper right corner to open the [log
streams] dialog box.

.. figure:: ../media/rtknavi_6.png
   :alt: center

7. Check [(6) Rover], [type] select [file], and then select a path to 
save the file, and click [OK] to close the dialog box.

.. figure:: ../media/rtknavi_7.png
   :alt: center

8. Click [start] to start data 
collection.

.. figure:: ../media/rtknavi_8.png
   :alt: center

9. Log data and decode the generated files in 
real time.

.. figure:: ../media/rtknavi_9.png
   :alt: center
