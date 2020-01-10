Requirements:
* Arduino Uno
* Jumper wires
* Atmega328P (Atmega328 also works but needs some additional steps)
* 16 MHz crystal
* 2 - 20 pF caps
* USB to serial connector (used to program Atmega328 once bootloader is burned)

Hardware:
Follow the graphics in the following link https://www.arduino.cc/en/Tutorial/ArduinoToBreadboard for the configuration you are interest in.

Software:
1. Download the beardboard zip from the above link (you will find it in the "Minimal Circuit ..." heading) and place it in your local arduino sketch repo in a folder called hardware (if hardware does not exist, create the folder)
2. Depending on the MCU you are using you may need to change the boards.txt file slightly
3. If the chip is an Atmega328P continue to step 5
4. If the chip is an Atmega328 open the breadboard/avr/boards.txt and remove the p from the line 
`atmega328bb.build.mcu=atmega328p`
this line should say 
`atmega328bb.build.mcu=atmega328` *Make sure to take note of this as we will need to add the p back later

5. Within the arduino IDE open the sketch Arduino ISP found in the examples folder
6. under tool board set the board to arduino on breadboard
7. under programmer select Arduino as ISP
8. under tools -> burn bootloader
9. if your chip is an Atmega328 revert the change in step 4 (add the p back)
10. upload* blink onto the chip and add a led and resistor to ensure it all worked

To upload with a usb to serial device without a Data Trigger Ready (DTR pin) You will need to add a pullup resistor to pin 1 and pull pin 1 to ground until the compilation is completed. When the sketch size is present in the debug terminal stop pulling pin 1 down. 

16 MHz work around:

When attempting to burn the boot-loader onto a 16MHz Atmega328, you will need to find avrdude.conf (should have a path similar to $HOME/.arduino15/packages/arduino/tools/avrdude/6.3.0-arduino17/etc/avrdude.conf) within your installation of arduino. Change the signature of the Atmega328P chip (1e 95 0f) to 1e 95 14. Burn the bootloader using the "Arduino Duemilanove" as the selected board. Make sure to revert the changes when you are done. 
