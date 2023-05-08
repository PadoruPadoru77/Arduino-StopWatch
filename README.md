# Arduino-StopWatch
A simple project to do using Arduino Uno R3 micro controller or something similar

StopWatch Project

Create a stopwatch with a timer, Pausey/Play Button
and Reset button.

The circuit:
- Arduino Uno R3 (or similar)
- (4-bit) 7-segment LED (SH5461AS or similar) connected through pins D2-D13
- 2 pushbuttons attatched to ground from A0 and A2
- 4 220 ohms resistors attatched to LED pins 12, 9, 8 and 6 (Or whatever your respective block pins are)
- Active buzzer attatch to ground from A3
- wires

created 5/7/2023
by Michael Schmidt



CONCEPT UNDERSTANDING

The 4-bit 7-segment LED does not have any onboard memory and does not display
individual numbers in each block simutaniously. Using the segment pins will
light up the pins for all the blocks. We can use the block pins to show which
block we wish to display, but to show multiple numbers, the computer need to
display 2 different segment pins combinations seperated by different block
pins sequentially fast enough to make it appear as individual numbers have appear
for each block. The code in RefreshClock() shows this by using delay(5) to give 
enough time to show the differences between 2 or more different segment pins combinations.

The button pins are set to INPUT_PULLUP as the pins will act as an output voltage HIGH
and when the button is pressed, it connects to the ground which completes the circuit
while the pin reads LOW. This is easier and uses no resistors, while just setting the
pin to be INPUT will require a resistor on the same leg connect to the pin to ensure
the completed circuit will pass through the pin.

The active buzzer will only make a tone when power goes through its pin, which is
set to be when the buttons are pressed.
