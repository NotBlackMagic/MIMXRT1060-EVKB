# Base MIMXRT1062 Project for RT-Thread Studio (LVGL + RT-Thread)

## Flashing and Debugging
The project uses the J-Link Debugger settings so it is necessary to flash the MIMXRT1060-EVKB on-board debug probe with the J-Link Firmware. 

The following article provides the instructions on how to flash the J-Link Firmware onto the on-board debug probe:
https://community.nxp.com/t5/i-MX-RT-Knowledge-Base/Using-J-Link-with-MIMXRT1060-EVKB/ta-p/1452717

### Recover Unresponsive/"Bricked" Board
When flashing an erroneous code, it can happen that the EVK board gets unresponsive, impossible to create a debug link and erase and flash a good code to it. To recover from such events, I found the following steps work:

- Reflash the on-board debug probe with the CMSIS-DAP firmware
- Change the boot option of the EVK board to the SD card (SW4: 1010), aka to nothing, and power cycle the board
- Use the MCUXpresso "GUI Flash Tool" to fully erase the flash
- Change the boot option back to the QSPI Flash (SW4: 0010) and power cycle the board
- The board should now allow a debug connection again
