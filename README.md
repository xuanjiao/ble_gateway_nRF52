Please find the program of **Gateway** in the following link

https://github.com/xuanjiao/ble_gateway

# Finished

## 1. Set up developing enviroment on Windows PC

1. Download [Microsoft Studio Code](https://code.visualstudio.com/) and install C/C++ extensions.

2. Download [Mbed Cli](https://github.com/ARMmbed/mbed-cli/blob/1.8.3/README.md) (Arm Mbed command-line tool) and export project to VS Code.

3. Download [GCC-ARM compiler](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads), [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm) and [Make-3.81](https://sourceforge.net/projects/gnuwin32/files/make/3.81/) and change PATH system variable.

4. [Configuring the debugger](https://os.mbed.com/docs/mbed-os/v5.15/tutorials/visual-studio-code.html) and debugging my project **failed, error shows in figure**（leave it for now and use RTT for sinple debug instead). 
![Debug error](./image/debug_error.png)

5. Build application in VS code using mbed.exe and generate .hex file.
![VS Code](./image/VSCode.png)


6. Download latest [Jlink Software Pack](https://www.segger.com/downloads/jlink/#J-LinkSoftwareAndDocumentationPack) includes [Jlink FlashLite V6.54](https://www.segger.com/products/debug-probes/j-link/technology/flash-download/)
[RTT Viewer](https://www.segger.com/products/debug-probes/j-link/tools/rtt-viewer/). Use RTT Viewer to monitor information from MCU.

7. Erase the MCU and flash .hex file to MCU.

8. Download [nRF Connect](https://www.nordicsemi.com/Software-and-tools/Development-Tools/nRF-Connect-for-mobile) on Android smart phone to scan BLE devices

## 2. Write firmware for ACD52832 develop board

1. Install [RTT library](http://os.mbed.com/users/jurica238814/code/aconno_SEGGER_RTT/) and [LDR library](https://os.mbed.com/teams/aconno-dev-team/code/LDR/), make MCU read light value from light sensor.

~~2. Make MCU advertise light value. MCU can be observed in nRF Connect in smartphone and see light value.(temporarily)~~

2. create a server called "Enviroment Sensing" and a custom characteristic that represent a light value. Screenshot of nRF Connect showns below. The light value will be update when user press *read* icon.

![light_char](./image/light_char.jpg)

# To Do

## 2. Write firmware for ACD52832 develop board

<strike>

4. Make MCU create a log file on file system and write light value on log file. 

5. Give each light value a timestamp

6. Try to synchcronize time with ble central device(use my PC for now).

7. Transmit log file to PC use BLE (if failed then use UART)

8. Try to create a Dat-time-possibility table on PC (because i can't find proper way to store and tramsmit a time-posibility table through BLE. And it would be very complex if store them in different BLE Service-Characteristic..).
</strike>

It not possible to store file on develop board because it doesn't have SPI flash or SD card slot..

Instead we use a Gateway as **BLE central device** as well as **BLE GATT Client** which read light value from **GATT server**(develop board) and store them in its file system.

to be continued......
