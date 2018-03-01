# Microbit-TVPong

Play the classic Pong game on a TV (composite video) - using BBC Microbits as paddles. Bluetooth also supported!

This is Grant Searle's fantastic Pong game for the Atmel/Microchip ATMEGA328P, modified to also support digital up/down paddles.

Original code at: http://searle.hostei.com/grant/AVRPong/index.html

The above page also has details of the microcontroller circuit that forms the basis of this project (with additions).

The aim was to produce a fun game that could be used in STEM coding workshops using BBC Micro:bits as digital game paddles.

This repo comprises:

1) The modified Pong code, which supports the following additional inputs to the ATMEGA:

* Pin D0 = Left player UP
* Pin D1 = Left player DOWN
* Pin D2 = Right player UP
* Pin D3 = Right player DOWN
* Pin A2 = Analogue / Digital paddles select (no connection = analogue, pin to GND = digital)

There's also some consts and variables to support alternate pin definitions and to change the digital paddle movement speed -
see the source code comments. The comments also include some important information about the AVR fuse settings and supported
Arduino IDE versions (1.6).

2) The microbit-paddles* files are the .hex firmware for the Micro:bits. There's a standard one and a -bt version that ALSO
supports controlling the Micro:bit from a bluetooth-paired device - tested with a Samsung Galaxy S7 and the Bitty controller
software (http://www.bittysoftware.com/apps/bitty_controller.html).

Both softwares use the A and B buttons on the Micro:bit as digital paddle controls - connect P0 and P1 Micro:bit pins
to the up/down inputs on the ATMEGA328P. You will also need a connection between Micro:bit GND and the 0V rail of the ATMEGA circuit.

**Stripboard version**

![Image](bitpong.jpg)

The header pins on the left are for the paddle potentiometers. The green terminals on the right are for the alternative digital inputs from the Microbits, and the large component to the left of the terminals is an LM1117 providing 3.3V from the 5V USB input to power the microbits.

The DIP switches set ball speed, paddle size, bounce angles and the added option to choose between analogue or digital paddles. The two buttons are game reset (right) and game select (left).

Have fun!


