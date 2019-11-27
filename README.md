1. Download the beardboard folder and place it in your local arduino sketch repo in a folder called hardware (if hardware does not exist, create the folder)
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
10. upload blink onto the chip and add a led and resistor to ensure it all worked
