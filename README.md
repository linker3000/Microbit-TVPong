# Microbit-TVPong

Play the classic Pong game on a TV (composite video) - using BBC micro:bits as paddles. Bluetooth also supported!

![Image](onscreen.jpg)
 	
This is Grant Searle's fantastic Pong game for the Atmel/Microchip ATMEGA328P, modified to also support digital up/down paddles.

Original code at: [Internet Archive link](https://web.archive.org/web/20211114205256fw_/http://searle.x10host.com/AVRPong/index.html)

The above page also has details of the microcontroller circuit that forms the basis of this project (with additions).

The aim was to produce a fun game that could be used in STEM coding workshops using BBC micro:bits as digital game paddles.

Video: https://youtu.be/jDqk6mIApZk

This repo comprises:

1) The modified Pong code, which supports the following additional inputs to the ATMEGA:

* Pin D0 = Left player DOWN
* Pin D1 = Left player UP
* Pin D2 = Right player DOWN
* Pin D3 = Right player UP
* Pin A2 = Analogue / Digital paddles select (no connection = analogue, pin to GND = digital)

There's also some consts and variables to support alternate pin definitions and to change the digital paddle movement speed -
see the source code comments. The comments also include some important information about the AVR fuse settings and supported
Arduino IDE versions (1.6).

2) The microbit-paddle* and microbit-radio files

There are two game controller (paddles) files and one remote control file. These files are ready to upload to a micro:bit, or import into the makecode environment for examination and modification:

The 'paddle' files use the A and B buttons on the micro:bit as digital paddle controls - connect micro:bit pins P0 and P1 
to the up/down inputs on the ATMEGA328P. You will also need a connection between micro:bit GND and the 0V rail of the ATMEGA circuit. The prototype pong board in the image below also has a 3V regulator to supply power to the micro:bits - alternatively you could use a battery pack or USB (but that leads to a bit of a mess of cables!)

---

The **paddle-bt** file lets the Micro:bit be controlled either from its A/B buttons or from a Bluetooth-paired phone. It responds to the micro:bit's standard Bluetooth D-pad events (MES_DPAD_CONTROLLER_ID): button 1 moves the paddle one way and button 2 the other, mirroring the B and A buttons.

It was originally tested with a Samsung Galaxy S7 running Bitty Controller, which is no longer available. Any app that sends standard micro:bit D-pad events should work instead. One option is the free HOVER:BIT web app (https://jakobst1n.github.io/microbit-gamepad/), which runs in Chrome on Android.

The **paddle-with-radio** file uses the A B buttons AND supports a remote control micro:bit connected using the inbuilt radio so that you can play pong without wires! Simply program a second micro:bit with the microbit-radio-remote.hex file.

These projects were built in MakeCode for micro:bit, and dragging a .hex file onto makecode.microbit.org opens the editable blocks.

---

![Image](microbits.jpg)

*micro:bit wired digital paddle and a battery-operated remote micro:bit*

When first started, the radio-enabled paddles will ask you to choose whether they are paddle A or paddle B - hold down the relevant button until the choice is registered. Likewise with the remote control micro:bits - Press and hold A or B on startup so that you have a remote control for each paddle. All radio comms is via micro:bit radio group 16.

To differentiate the two micro:bit types, the paddles display 'PAD!' on startup, and the remote controls show 'RMT!'

*For a bit of fun, you can have multiple A or B remote control micro:bits for a team tug of war!*

**Stripboard version**

![Image](bitpong.jpg)

The header pins on the left are for the paddle potentiometers (not used for this application). The green terminals on the right are for the alternative digital inputs from the micro:bits, and the large component to the left of the terminals is an LM1117 providing 3.3V from the 5V USB input to power the micro:bits.

The DIP switches set ball speed, paddle size, bounce angles and the added option to choose between analogue or digital paddles. The two buttons are game reset (right) and game select (left).

The code for the game can be uploaded to an Arduino Uno if you don't want to build your circuit from scratch. There's also ready-made boards that hold just the 328P - eg: the Bitsbox "Barebones 'Duino PCB" (https://www.bitsbox.co.uk/index.php?main_page=product_info&cPath=255_313&products_id=3297) 

**Schematic**

![Image](microbit-pong-schematic.png)

Have fun!
