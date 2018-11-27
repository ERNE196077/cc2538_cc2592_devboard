# cc2538_cc2592_devboard
This board is small enough to fit in a breadboard and let one space for pin connectivity, some features are:
* APA102 2020 onboard.
* FTDI FT232 UART-USB transceiver onboard 
* SN74AHCT125 onboard for 5v TTL (PA5 & PA6)
* RP SMA Female connector for high gain antenna
* Power consumption with LED working and SPI trasmitting each 100 ms = 0.05 A
* Dedicated Flash (PA2) and Reset buttons. 

## Flashing instructions for OpenThread
I'm using the cc2538-bsl.py script from JelmerT to flash the board. All the recognitions goes to him: 
[cc2538-bsl](https://github.com/JelmerT/cc2538-bsl)

Set the bootloader in the board: Press Reset button while holding the Flash button.
Compile the cc2538 example as seen in the [OpenThread.io](https://openthread.io/guides/build) page.

*NOTE* Make sure to modify the dedicated pins in the file /examples/platforms/cc2538/startup-gcc.c to match the above ones.

Convert to binary the resulting image
```
arm-none-eabi-objcopy -O binary output/cc2538/bin/ot-cli-ftd output/cc2538/bin/ot-cli-ftd.bin
```
Flash the image
```
sudo python ./cc2538-bsl/cc2538-bsl.py -p /dev/ttyUSB0 -b 115200 -e -w -v -V  output/cc2538/bin/ot-cli-ftd.bin
```

## KICAD dependencies 
Make sure to update your KICAD and update the libraries. Then you will need to link and match the footprints and schematic components.
![Schematic](https://github.com/ERNE196077/cc2538_cc2592_devboard/blob/master/sch.png)
![PCB layout](https://github.com/ERNE196077/cc2538_cc2592_devboard/blob/master/pcb.png)
![Board](https://github.com/ERNE196077/cc2538_cc2592_devboard/blob/master/board.jpeg)
