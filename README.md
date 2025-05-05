# Buffered IDE2CF Adapter
<img src="rev1\images\pcb_top.svg" alt="PCB top" width="400"/><br/>
This adapter was designed with the TF1260 accelerator board in mind because my TF1260 EHIDE interface does not work with a plain IDE2CF-adapter but works fine with a buffered adapter.  
The shape of the adapter makes it fit directly on top of the Tf1260 even if there are heatsinks on the CPLDs.  
It can also be fitted onto the standard IDE controller on the motherboard of the Amiga 1200 but there's not enough room to fit it directly onto the motherboard of the Amiga 600.  
When used with the onboard IDE controller on the Amiga 1200 it can cause issues with some RTC clock modules. This is not the case when used with the Terrible Fire boards that it was designed for.   

The adapter provides an external LED connector so that the Amiga 1200 HDD LED can be connected to the IDE2CF adapter instead of the motherboard and thereby making the standard HDD LED work with the TF1260 EHIDE interface.  
<img src="rev1\images\tf1260.jpg" alt="Adapter installed on TF1260" width="600"/><br/>

### Build & configuration
The adapter is designed to have a 44-pin female IDE-connector on the bottom side which can mate directly to the IDE controller's pin header.  
If you wish to connect the adapter to an IDE cable, use a 44-pin male pin header on the top side of the adapter instead.

#### External LED connector
The external LED connector has two pins. Pin 1 which is the right pin (square pad) is active low and the pin 2 which is the left PIN is the inverted version of pin 1.
You can connect just on of the pins to an LED if the LED is connected to either ground or +5V (or similar).  
Depending on if the LED you are connecting has a current limiting resistor, you may or may not need to add a resistor on the adapter. That is either R3 or R4. On the pins where you don't need resistors, simply add a solder blob to close the corresponding jumper (JP3 or JP4)
You can also connect an LED across both pins. If you do, add one resistor to either of the pins and add a solder blob to the jumper for the other pin.
JP4/R4 is for pin 1  
JP3/R3 is for pin 2  

Some LED configurations examples:

##### Amiga 1200 HDD LED on original LED board (with resistor)
* Unplug LED cable from motherboard connector
* Connect LED cable to pin 2 (left pin)
* Add solder to JP3 (there is already a resistor on the LED board)
* R4/JP4 can be left unpopulated as they aren't used.

##### External LED connected to ground
* Connect LED to pin 2 (left)  
* Do NOT add solder to JP3
* Add a current limiting resitor to R3. 560 Ohm is probably a good value.  
* R4/JP4 can be left unpopulated as they aren't used.

##### External LED connected to +5V
* Connect LED to pin 1 (right)  
* Do NOT add solder to JP4.  
* Add a current limiting resitor to R4. 560 Ohm is probably a good value.  
* R3/JP3 can be left unpopulated as they aren't used.

##### External LED connected only to pin 1 and 2.
* Connect LED anode to pin 2 (left) and cathode to pin 1 (right)  
* Do NOT add solder to JP3.  
* Add solder to JP4
* Add a current limiting resitor to R3. 560 Ohm is probably a good value.  

#### U4 LED buffer
The optional U4 is optional.
If you wish to leave U4 out and drive the LEDs directly from the CF card, you need to close jumper JP2 to let the signal pass by the unpopulated U4 footprint.

#### Master/Slave
The jumpers JP1.1 and JP1.2 are used for setting master/slave configuration. JP1.1 is bridged by default and configures the drive as master.  
If you wish to use the drive in a slave configuration you should cut JP1.1 and optionally install a master/slave jumper at JP1.2 or add a solder blob at JP1.1 when you want to set the drive as master again.
If JP1.1 is uncut or closed with a solder blob, JP1.2 has no effect at at.

